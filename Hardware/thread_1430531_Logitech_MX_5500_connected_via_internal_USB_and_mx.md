---
title: "Logitech MX 5500 connected via internal USB and mx5000-tool"
date: 2010-03-15
forum: Hardware
---

### Post by nicholas.alipaz on 2010-03-15
I am attempting to use mx5000-tool to set my Logitech MX 5500 keyboard's lcd screen settings.  However, my keyboard is connected via the computer's INTERNAL BLUETOOTH.

What works:
[LIST]
[*]Installing and mx5000-tool and getting it to run.
[*]Keyboard is connected and working properly, all keys work with an exception of a few that don't register in xev.
[*]I can find the mac address of the keyboard.
[/LIST]
What doesn't work:
[LIST]
[*]Can't run any mx5000-tool commands using my mac address or anything else that I can think of.
```
nicholas@alipaz-asus:~$ hidd --show
00:07:61:B5:A4:BF Logitech MX5500 Keyboard [046d:b30b] connected 
00:07:61:AD:4E:7C Logitech MX Revolution Mouse [046d:b007] connected
nicholas@alipaz-asus:~$ sudo mx5000-tool -d 00:07:61:B5:A4:BF -b
Could not open device or improper device (No such file or directory)
nicholas@alipaz-asus:~$ sudo mx5000-tool -d 046d:b30b -b
Could not open device or improper device (No such file or directory)
nicholas@alipaz-asus:~$ sudo mx5000-tool --device /dev/hiddev0 --beep
Could not open device or improper device (No such file or directory)
nicholas@alipaz-asus:~$ sudo mx5000-tool --device 00:07:61:B5:A4:BF --beep
Could not open device or improper device (No such file or directory)
nicholas@alipaz-asus:~$ sudo mx5000-tool --device obex://00:07:61:B5:A4:BF --beep
Could not open device or improper device (No such file or directory
```
[/LIST]

---

### Post by Demosthenesaus on 2010-10-18
Same problem, Ubuntu 10.10 MX5500 with generic BT dongle - any luck?

---

### Post by kniwor on 2010-11-13
Any solution to this problem?

---

### Post by rolvo_volvo on 2010-11-27
Hi,

this is a question of permissions. More information about configuration can be found [here]("http://www.gentoo-wiki.info/Logitech_Cordless_Desktop_MX_5000"). Just try it with a "sudo" before.

Currently I'm running Lucid on my desktop and Maverick on my notebook. On both systems I get the the following error if I try to send a command to the keyboard:

```
tom@daemonenstall:~$ sudo mx5000-tool -d /dev/hidraw0 -b
Could not open device or improper device (Inappropriate ioctl for device)
```

Any clues?

Best, rolvo_volvo

---

