---
title: "Update caused boot fail -newbie question"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by tozhan on 2009-02-01
Hi, I recently upgraded to Kernel 2.6.27-11 but after a reboot ubuntu fails at the splash screen and falls back to busybox prompt. none of the options in grub load and im not sure how to fix the problem. I would reinstall ubuntu but i dont want to have to reconfigure the whole OS, can i reinstall but keep my /home folder (and hence all my settings)?
is there anyway to fix boot error, maybe install the kernal from busybox?

Ill try to copy down the error messages.

Thanks

T

---

### Post by tuxxy on 2009-02-01
You could try to [restore GRUB ]("http://ubuntuforums.org/showthread.php?t=224351")or you could move your /home folder to a new seperate partition then reinstall Ubuntu to your / partition saving all your settings and files.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by tozhan on 2009-02-01
Thanks ill try fixing grub now.

For what its worth these are the messages i get:

Current working drive - /ubuntu/disks
Gave up waiting for root device.
ALERT! /dev/disk/by-uuid/CE200392200380A7 does not exist. Dropping to shell.
Busybox v1.10.2
(initramfs)

hope that helps a bit.

EDIT:

i was unable to edit grub from the live cd boot. also i couldnt access my home folder from the live cd boot so i cant back it up.

plz help :)

Thanks
T

---

### Post by tuxxy on 2009-02-02
> **tozhan said:**
> Thanks ill try fixing grub now.

For what its worth these are the messages i get:

Current working drive - /ubuntu/disks
Gave up waiting for root device.
ALERT! /dev/disk/by-uuid/CE200392200380A7 does not exist. Dropping to shell.
Busybox v1.10.2
(initramfs)

hope that helps a bit.

EDIT:

i was unable to edit grub from the live cd boot. also i couldnt access my home folder from the live cd boot so i cant back it up.

plz help :)

Thanks
T

What was the issue restoring GRUB, it will work if you follow the guide through and copy/paste the commands into terminal so you don't mistype.

---

### Post by avtolle on 2009-02-02
It looks to me that the OP did a Wubi install. I want to suggest that the Wubi sub-forum be consulted for assistance.

---

### Post by geekas on 2009-02-05
I had exactly the same problem with the same error after updating to 8.10. I found if I chose the previous kernal in the GRUB list 2.6.24-23 the system booted ok. I am still comparing boot records to see if I can nut out where it is tripping over. Meanwhile I have edited /boot/grub/menu.lst to choose the second kernal (default 2) until an answer is found.

---

### Post by Jeenyus on 2009-02-05
I have a similar problem;

I updated to kernel 2.6.27-11 from 2.6.27-9 and luckily I'm dual booting so I am able to still boot into 2....-9 but whenever I try and boot into 2....-11 I get brought to a command line looking screen and it freezes at one step, I forget exactly which one.

I am wondering if there is a way to delete the updated kernel (2.....-11) and then just try and re-update and hope it works this time.

Thanks,
Jeenyus

---

### Post by simple.0 on 2009-02-08
Well, I got the same problem.  Was fishing around and by fluke happened to find out that if I switched to the /dev directory and exited initramfs the system would continue and boot up correctly.  I.E.

initramfs> cd /dev
initramsfs> exit

Seems somethings wrong with a cd line somewhere.  I looked in the grub menu.lst file and it specifies correctly /dev/disk/by_uuid/ and the correct uuid.  really weird.

You may be able to get your machine up if you type the above two command lines every time you boot after you get to the initramfs prompt.  In the meantime I'm still trying to get to the bottom of this.

(Might need some help from Ubuntu.org here.)

---

