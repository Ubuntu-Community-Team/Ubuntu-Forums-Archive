---
title: "Looking for CD/DVD external USB that I can boot from for UBUNTU install?"
date: 2015-11-04
forum: Hardware
---

### Post by DVD-R on 2015-11-04
Hi All,
I'm wondering if there is an external USB CD/DVD device that anyone knows of that can be used for UBUNTU installations on PCs that don't have internal disk devices?
I would assume it would have to be a device that appears as a thumb drive to the bios, and thus doesn't require special driver.
I'm really not interested in the net-boot method.

Sincere thanks
:-]

---

### Post by yancek on 2015-11-04
You need to clarify exactly what you want.  You can install Ubuntu to any flash drive if it is large enough so I'm not sure what you're asking.  You would need to use a CD/DVD or flash drive with Ubuntu on it to install, either that or a netinstall which you say you don't want.  You could boot the iso directly if you had Grub but since you don't have any internal drives I would expect you don't have any operating system.  You'll need to post more specifics.

---

### Post by ajgreeny on 2015-11-04
Why use a USB attached CD/DVD drive; why not just use a USB flash drive memory stick?

If the computer will boot from a USB attached DVD drive it should also boot from a USB flash drive, and will also probably be much quicker when using the live system and installing to your hard drive.

---

### Post by DVD-R on 2015-11-05
Thanks for your reply yancek.
Lets say I have a laptop/PC that has no internal CD/DVD drive.
Perhaps I have to do some repairs....perhaps a crashed OP system.
I have the ability to boot up into USB, by selecting it from the bios at time of boot-up.
But I don't have any software, such as an ISO ect, in a thumb-drive.
But I do have a grub repair, or a Ubuntu installation CD.
Then it would be awesome to have a CD/DVD external device which can plug into the PCs USB port and will function exactly as a USB thumbdrive would.
The PC will boot-up from the USB CD/DVD device, just exactly as it would if I were using a thumbdrive.
In this case, I would assume that a CD/DVD device that requires special drivers to talk to the PC won't work as the bios will not be able to talk to such a device.
But if there is a CD/DVD device that is designed in such a way as to replicate a thumb drive, the bios would be able to access its contents and boot-up from them.

---

### Post by westie457 on 2015-11-05
Do you mean something similar to this?

---

### Post by DVD-R on 2015-11-05
yes...thanks for the picture :-]
I can build installation thumb drives.
Actually, I have started to accumulate them because of laptops which don't come with disk drives.
So I'm looking at my accumulating collection of boot-able thumb-drives and my massive collection of boot-able ISOs in disk.
Man would it be cool if I could just pop an install CD into a disk device, plug that device into the USB port of the PC and boot up with it.  :-]

---

### Post by tea for one on 2015-11-05
> **DVD-R said:**
> yes...thanks for the picture :-]
I can build installation thumb drives.
Actually, I have started to accumulate them because of laptops which don't come with disk drives.
So I'm looking at my accumulating collection of boot-able thumb-drives and my massive collection of boot-able ISOs in disk.
Man would it be cool if I could just pop an install CD into a disk device, plug that device into the USB port of the PC and boot up with it.  :-]

I hope that I've understood you correctly:-

I thought that all CD/DVD external drives connected to a USB port would boot a DVD/CD with a correctly burnt Linux ISO.

For example, I have an external LG Device (approx 7 years old) and I use it 6/7 times per year and it never fails.

---

### Post by yancek on 2015-11-05
I'm not really clear on what the problem is.  You can boot from a usb but have no CD/DVD drive but have a number of CD/DVD's you want to use.  Why not combine all the various iso files of distributions and/or utilities on one or two flash drives and select from them on boot?

---

### Post by sudodus on 2015-11-06
> **DVD-R said:**
> yes...thanks for the picture :-]
I can build installation thumb drives.
Actually, I have started to accumulate them because of laptops which don't come with disk drives.
So I'm looking at my accumulating collection of boot-able thumb-drives and my massive collection of boot-able ISOs in disk.
Man would it be cool if I could just pop an install CD into a disk device, plug that device into the USB port of the PC and boot up with it.  :-]

You need not accumulate thumb drives, because they can be re-used many times. See this link

[Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

So you can store ISO files in a HDD and build an installation thumb drive, whenever you need it in a couple of minutes. Or if you wish, you can make some multiboot thumb drives as suggested by yancek.

---

### Post by efflandt on 2015-11-06
I got an LG GP40LB10 years ago to use with my 10.1" tablet PC that came with Win7 Pro on 32 GB SSD, but no CD/DVD [it currently boots Lubuntu or Ubuntu 12.04 from its SD slot (internally USB connected)]. Although, that was USB 2.0 and they likely have a newer model with USB 3.
[http://www.lg.com/us/burners-drives/lg-GP40LB10-external-dvd-rewriter](http://www.lg.com/us/burners-drives/lg-GP40LB10-external-dvd-rewriter)

It shows up in 14.04 lsusb as:
Bus 002 Device 007: ID 0e8d:1836 MediaTek Inc. Samsung SE-S084 Super WriteMaster Slim External DVD writer

The only CD I had handy was an old one from Lucid, since I normal use USB memory sticks to install Ubuntu:```
efflandt@XPS-8100-1404:~$ ls -l /media/efflandt/Ubuntu\ 10.04\ LTS\ amd64/
total 1470
-r--r--r-- 1 efflandt efflandt     143 Apr 29  2010 autorun.inf
dr-xr-xr-x 2 efflandt efflandt    2048 Apr 29  2010 casper
dr-xr-xr-x 3 efflandt efflandt    2048 Apr 29  2010 dists
dr-xr-xr-x 2 efflandt efflandt    2048 Apr 29  2010 install
dr-xr-xr-x 2 efflandt efflandt   16384 Apr 29  2010 isolinux
-r--r--r-- 1 efflandt efflandt    4634 Apr 29  2010 md5sum.txt
dr-xr-xr-x 2 efflandt efflandt    2048 Apr 29  2010 pics
dr-xr-xr-x 4 efflandt efflandt    2048 Apr 29  2010 pool
dr-xr-xr-x 2 efflandt efflandt    2048 Apr 29  2010 preseed
-r--r--r-- 1 efflandt efflandt     228 Apr 29  2010 README.diskdefines
lr-xr-xr-x 1 efflandt efflandt       1 Apr 29  2010 ubuntu -> .
-r--r--r-- 1 efflandt efflandt 1469477 Apr 26  2010 wubi.exe
```

---

### Post by DVD-R on 2015-11-10
Thank you very much for all of the information on the LG GP40LB10.
I will definitely look into it!!

I want to thank all of the others also who took the time to provide info.
The idea of putting multiple ISOs on a thumbdrive is pretty interesting.
If I have time, I'll experiment with that.
I think we must admit though, having an external DVD device that connects to a machine without one and can be used to boot up Linux, would be a nice thing!
Thanks all :-]

---

