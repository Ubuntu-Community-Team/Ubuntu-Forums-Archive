---
title: "160 Gig hard drive with OLD bios"
date: 2007-06-16
forum: Hardware &amp; Laptops
---

### Post by RabidWeezle on 2007-06-16
I used to use a DDO, or what's called a Dynamic Drive Overlay to control my hard drive because I didn't have newer bios, and I can't get an upgrade because well, msi don't care about older motherboards from 2004 . 

Well, when you install linux it overwrites the DDO because it resides in the master boot record of the hard drive. So the only way to get ubuntu to install is basically manually partition the drive and make the first partition the /boot partition around 100 megs or so, then add on your ext3 "/", and then your swap partition.  

Problem I'm having now though is how do I make the "/" partition grow now? I need it to fill the rest of the drive. According to other people with the problem, you just do what I did and once linux loads, it recognises the rest of the hard drive space EVEN THOUGH the bios reports it wrong. I figure this operation would require booting the live cd so I can work on the filesystem unmounted and somesuch. So if someone could post me step by step instructions for setting the new size of the hard drive, that would be great.

---

### Post by RabidWeezle on 2007-06-16
bump

---

### Post by IntuitiveNipple on 2007-06-16
From what you said I initially thought you'd already got it correct. One of us may be confused!

Can you show the output of:
```
$ sudo fdisk -ul /dev/<disk_id>
```
where <disk_id> is the device-name of the drive, e.g. /dev/sda.

---

