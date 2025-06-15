
# 📶 ADB Wireless Toolkit

Control your Android phone **completely over Wi-Fi** using ADB — no app install, no root, no cable (after setup).  
This guide includes setup instructions, categorized ADB commands, automation scripts, and usage tips.

---

## 🔧 Requirements

- Android phone with Developer Mode and USB Debugging enabled
- Linux/Mac/Windows machine with ADB installed
- Phone and PC must be on the **same Wi-Fi network**

---

## 🚀 Getting Started [In Detailed](https://github.com/shivamprasad1001/adb-wireless-toolkit/wiki)

### 1. Enable Developer Options on your phone

- Go to **Settings > About Phone**
- Tap **Build number** 7 times
- Go back to **Settings > Developer Options**
- Enable **USB Debugging**
### 2. Connect Phone via USB Temporarily

Run this in terminal:
```bash
adb devices
````

When your phone prompts, tap **Allow USB Debugging**.

### 3. Switch ADB to Wireless Mode

```bash
adb tcpip 5555
```

Now unplug the USB cable.

### 4. Connect to Phone Over Wi-Fi

Find your phone's IP in Settings > Wi-Fi > Info
Then run:

```bash
adb connect 192.168.1.15:5555
```

You’re now wireless! 🎉

---

## 🧭 Table of Contents

* [📱 Screen Control (Tap, Swipe)](#-screen-control)
* [⌨️ Text & Keyboard Input](#️-text--keyboard-input)
* [🎮 KeyEvents (Hardware Buttons)](#-keyevents)
* [🎥 Media: Screenshot & Screen Recording](#-media-screenshot--recording)
* [📂 File Transfer (Push & Pull)](#-file-transfer)
* [📦 App Control (Launch, Info)](#-app-control)
* [🛠️ System Info](#️-system-info)
* [🔐 Safety & Tips](#-safety--best-practices)
* [❗ Troubleshooting](#-troubleshooting)

---

## 📱 Screen Control

| Action       | Command                                                        |
| ------------ | -------------------------------------------------------------- |
| Tap screen   | `adb shell input tap <x> <y>`                                  |
| Swipe screen | `adb shell input swipe x1 y1 x2 y2`                            |
| Long press   | `adb shell input swipe x y x y duration`                       |
| Example      | `adb shell input swipe 500 1000 500 1000 1500` (1.5 sec press) |

---

## ⌨️ Text & Keyboard Input

| Action     | Command                              |
| ---------- | ------------------------------------ |
| Type text  | `adb shell input text 'Hello_World'` |
| Enter key  | `adb shell input keyevent 66`        |
| Delete key | `adb shell input keyevent 67`        |
| Space key  | `adb shell input keyevent 62`        |

---

## 🎮 KeyEvents

| Key Name      | KeyEvent Code                          |
| ------------- | -------------------------------------- |
| Home          | `adb shell input keyevent 3`           |
| Back          | `adb shell input keyevent 4`           |
| App Switch    | `adb shell input keyevent 187`         |
| Power         | `adb shell input keyevent 26`          |
| Volume Up     | `adb shell input keyevent 24`          |
| Volume Down   | `adb shell input keyevent 25`          |
| Lock screen   | `adb shell input keyevent 223`         |
| Unlock screen | Use swipe gesture (see screen control) |

---

## 🎥 Media: Screenshot & Recording

| Action             | Command                                      |
| ------------------ | -------------------------------------------- |
| Screenshot         | `adb exec-out screencap -p > screenshot.png` |
| Start screenrecord | `adb shell screenrecord /sdcard/record.mp4`  |
| Stop recording     | Press `Ctrl + C` in terminal                 |
| Pull video to PC   | `adb pull /sdcard/record.mp4`                |

---

## 📂 File Transfer

| Action               | Command                                 |
| -------------------- | --------------------------------------- |
| Pull file from phone | `adb pull /sdcard/Download/file.txt`    |
| Push file to phone   | `adb push myfile.txt /sdcard/Download/` |
| List files           | `adb shell ls /sdcard/Download`         |

---

## 📦 App Control

| Action                    | Command                                                                        |
| ------------------------- | ------------------------------------------------------------------------------ |
| Launch app (e.g., Chrome) | `adb shell monkey -p com.android.chrome -c android.intent.category.LAUNCHER 1` |
| List all packages         | `adb shell pm list packages`                                                   |
| App info                  | `adb shell dumpsys package <package-name>`                                     |
| Force stop app            | `adb shell am force-stop <package-name>`                                       |
| Open Chrome with a Specific URL                          | `adb shell am start -a android.intent.action.VIEW -d "https://github.com/shivamprasad1001/" com.android.chrome`|


---

## 🛠️ System Info

| Info Type       | Command                                      |
| --------------- | -------------------------------------------- |
| Phone model     | `adb shell getprop ro.product.model`         |
| Android version | `adb shell getprop ro.build.version.release` |
| Battery status  | `adb shell dumpsys battery`                  |
| Network info    | `adb shell dumpsys connectivity`             |

---

## 🔐 Safety & Best Practices

* Only enable USB debugging **when needed**
* After use, run: `adb disconnect`
* Revoke USB debugging in **Developer Options**
* Never use unknown ADB commands/scripts
* Prefer Wi-Fi ADB only on **trusted networks**

---

## ❗ Troubleshooting

| Problem                        | Solution                                              |
| ------------------------------ | ----------------------------------------------------- |
| `adb: command not found`       | Install ADB: `sudo apt install adb`                   |
| Can't connect to IP            | Ensure same Wi-Fi network, use `adb tcpip 5555` first |
| `unauthorized` device          | Re-plug USB, check phone screen for prompt            |
| `Connection refused`           | Reboot phone and retry connection                     |
| Commands don't work over Wi-Fi | Try `adb kill-server` then `adb connect` again        |

---

## ✨ Contribute

PRs welcome! Share your own commands, scripts, or ideas.

---

## 📜 License

[MIT License](LICENSE)

---

> Made with ❤️ to control your phone like a hacker.
