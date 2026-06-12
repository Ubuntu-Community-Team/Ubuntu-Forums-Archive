---
title: "Grub error 17 on Jaunty install"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by sparkey7t on 2009-04-30
Hey all, I am getting an error 17 after I installed Jaunty. I changed hard drive and did a fresh install of Jaunty on new drive.

Have searched the forums but haven't found anything that works yet.
I am dual booting with XP.  I did a mbrfix and XP loaded fine, but when I tried reinstalling jaunty I still get error 17 on restart.

Any help appreciated.

---

### Post by sparkey7t on 2009-04-30
Forgot to add some specs.  The install is on a desktop computer with four hard drives, two SATA and to IDE. On one SATA is the original XP install and the other SATA I added is Jaunty, the two IDE are for storage.  I have had other versions of Ubuntu on this computer before but those were on an IDE drive and worked fine.

I have tried running 

```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```

the first appears to work and the second gives Error 15: File not found

---

### Post by sparkey7t on 2009-04-30
Solved with supergrub

---

### Post by maxkool on 2009-05-01
I'm having the same problem right now. How did you solve it with Supergrub? (I'm assuming that's the Super Grub Disk)

LE. Solved, by going into BIOS and changing the Hard Disk boot order. (it seems Grub expects to boot off the first partition on the first drive)

---

### Post by mihlub on 2009-09-24
i am having this grub error 17 right after a fresh 9.04 jaunty install. i had been using ubuntu for about a year now mostly just inside virtualbox guest with windows vista as host. now that i feel comfortable with it i try to install it on my main system. install 904 on the system with this spec:
- cpu intel i7-920
- ram 12gb
- 4 sata hard drive. one of which is a 30gb ssd drive.

i am installing it on the main boot drive 30gb ssd-- only one partition on this drive. previously had vista and windows 7rc on it with no issue. The installation of 904 64bit went fine just as it had been inside those virtualbox guest had been doing. the issue is right after it reboot it say:

grub stage 1.5.
grub error 17


i did Google this issue. it seems like many people have this same problem but none of the suggested solution works for me. if you have any suggestion i am willing to try it.

thanks.

---

### Post by Darkwing-Duck on 2009-09-24
Try reinstalling GRUB and trying it that way. Here is a good guide to help you with that.

[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

Hope this can help fix it.

---

### Post by rreese6 on 2009-09-24
Mihlub,
the error 17 is a device error. Grub can not find the partition with the  vmlinuz file on it.
We need more information because your partition may be faulty.

Do this:

boot from a live CD and post the results here of these two commands

```

gedit /boot/grub/menu.lst

sudo fdisk -l
```

---

### Post by mihlub on 2009-09-24
:KS [COLOR="Blue"][SIZE="3"]thanks darkwing i followed the first link you gave above and follow the instruction there to re-install grub. i did encounter a few errors but after a few attempts later it finally said install successful. i reboot and there it popup my ubuntu that i had installed. THANKS SO MUCH.  i had been up for a few nights just re-installing 904 over and over for a dozen times. each time it will fail after the reboot. i hope cannonical get rid of these grub issues in future releases.[/SIZE][/COLOR]
[COLOR="Blue"][COLOR="Blue"]
again thanks.[/COLOR][/COLOR]

--mihlub.

---

