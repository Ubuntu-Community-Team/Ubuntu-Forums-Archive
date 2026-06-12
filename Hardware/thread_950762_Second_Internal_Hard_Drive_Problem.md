---
title: "Second Internal Hard Drive Problem"
date: 2008-10-17
forum: Hardware
---

### Post by weiqiang on 2008-10-17
I'm wondering if anybody has tried installing a second HD to their system. I have Ubuntu 7.04 running with a SATA HD, I got a spared PATA-133 HD from my friend and decided to use it as my storage HD in ubuntu. But the system didn't detect the drive after I plugged in the HD and rebooted. Any thought? Thx.

---

### Post by alphaniner on 2008-10-17
What do you mean when you say it wasn't detected?  Did you run *fdisk -l* (as root)?  If it didn't show up there, go to the BIOS.  If it doesn't show up there, check your cables and jumpers and make sure your PATA controller is enabled.

When you do get it working, I have a bit of advice.  When you format (ext3) a drive/partition with pretty much any of the tools Ubuntu offers, 5% of the space will be reserved for root.  For big drives, this equals way to much lost space.  Use the command

```
mkfs.ext3 -m # /dev/hdXX
```

where # is the amount in % to reserve.  I usually go with 1% just to be safe.

**[COLOR="Red"]Edit:[/COLOR]**

I originally took "system didn't detect the system" as a typo, and read it as "system didn't detect the drive."  If you mean you didn't get to GRUB, make sure your SATA drive is still in the BIOS boot order and not the new PATA drive.  Then when you get to GRUB you may get an error when trying to boot Ubuntu.  If so you will need to edit the boot script for Ubuntu, in particular the line

[code]root            (hdX,1)[\code]

If you only have 2 HDDs, then you would change it from 0 to 1.  This edit will only be temporary, and you will have to edit /boot/grub/menu.lst directly after Ubuntu has loaded.

---

### Post by Therion on 2008-10-17
EDIT: Nevermind... Misread original post.

---

### Post by weiqiang on 2008-10-17
Thanks a lot guys! It was a typo...I meant the system didn't detect the drive... I ran fdisk -l as root and the drive didn't show up, I'm guessing it's probly because of the cable or the jumper.

I'm using a maxtor 300G HD without any jumper on it, it shares the same IDE cable with the dvd-rom. The dvd-rom is not working either.

---

### Post by weiqiang on 2008-10-17
BTW, the IDE cable I'm using is a 40 pins one, rather than 39 pins, so I wouldn't know the if I plugged wrong...I'll double check when I get home...Thanks.

---

### Post by weiqiang on 2008-10-18
Problem solved, it turned out that the DVD-ROM and HD couldn't share the same IDE cable. I used a PCI expansion card to hook up the HD, it works now. Thanks guys.

---

