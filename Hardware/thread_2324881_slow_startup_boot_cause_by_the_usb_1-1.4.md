---
title: "slow startup boot cause by the usb 1-1.4"
date: 2016-05-17
forum: Hardware
---

### Post by miko5054-gmail on 2016-05-17
[TABLE]
[TR]
[TD="class: votecell"][CENTER]
[/CENTER]
[/TD]
[TD="class: postcell"]For some reason the boot time is very slow
I run the **dmesg** command in order to see what i tacking so much time.
```
[    8.191775] USB Video Class driver (1.1.1)
[    8.230700] usb 1-1.4: USB disconnect, device number 3
[   98.199636] aufs 4.x-rcN-20160111
```
Then i found out the **usb 1-1.4** action is the issue .
Im using kernel version **4.4.0-22-generic**
How can i solve it ?[/TD]
[/TR]
[/TABLE]

---

### Post by howefield on 2016-05-17
Thread closed, duplicate here : [http://ubuntuforums.org/showthread.php?t=2324880](http://ubuntuforums.org/showthread.php?t=2324880)

---

