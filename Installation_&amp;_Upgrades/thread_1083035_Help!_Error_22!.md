---
title: "Help! Error 22!"
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by Charkel on 2009-02-28
First of all I just wanna say that I'm really angry atm so I'm sorry if I do or say something dumb.
And dunno if this is the right section.

Well!
I had 2 partitions on my system disk. My windows partition was too small so I decided to merge the to partitions into one. (In other words, increasing my windows partition)

But, when I had done so and rebooted my computer i got this beatuiful message;

> GRUB loadin, please wait...
Error 22

How can I fix this?! I got no windows CD and I cannot boot linux either. I do got a ubuntu 6.1 CD if that would help my anyhow.
My current installation is 7.10.

Please help!

P.S
I'm on laptop atm if someone's wondering how I can post this...

---

### Post by rhcm123 on 2009-02-28
You modified partitons WITHOUT correcting GRUB... tsk tsk.. even modifying partitions like that is stupid. No offence, but this is the kind of situation i put my favoite quote of all time: "Linux makes the critical assumption you know what you are doing." Now, to fix this debacle.

Boot from the "6.1" CD (which dosen't exist so i'm assuming its another version) and hit the "Rescue a broken system" option. Answer all the prompts and open up a shell, then find and post your /boot/grub/menu.lst file. (Thats gonna be hard cause your gonna have to copy it all manually.)

After that, I can help you. I think.

---

### Post by Charkel on 2009-02-28
> **rhcm123 said:**
> You modified partitons WITHOUT correcting GRUB... tsk tsk.. even modifying partitions like that is stupid. No offence, but this is the kind of situation i put my favoite quote of all time: "Linux makes the critical assumption you know what you are doing." Now, to fix this debacle.

Boot from the "6.1" CD (which dosen't exist so i'm assuming its another version) and hit the "Rescue a broken system" option. Answer all the prompts and open up a shell, then find and post your /boot/grub/menu.lst file. (Thats gonna be hard cause your gonna have to copy it all manually.)

After that, I can help you. I think.

Just tried to boot the cd but I cant! I get "Buffer I/O Error on device hdc-logical block..."
I didn't have in mind that the grub would **** up. Is there any way that I can remove the GRUB so that it goes direct to try to boot windows? I don't care if I lose my linux for now.

I got an even older ubuntu cd that I'm gonna try and an old knoppix CD.
But if nothing of that works I only got hiren's boot cd, wich i know work tho :'(

EDIT: Yes! I got an old live cd running. I am currently on ubuntu 6.06

---

### Post by Charkel on 2009-02-28
> **rhcm123 said:**
> You modified partitons WITHOUT correcting GRUB... tsk tsk.. even modifying partitions like that is stupid. No offence, but this is the kind of situation i put my favoite quote of all time: "Linux makes the critical assumption you know what you are doing." Now, to fix this debacle.

Boot from the "6.1" CD (which dosen't exist so i'm assuming its another version) and hit the "Rescue a broken system" option. Answer all the prompts and open up a shell, then find and post your /boot/grub/menu.lst file. (Thats gonna be hard cause your gonna have to copy it all manually.)

After that, I can help you. I think.

I hope youre still online and can help me :o

Heres the menu.lst file from my ubuntu partition.
[http://data.fuskbugg.se/skalman01/-menu.lst](http://data.fuskbugg.se/skalman01/-menu.lst)

I havent done any recovering as you said. What whill that change? And how do i do it?

---

### Post by Pumalite on 2009-02-28
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)
You might need to reinstall Grub. Maybe your partitions are screwd up.
Post:
```
sudo fdisk -lu
```

---

### Post by Charkel on 2009-02-28
> **Pumalite said:**
> [http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)
You might need to reinstall Grub. Maybe your partitions are screwd up.
Post:
```
sudo fdisk -lu
```

I tried to use this guide to recover grub but it failed to find stage1:
[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

sudo fdisk -lu:
> ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   234436544   117218241    7  HPFS/NTFS

Disk /dev/hdb: 60.0 GB, 60000000000 bytes
255 heads, 63 sectors/track, 7294 cylinders, total 117187500 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    69641774    34820856    7  HPFS/NTFS
/dev/hdb2        69641775   117178109    23768167+   5  Extended
/dev/hdb5        69641838    70637804      497983+  82  Linux swap / Solaris
/dev/hdb6        70637868   117178109    23270121   83  Linux

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              

---

### Post by rhcm123 on 2009-02-28
> **Charkel said:**
> I tried to use this guide to recover grub but it failed to find stage1:
[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)


Sorry, im back
would you post your menu.lst file.. I need that to fix grub.

Edit: Here, google is your friend: [click this]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/")

---

### Post by Charkel on 2009-02-28
> **rhcm123 said:**
> Sorry, im back
would you post your menu.lst file.. I need that to fix grub.

Edit: Here, google is your friend: [click this]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/")

Thx but I fixed it. I tried like 10 ways of re-installing the GRUB and none worked. I managed to do a few steps on every tutorial untill i encountered problems. So I just re-installed ubuntu and got it all to work.

So apparently the GRUB was my only problem. I'm on my XP partition now and it works great. I now got a bigger C drive :)

---

### Post by rhcm123 on 2009-02-28
> **Charkel said:**
> Thx but I fixed it. I tried like 10 ways of re-installing the GRUB and none worked. I managed to do a few steps on every tutorial untill i encountered problems. So I just re-installed ubuntu and got it all to work.

So apparently the GRUB was my only problem. I'm on my XP partition now and it works great. I now got a bigger C drive :)

Would you mind posting what you did for other users for with the same problem (and also for me, as what you did sounds cool :) )

---

