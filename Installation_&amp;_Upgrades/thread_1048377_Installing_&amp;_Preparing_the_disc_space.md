---
title: "Installing &amp; Preparing the disc space"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by ajpearson on 2009-01-23
I want to load ubuntu on to my new laptop. The vista hard drive is split into 2 drives. The C drive is 69.5 gb (38.5 free) and the D drive is 69.5 gb (all free). I want to dual boot giving Ubuntu the complete D drive.

When I get to the step 4 do I select the guided - use the largest continuous free space - will it automatically select the D drive. Or will it add some of the C drive in (I will have defragged and shrinked the Vista C drive).

Or should I select manual - does manual allow me to select the amount of gb I give Ubuntu.

Finally, can I exit out of this step if I get confused (often happens) without going through with the whole installation process.

Thanks for any help offered.


Andrew

---

### Post by mozkill on 2009-01-23
If you have a spare hard drive also in the system I would do a CloneZilla backup of the hard drive and then go ahead and do your install.  If it doesn't work out then you can restore back to your CloneZilla image and try again.

Of course, this probably requires that you have a second hard drive to back your image up to, which is not usually the case with a laptop.  In that case you can back up the image to a network drive on a computer nearby.

---

### Post by ajpearson on 2009-01-23
Thanks for such a quick reply. Apologies for maybe not fully understanding your advice. I have an external hard drive with plenty of space. Is Clonezilla within vista or software I need to download from the net.

Do you think it will select the D drive and should I go manual or automatic on the installation?

Thanks

Andrew

---

### Post by russu52 on 2009-01-23
i did a dual install on a vista laptop. as you said, since vista splits the hard drive into two partitions, i had cleaned the D part (on an external HDD) and installed ubuntu on the D part. i did not find any problems, and my laptop hard disk was quite small (32.5 gb for every part). WARNING: if you like ubuntu, you will probably end up making a clean wipe of your entire drive, as i did!

---

### Post by russu52 on 2009-01-23
Opps!! just forgot! if you choose manual install you may uses only a part of D, and not all. Your vista installion shoulds remain untouched with the process.
You can install and run ubuntu from an external hdd (without touching anything on your Laptop hdd), and on your bios select boot from usb Hdd. But there i suggest xubuntu, which is lightweight and makes running faster...
OR, you can install ubuntu through windows itself (using WUBI) which creates a large file into your hard drive, where you can use ubuntu at leisure, and remove when you want to...

---

### Post by ajpearson on 2009-01-23
Did you do the automatic (Ubuntu automatically selects the free D drive or is manual better because you can then select the drive.

Thanks for your speedy reply.

I do like Ubuntu alot - but want to keep vista just in case.

Andrew

---

### Post by russu52 on 2009-01-23
depends on how much space you are ready to give up for ubuntu - if i am not mistaken the automatic install takes up all the d partition. 

do you use vista for anything particular?

---

### Post by ajpearson on 2009-01-23
No - just bought a new laptop - it has planty of hard drive - my old PC (XP) dual booted with Ubuntu on much less space - and I used Ubuntu for everything apart from lightscribe. So happy with Ubuntu just thought that the D drive would be more than enough for Ubuntu while leaving vista with the C Drive again should be more than enough for the few things I may use it for.

Thanks

Andrew

---

### Post by mozkill on 2009-01-26
> **mozkill said:**
> If you have a spare hard drive also in the system I would do a CloneZilla backup of the hard drive and then go ahead and do your install.  If it doesn't work out then you can restore back to your CloneZilla image and try again.

Of course, this probably requires that you have a second hard drive to back your image up to, which is not usually the case with a laptop.  In that case you can back up the image to a network drive on a computer nearby.

Clonezilla is a freeware Ghosting software.  Download the CloneZilla light" ISO image and burn it to a CDROM and then boot with it.  You can back up the image/copy of your entire physical C+D drive to either a nearby network share OR to a different physical disk on the same machine.  You cant use Clonezilla to backup a partition to another partition on the same disk.

The idea here is to make a complete and total backup so that when your install overwrites the boot sector and partition table then you can still restore back to where you were if something goes wrong.     Also, it will allow you to practice different ways of installing and figure out what works best for you.  Afterwards you will know more than most people who reply to this thread.   Just be careful while you are making your backup so that you know how to restore it.

[http://clonezilla.org/screenshot/?in_path=/01_Clonezilla](http://clonezilla.org/screenshot/?in_path=/01_Clonezilla)

---

