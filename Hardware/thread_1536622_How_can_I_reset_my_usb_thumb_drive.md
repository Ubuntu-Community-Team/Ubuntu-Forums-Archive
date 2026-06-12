---
title: "How can I reset my usb thumb drive?"
date: 2010-07-22
forum: Hardware
---

### Post by xpluto on 2010-07-22
I got a usb thumb drive which was  to be 32gig but only holds about 5gig.
Can I scan the drive to findout what size it is and to reset the ID
                          **Additional Details**

                                     I  got a usb thumb drive which was to be 32gig but only holds about 5gig.
Can I scan the drive to findout what size it is and to reset the ID

---

### Post by C.S.Cameron on 2010-07-22
Have a look at it in gparted.

---

### Post by pricetech on 2010-07-22
Gparted will show the usable size of the drive.  It may have been partitioned, or you may have gotten stiffed when you bought it.  I've heard stories of such.

---

### Post by xpluto on 2010-07-24
ok i tried gparted it doesn't work for :(
i distinguish the partition as 32 gig and i know it is less than 32 gig

---

### Post by sidzen on 2010-07-24
> **xpluto said:**
> ok i tried gparted it doesn't work for :(
i distinguish the partition as 32 gig and i know it is less than 32 gig

A very good manual with information on the topic "Partitioning the USB Stick" is here"
[http://manual.sidux.com/en/bios-freedos-en.htm](http://manual.sidux.com/en/bios-freedos-en.htm)
I've referred to it may times to deal with the problem which you have encountered.  
I know it will help if read carefully!
8)

---

### Post by xpluto on 2010-07-25
i tried ur link it was for updating BIOS!
then nothing worked

---

### Post by xpluto on 2010-07-26
up

---

### Post by xpluto on 2010-07-28
any help?  i really need my thumb drive

---

### Post by IcarusR on 2010-07-28
> ok i tried gparted it doesn't work

What do you mean, gparted does not see usb drive at all or does not see it as big as you think it should be ??

Try fdisk with USB plugged in, from a terminal type...

```
sudo fdisk -l
```

This will show you details of all drives attached to your box.

Gparted documentation here ..

[http://gparted.sourceforge.net/documentation.php]("http://gparted.sourceforge.net/documentation.php")

---

### Post by linux18 on 2010-07-28
back it up and reformat it

---

