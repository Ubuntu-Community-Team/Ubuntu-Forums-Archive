---
title: "[SOLVED] Eject function - strange behaviour"
date: 2008-10-23
forum: Hardware
---

### Post by steveydoteu on 2008-10-23
Running 8.10 I and also during use of 8.04, I have encountered issues with ejecting media from my DVD drive.

More often than not, the button press will unmount and then remount the media without opening the tray, usually if I am lucky enough to get the tray to open it will snap back shut.

Using **eject /dev/cdrom/** yeilds similar outputs, it will eject each time, but then proceeds to close the tray immediately afterwards. No error messages are given in the terminal session.

Any assistance would be appreciated on this, the model of the drive is **Optiarc DVD RW AD-7200S**. If you need anymore info I can attach hardinfo reports and lspci outputs etc.

Cheers.

---

### Post by steveydoteu on 2008-10-23
Turns out its not just me: [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/283316](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/283316)

---

