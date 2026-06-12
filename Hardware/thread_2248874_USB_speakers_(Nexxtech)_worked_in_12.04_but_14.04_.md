---
title: "USB speakers (Nexxtech) worked in 12.04 but 14.04 Sound settings don't see them"
date: 2014-10-17
forum: Hardware
---

### Post by steveontario on 2014-10-17
Hello Ubuntu experts:

Having a weird problem. As the subject titled suggests, my USB speakers aren't working. Sound settings (the "Sound" in the System Settings) doesn't see these things, though they're hooked up to my pc. I opened Terminal and ran an "lsusb" and here's what I got:

```
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubBus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 18a5:4123 Verbatim, Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 005 Device 002: ID 0d8c:0103 C-Media Electronics, Inc. CM102-A+/102S+ Audio Controller
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 004 Device 002: ID 03f0:1d17 Hewlett-Packard LaserJet 1320
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



```

When I unplug the speaker USB, the line 
```
Bus 005 Device 002: ID 0d8c:0103 C-Media Electronics, Inc. CM102-A+/102S+ Audio Controller
```

doesn't show. So it's recognizing something, but that something is now showing as an alternative in Sound settings.

Any idea how I could get this thing to work?

I just installed 14.04, my previous system was 12.04 and the USB speakers worked fine in that.

Thanks!

---

### Post by Vladlenin5000 on 2014-10-17
Please make sure you have a fully updated system before anything else (preferably without the USB audio device):
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Then reboot and try again. If the symptom persists try another USB port.

---

### Post by steveontario on 2014-10-17
actually, just figured it out. One of the options in the Sound settings WAS the USB speakers... but because it wasn't the same as it was in 12.04 I assumed it was something else. Apologies!

BTW -- 14.04 is WAAAAYYYY better than 12.04!

---

### Post by steveontario on 2014-10-17
Vladlenin5000 -- thanks very much for your prompt reply. I had done the first of those lines you suggested; I'll do the others before I get further.

Thanks!

---

### Post by Vladlenin5000 on 2014-10-17
You're welcome.

The first line just updates the information about available packages and their versions. It doesn't upgrade those packages. That's what the other commands are for...

Please use the thread tools to mark this one as solved so other can benefit.

Happy Ubuntuing.

---

