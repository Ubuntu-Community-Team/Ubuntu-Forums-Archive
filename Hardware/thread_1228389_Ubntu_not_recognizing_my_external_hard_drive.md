---
title: "Ubntu not recognizing my external hard drive"
date: 2009-07-31
forum: Hardware
---

### Post by Lakeside5 on 2009-07-31
I'm going to try this again.  I wasn't able to figure this out before.
Ihave an external hard drive that was able to be read by both machines (this one, which has hardy heron lts ubuntu on it, and the other, has Win xp) Now, neither seems to 'see' it when I connect it to the usb port. Can someone please help me with a 'simple' solution, lol
I'm not that good at this. thanks very much.

---

### Post by Lakeside5 on 2009-08-01
Here is the output when I enter sudo fdisk -l if that helps:   
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18a218a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8474    68067373+  83  Linux
/dev/sda2           16248       30401   113692005    f  W95 Ext'd (LBA)
/dev/sda3   *        8475       16247    62436622+  83  Linux
/dev/sda5           16710       30401   109980958+   7  HPFS/NTFS
/dev/sda6           16585       16709     1003999+  82  Linux swap / Solaris
/dev/sda7           16248       16584     2706889+  82  Linux swap / Solaris

---

### Post by Bucky Ball on 2009-08-01
Well, it's certainly not there. It would be listed as 'sdb'. Can you run:

```
sudo blkid

```
... with the external drive plugged in and switched on of course, and post that or look for a /dev/sdb somewhere, please?

---

### Post by Lakeside5 on 2009-08-01
wow, thanks for the quick reply :)
I get this:  /dev/sda1: UUID="2bb4ae08-0d72-4a5a-934d-300f2de4202a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="ac597835-2653-4cc4-98b8-611039f3fc9c" TYPE="ext3" 
/dev/sda5: UUID="20EC85CDEC859DA2" TYPE="ntfs" 
/dev/sda6: TYPE="swap" UUID="7515b654-c489-4506-95f0-caa24f43ccf6" 
/dev/sda7: TYPE="swap" UUID="c3c3cdbb-8cde-4e86-9ca7-416f171eff9f"

---

### Post by Bucky Ball on 2009-08-01
Hmmm. Invisible. My advice would be to try a different USB cable at this point, and possibly another port on the computer and/or the external drive if it has one.

Even if the drive is not mounting when you switch it on, it should be showing up in '/dev/sd?'. There is no sign of it which means this is probably hardware related.

The drive has been working fine until this, works with other machines okay?

---

### Post by Lakeside5 on 2009-08-01
Thanks.  I will have to get another usb cable to try. The one I'm using came with the device.  I tried another port, but that didn't work.  Funny thing is,  I brought the drive to school, and my instructor tried it on his dual OS laptop (windows and Linux are on it) and both OS operating systems recognized it, it showed up on both, so it must be my computer, or how Linux is configured (or NOT configured lol). It was working and suddenly it isn't. hmmmm

---

### Post by Bucky Ball on 2009-08-01
That can happen and I don't think it is the computer. Did the teacher use their USB cable or yours?

Have you got another USB device you can plug in using the same cable?

---

### Post by Lakeside5 on 2009-08-01
Ah, I like the way your mind works,  I will have to get one. thanks
I don't remember, but I think I used my own cable, brought the external hard drive and all.

---

### Post by Bucky Ball on 2009-08-01
Any other external device will do to test that cable and see where the problem is originating. iPod? Even if it doesn't mount, it should show with:

sudo blkid

... in a terminal whatever it is. Anything that is NOT sda*. :)

---

### Post by Lakeside5 on 2009-08-01
Ok, brb

---

### Post by nwadams on 2009-08-01
ok, this might sound strange but plug it in...even though it won't mount or be detected. then reboot your laptop, when it boots up again it should be detected and mount

also what happens when you run ```
dmesg | tail
``` the moment after its plugged in?

---

### Post by Lakeside5 on 2009-08-01
Thanks very much.  It was the cable :) So far it works on my Linux, have to try it on the Windows.

---

### Post by Bucky Ball on 2009-08-01
Excellent news!

---

### Post by Lakeside5 on 2009-08-03
Thanks Bucky Ball, Nwadams, I am so lucky to have found this forum, so I'm not 'all alone' with Linux lol. And the other solutions I am sure i might need somewhere down the road, it's all learning.

---

### Post by nwadams on 2009-08-03
i'm glad to hear it was something trivial. good luck to you in all your future linux endeavors :p

---

### Post by Bucky Ball on 2009-08-04
Your welcome. Good news, good luck and welcome to the forums.

Post again with any further issues. :)

(... and yes, it is all learning but the fruits are worth the labour and you know what they say, knowledge is freedom)

---

