---
title: "SUDO commands"
date: 2008-12-19
forum: Hardware
---

### Post by FarmerReg on 2008-12-19
Does anyone know of any SUDO commands for mounting and unmounting portable HDD's/flash drives??

I really hate having to turn my pc on and off just to be able to use my portable hdd's and flash drives.

Any help is greatly appreciated.




-Farmer

---

### Post by jocko on 2008-12-19
There must be something wrong with your system. All you need to do to mount any usb drive is simply plug it in. It should be detected and mounted in a few seconds.
If it's not working the way it's supposed to, it's better to find out what the problem is and fix it instead of asking for a workaround...
Unfortunately I have no idea what causes the problem, but I have tip which may help you or someone else figure it out.

Check the output of this command:
```
lsusb
```both before and after you plugged in a usb drive.
Does the output change (you may need to wait a while and run the command again if nothing changes the first time)? If it does, that means the usb drive is detected, but if it doesn't change there is something wrong with whatever part of the os is responsible for detecting new usb devices.
If it's detected but just not mounted the problem is in whatever program is responsible for automatically mounting removable drives.

---

