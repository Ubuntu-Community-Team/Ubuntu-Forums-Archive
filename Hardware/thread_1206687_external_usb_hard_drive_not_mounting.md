---
title: "external usb hard drive not mounting"
date: 2009-07-07
forum: Hardware
---

### Post by mickyboy on 2009-07-07
I'm a newly converted Linux Lover and am having trouble with my external hard drive.
Being a Linuxly challenged newbie was after some much needed assistance.
My external HD won't mount. Not showing anywhere but It is showing up in GParted although it says there is no filesystem. What should I do to sort this out. Dummy instructions appreciated.
Incidently i'm running Ubuntu 9.04


Many Thanks

---

### Post by cariboo on 2009-07-07
The first thing we need is a little ore information. Open an Application-->Accessories-->Terminal and type:

```
sudo fdisk -l
```

that's a lowercase L, with your external drive connected. Paste the output in your next post.

---

### Post by mickyboy on 2009-07-08
Thanks for reply cariboo907.

For some reason It won't let me copy and paste to some "fill in boxes" so have attached a screenshot

many thanks


Have just tried to upload from my digital camera and it's not recognizing that either.
Hope that helps.

---

### Post by mickyboy on 2009-07-10
> **cariboo907 said:**
> The first thing we need is a little ore information. Open an Application-->Accessories-->Terminal and type:

```
sudo fdisk -l
```

that's a lowercase L, with your external drive connected. Paste the output in your next post.
Have replied but pressed 'new reply' previously so might not get email notification.

mickyboy (HD not mounting)

---

### Post by Tharmas on 2009-07-10
Strange... You have two identical 80GB disks?
Could you please report the brand/model of you usb hard drive and the output of the " lsusb " command?
 From what you said it appears that the usb device was connected but the not mounted.

---

### Post by mickyboy on 2009-07-11
> **Tharmas said:**
> Strange... You have two identical 80GB disks?
Could you please report the brand/model of you usb hard drive and the output of the " lsusb " command?
 From what you said it appears that the usb device was connected but the not mounted.


mickyboy: hmmm. I had tried a little self maintenance which to be honest, with my level of know-how was a bit of a stab in the dark. This is the wreckage that's left over.
I can't find a model number on my HD but can tell you it's a Hitachi i Smart 80 G. 
When I said please explain everthing in dummy terms i'm afraid I wasn't exagerating.
I have very rudimentary knowledge of Linux unfortunately but my theory is, have a go - run for help later...of course, i wouldn't have a shot if i didn't think i at least had a chance. 
Anyway....I did discover somewhere on my laptop the name of this elusive HD but due to my incompetence am unable to find it again.

As for a Isusb command - how do I go about that?
God help me

---

### Post by dePeatrick on 2009-07-15
I got the same problem here so am watching this thread with my fingers crossed. mine is not showing up in gparted though..!

---

### Post by mickyboy on 2009-07-15
[quote=dePeatrick;7622133]I got the same problem here so am watching this thread with my fingers crossed. mine is not showing up in gparted though..![/quote

Not even when you click GParted menu then Devices? I done this and there it was. I done a complete reformat and everything is fine now. I was lucky enough in that my HD was new and so empty.
Not sure of your level of know-how but if this is any good to you will be happy to help.

---

### Post by Tharmas on 2009-07-20
It is **lsusb** starting with **l** as in **l**ubricant not **I** as in **i**mage.
and you just have to enter the command in a terminal.
And does the drive mount in other linux computer/system.
Does it mount in windows?

---

### Post by mickyboy on 2009-08-01
> **Tharmas said:**
> It is **lsusb** starting with **l** as in **l**ubricant not **I** as in **i**mage.
and you just have to enter the command in a terminal.
And does the drive mount in other linux computer/system.
Does it mount in windows?


Cheers very much Tharmus but I have managed to fix things myself by reformatting the HD
Much appreciated though.

---

### Post by frog3764 on 2009-08-01
Here comes another newbie/dummy.  My external does show in Gparted but can't recognize it.  It is a 320GB Seagate.  I found on the site docs - System - Administration - Partition Editor - to label it, but the label is greyed out so I can't do that.  Here is the fdisk

 Disk /dev/sda: 33.8 GB, 33820286976 bytes
255 heads, 63 sectors/track, 4111 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa82ba82b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3937    31623921   83  Linux
/dev/sda2            3938        4111     1397655    5  Extended
/dev/sda5            3938        4111     1397623+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568668   54  OnTrackDM6

All help in the dummy format is appreciated.

---

