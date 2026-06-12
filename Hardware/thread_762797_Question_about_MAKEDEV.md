---
title: "Question about MAKEDEV"
date: 2008-04-22
forum: Hardware
---

### Post by gear_head on 2008-04-22
I've managed to figure out how to add a gamepad (joystick) to my system so I can use my cheap 4-button gamepad to play NES roms.

I found instructions in another thread that said to use:

 ```
MAKEDEV js
```

Which created js0, js1, etc.. under /dev/input.

The thread also gave instructions on how to modify /etc/modules to include the modules to support the gameport and the joystick/gamepad as well as create a modules.conf file all to be reloaded everytime I boot so I don't have to do it manually each time.

However...(and this is my problem)

Once I reboot, the device 'js0' (as well as the other js* devices) no longer exists. The modules and modules.conf files are still there, but the device doesn't exist thus rendering them useless.

How do I make this device activation permanent?

EDIT: Here is the thread I used.

[http://ubuntuforums.org/showthread.php?t=338457]("http://ubuntuforums.org/showthread.php?t=338457")

---

### Post by jon743 on 2008-08-01
yeah... I'm having the same problem. Call me lazy, but I don't like having to go to the command prompt whenever I want to use my joystick, even if it is only to type a few lines. 
Didn't happen to figure it out did you?

---

