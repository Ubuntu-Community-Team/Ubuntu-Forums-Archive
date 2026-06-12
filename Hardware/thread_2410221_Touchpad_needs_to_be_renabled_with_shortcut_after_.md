---
title: "Touchpad needs to be renabled with shortcut after suspend"
date: 2019-01-12
forum: Hardware
---

### Post by llamalord2 on 2019-01-12
Every time I suspend my HP Pavillion 14 laptop, the touchpad stops working. The weird thing is that it's obviously not a driver issue or similar, because if I push the shortcut to enable the touchpad, then it starts working again until I resume again.

The shortcut is set in System Settings > Touchpad > Keyboard shortcuts.

I'd just like the OS to re-enable the touchpad automatically on resume, without having to push the keyboard shortcut each time.

How might I go about this? I've looked at a ton of "my touchpad stops working on suspend" threads, but they all seem related to necessary drivers / modules not being loaded/installed.

---

### Post by him610 on 2019-01-13
From [https://help.ubuntu.com/stable/ubuntu-help/power-suspend.html.en]("https://help.ubuntu.com/stable/ubuntu-help/power-suspend.html.en")
> When you suspend the computer, you send it to sleep. All of your applications and documents remain open, but the screen and other parts of the computer switch off to save power. The computer is still switched on though, and it will still be using a small amount of power. You can wake it up by pressing a key or clicking the mouse. If that does not work, try pressing the power button.

Some computers have problems with hardware support which mean that they may not be able to suspend properly. It is a good idea to test suspend on your computer to see if it does work before relying on it.

---

### Post by llamalord2 on 2019-01-14
> Some computers have problems with hardware support which mean that they may not be able to suspend properly.

The unusual thing here though, is that the hardware *does* successfully sleep and resume. It's just that the touchpad is set to "disabled" when it resumes, which can be fixed just by pushing the shortcut. I just want to not need to push the keyboard shortcut every time I resume.

---

