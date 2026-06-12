---
title: "Scanner HP ScanJet 2400c. Permissions."
date: 2011-06-06
forum: Hardware
---

### Post by Lexus45 on 2011-06-06
Hi guys.

The scanner works fine after some googling. There's only one problem: after each system reboot I have to manually 'correct' permissions to let the scanner work:
```

support@manager77-1-desktop:~$ lsusb 
...
Bus **007** Device** 004**: ID 03f0:0a01 Hewlett-Packard ScanJet 2400c
...

``````
sudo chmod 666 /dev/bus/usb/007/004
```The solution of changing the permissions I've read in the tutorial found by Google.
I only dislike that I have to do this each time the PC was rebooted.
```
support@manager77-1-desktop:~$ ll /dev/bus/usb/007/004
crw-rw-rw- 1 root root 189, 771 2011-06-06 10:10 /dev/bus/usb/**007**/**004**

```The PC is not mine, it's in another city, and each time the manager writes/calls me to help him (to do this), as he doesn't have admin (root) permissions.

Is there any solution to fix it for ever?

**[COLOR=DarkGreen]I found the solution but haven't tried it yet.[/COLOR]** If anybody is interested, [here it is]("http://www.linuxquestions.org/questions/linux-hardware-18/scanner-hp-scanjet-2400c-chmod-dev-bus-usb-884965/#post4378820").

---

### Post by desertdog on 2011-06-14
[https://help.ubuntu.com/community/SettingScannerPermissions](https://help.ubuntu.com/community/SettingScannerPermissions)

---

