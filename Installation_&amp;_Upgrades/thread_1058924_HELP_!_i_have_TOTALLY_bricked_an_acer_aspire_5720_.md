---
title: "HELP ! i have TOTALLY bricked an acer aspire 5720 by deleting partitions"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by peteloaf on 2009-02-03
willy nilly deletion i might add, founded on some rather unhelpful advice..

i had a dual install of vista/ubuntu intrepid, updated from heron. using grub, not sure if it updated itself after the upgreda from ibex to heron, not sure if it's relevant, trying to include as much info as possible.

 deleted the linux partition and what i now know to be the acer support partition, and at reboot i get grub error 22.

tried to install windows (xp pro this time) but it can't find a CD.
the unopened bundle of handbooks and junk from the acer laptop didn't have an install disc, which, i assumed (yes, yes i know) it would have.

so basically, without resorting to whipping out the hdd, buying it a little usb enclosure, making it a slave and formatting it from a windows pc, then reinstalling windows from scratch what can i do?

i stil want to run ubuntu at some point, but as there's no support for my sound, or wifi (at least that's do-able by me) it's not practical for what i use this laptop for right now.
i don't need to keep any documents off the old install.
i don't have a vista disc
i don't have an enclosure. 

is there anything i can do without theser things guys?

thanks in advance
Pete

---

### Post by Mark Phelps on 2009-02-03
I'm assuming the Acer came with Vista preloaded, right?  And, that you want to get your working PC back in the state it was in before you wiped the partitions?

Regarding Vista reinstall, even if you were to be able to get hold of an OEM DVD, it would still NOT contain the ACER-provided software and drivers. So, at best, you'd get a working PC back but without the ACER stuff.  You would then be faced with tracking down any drivers that Vista doesn't automatically find and install.  You would lose all of your files and data in the process.

Regarding drive recovery, if you can pull the hard drive and have access to another Windows PC, there are a number of commercial products that you can use to try to restore the original partitions and files. Paragon and Acronis both sell products that will do this.  Runtime software also sells sone RecoveryMyFiles and GetDataBack products that can do this.  I recently recovered an entire NTFS partition with their GetDataBack product.

If neither of these work, since you removed the ACER recovery partition, you have no choice other than to send the PC to ACER and pay them to recover it.

---

### Post by dstew on 2009-02-03
If you have not done anything to the hard disk, but just messed up the partition table (which is what you do when you delete partitions) you might be able to recover your partitions using [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"). Check it out, it has a good reputation.

---

### Post by andysuth on 2009-02-03
Must be that time of week.

I too have just deleted a partition table (Linux mint5/WinXPSP3).

I can put the software back on it, but since I was just about to do the January back up I'll be losing a whole month of work (and probably my job with it).


Funny thing was I was looking at deletion for my college who need to factory reset his identical laptop. I was using Partition Editor and it came up with rename partition, which I thought I had not edited, and exited and then made sure all the WinXP data was still there and the Ubuntu stuff was still there.

I'm cakking oneself here. I've looked at the link by dstew, but can't find ubuntu variant to put on memory stick and use in conjunction with a live Mint CD I have.

I'm in Fedora at moment and I'm trying to use a live fedora CD with the RPM version of TestDisk.

Any help would be greatly appreciated as I can't afford to faff up (again!).

Thanks for this thread guys.

I've found a rescue Remix of Ubuntu for this, I've not tried it yet, but I'm downloading the ISO from:
[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

30min download - so don't know yet, if anyone has any other tips, please post!!!!!

I'll edit if this ISO works or not for my problem.

-Andy

---

### Post by icanfly0307 on 2009-02-03
Can't you just reinstall Ubuntu entirely from the CD that you burned? You said that you don't care about any docs on your hdd, so there should be no problem. 

PS. If you have an old XP, 2000 or any other Windows CD, post back and I'll tell you how to boot into Vista without wiping out your hard drive.

---

### Post by dstew on 2009-02-03
Andysuth wrote> I've looked at the link by dstew, but can't find ubuntu variant to put on memory stick and use in conjunction with a live Mint CD I have.The testdisk program is part of the [GParted Live CD]("http://gparted.sourceforge.net/livecd.php"). You can create a bootable version on a USB stick.

---

### Post by andysuth on 2009-02-03
> **dstew said:**
> Andysuth wroteThe testdisk program is part of the [GParted Live CD]("http://gparted.sourceforge.net/livecd.php"). You can create a bootable version on a USB stick.

Dstew,

Thanks for the GParted Tip, That's now become my favourite LiveCD.

Very scarey actually doing the re-tabling of the partition.

Thank you everyone for the tips, I'd highly recommend the Gparted live CD for anyone who accidentally deletes their partition with PartitionEdit.

Thanks.

-AS

---

### Post by peteloaf on 2009-02-03
> **Mark Phelps said:**
> I'm assuming the Acer came with Vista preloaded, right?  And, that you want to get your working PC back in the state it was in before you wiped the partitions?

Regarding Vista reinstall, even if you were to be able to get hold of an OEM DVD, it would still NOT contain the ACER-provided software and drivers. So, at best, you'd get a working PC back but without the ACER stuff.  You would then be faced with tracking down any drivers that Vista doesn't automatically find and install.  You would lose all of your files and data in the process.

Regarding drive recovery, if you can pull the hard drive and have access to another Windows PC, there are a number of commercial products that you can use to try to restore the original partitions and files. Paragon and Acronis both sell products that will do this.  Runtime software also sells sone RecoveryMyFiles and GetDataBack products that can do this.  I recently recovered an entire NTFS partition with their GetDataBack product.

If neither of these work, since you removed the ACER recovery partition, you have no choice other than to send the PC to ACER and pay them to recover it.

basically apart from the stuff to manage the power consumption etc the acer supplied software (and vista home itself) is a steaming pile of dung. i can get it all driver-wise from acer's website, so no worry there. and i don't need a damn thing off the drive LUCKILY! thanks for the tips though.

> **dstew said:**
> If you have not done anything to the hard disk, but just messed up the partition table (which is what you do when you delete partitions) you might be able to recover your partitions using [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"). Check it out, it has a good reputation.

will have a look.. i did whatevr windoze disk manager does when it delets a partition..

> **icanfly0307 said:**
> Can't you just reinstall Ubuntu entirely from the CD that you burned? You said that you don't care about any docs on your hdd, so there should be no problem. 

PS. If you have an old XP, 2000 or any other Windows CD, post back and I'll tell you how to boot into Vista without wiping out your hard drive.

now the last part of this sounds promising. i have an install of xp pro i basically want to upgrade to, but when i put it in, it doesn't even recognise that there is a hdd in the machine! madness, as the bios sees it.

---

### Post by andysuth on 2009-02-04
> **peteloaf said:**
> 
now the last part of this sounds promising. i have an install of xp pro i basically want to upgrade to, but when i put it in, it doesn't even recognise that there is a hdd in the machine! madness, as the bios sees it.

Pete, 

If you're getting the grub error 22 like I did, the boot sector is still there on your hard drive as I believe grub is stored on your HDD Download the GParted Live CD and type testdisk at the console.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

(get the ISO and burn to CD).

My GParted had Partition Editor open when it booted, and showed 95gb unallocated space on a HDD. Testdisk will search for missing partitions and then save them and reboot and your HDD will be back and a normal reboot will work.

-Andy

---

### Post by peteloaf on 2009-02-04
> **andysuth said:**
> Pete, 

If you're getting the grub error 22 like I did, the boot sector is still there on your hard drive as I believe grub is stored on your HDD Download the GParted Live CD and type testdisk at the console.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

(get the ISO and burn to CD).

My GParted had Partition Editor open when it booted, and showed 95gb unallocated space on a HDD. Testdisk will search for missing partitions and then save them and reboot and your HDD will be back and a normal reboot will work.

-Andy



alas, no dice.
i'm heading out to buy a usb enclosure.

thanks ubuntu peeps for all the help and support, i guess i will know better in future right? here's hoping the code monkeys can get the wifi and sound workifng on my lappy so i can finally ditch that massive steaming pile of microsoft dung.

---

### Post by peteloaf on 2009-02-04
thank god my assumption that sticking it in an enclosure and formatting it from osx has worked! currently wiping it back ot a blank, ms-dos fat format, HOPEFULLY once that concludes it will be recognised by windows xp pro's install disc and this time might actually work!

again, thanks for all the helpful suggestions people, alas i had fudged it too far for them to work, but the intent was there and for that i thank you.

---

### Post by icanfly0307 on 2009-02-04
Glad to know you got it to work! :)

---

### Post by makins on 2010-12-06
Might already have been said but for anyone else that does this then (I think this is what I did) you need to borrow, if you don't already own, a Vista disk and put it in the disk drive. Boot up the disk and enter in the necessary details (Language, keyboard etc)until you get to a page where repair is an option. Click on it and then click on the vista install. Click next and then in the System Recovery Options dialog box click command prompt. Type Bootrec.exe /FixMbr, and then press enter. Once you've done that you can reboot your pc and vista should boot automatically.

---

