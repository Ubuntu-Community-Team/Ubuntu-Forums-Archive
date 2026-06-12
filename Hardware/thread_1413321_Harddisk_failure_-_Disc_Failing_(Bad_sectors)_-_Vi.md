---
title: "Harddisk failure - Disc Failing (Bad sectors) - Virtual Box"
date: 2010-02-22
forum: Hardware
---

### Post by adityab88 on 2010-02-22
I am using ubuntu Karmic, and I recently installed Virtual Box in order to run Windows XP on it. Anyway, while doing so, I attempted to create a virtual partition of 4 GB which failed because of an error related to VERR_WRITE_PROTECT or something along those lines. Note that it was attempting to write to the disc for a while before returning an error right at the end.

Anyway, then I closed Virtual Box and decided to forget about having a virtual machine for a while.. well then upon rebooting my computer the next time it said that the disc is failing. There are bad sectors in my hard drive now and it says that I should replace my hard disk. Ubuntu works well (apparently at least) but it takes slightly longer to load and I don't ever want to risk making this into a bigger problem.

If you want more information on these bad sectors, do let me know.

Is there now anyway to delete/fix these bad sectors? Any geniuses out there to help me out with this?

---

### Post by RRF2525 on 2010-02-22
[http://www.grc.com/intro.htm](http://www.grc.com/intro.htm)
Spinrite

Spinrite will do it...need to run a level II diagnostic and repair.  I know it's not freeware (and it aint cheap) but it's a must have in the techie-toolbag.  I've rescued more than one dying machine with this.

---

### Post by adityab88 on 2010-02-22
Does anyone know some freeware for this? Because I really can't afford 89 dollars (i'm a student)

---

### Post by adityab88 on 2010-02-22
do you think if i formatted my entire hard drive and reinstall linux it will work without any bad sectors?

---

### Post by adityab88 on 2010-02-22
how about if i format the entire hard drive, will it work after that?

---

### Post by RRF2525 on 2010-02-22
Bad sectors will have to be "repaired" if possible and recovered.  Reformatting won't get you much of anywhere.  If the drive is going "south" then you're either faced with replacing the drive ($$) or repairing it.

---

### Post by ajgreeny on 2010-02-22
You don't mention the age of machine or disks, nor their make.  However, it could be worth downloading the ultimate boot CD from [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) which contains good diagnostic software from many of the major hard disk manufacturers.  It works a bit like a live CD, ie you boot to the CD and then choose what you want to do from a menu that appears.  That may at least give you a second opinion on the health of you hard disk, rather than depend solely on the karmic system tool palimpsest, which I know at one time was giving a lot of false errors on good disks.

---

### Post by Nick_Jinn on 2010-03-12
The Ubuntu community should be aware that many hard drives are being damaged during reformatting since Karmic has been released. Many people have lost multiple NEW hard drives.

Just something to be aware of. There is debate about whose fault it is....the default hardware settings vs Ubuntu not compensating for them. It happens with Karmic but doesnt seem to happen with windows or mac.


I am hoping this issue will get a serious look by the programmers before next release.

---

### Post by Nick_Jinn on 2010-03-12
Also, if you already have purchased this program in the past it may be legal to obtain a replacement copy from another user who also legally purchased the disk......


You can download this program for free right here.

Spinrite

[http://www.picktorrent.com/download/19/186224/spinrite-v6-3431119-retail%5Bwww.ilovetorrents.com%5D/](http://www.picktorrent.com/download/19/186224/spinrite-v6-3431119-retail%5Bwww.ilovetorrents.com%5D/)

[http://www.picktorrent.com/download/19/186224/spinrite-v6-3431119-retail%5Bwww.ilovetorrents.com%5D/](http://www.picktorrent.com/download/19/186224/spinrite-v6-3431119-retail%5Bwww.ilovetorrents.com%5D/)


Make sure you have a torrent client installed like Utorrent or transmission, and to download it legally please make sure you at one time purchased this program. In that case this is merely your replacement disk.

We all know how it is being a poor student. You cant run out and spend $90 every time you loose a disk when you can barely make rent, just to replace the same item. The cool thing is that you can replace it at no cost to the manufacturer.

---

