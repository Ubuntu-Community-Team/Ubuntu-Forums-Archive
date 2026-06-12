---
title: "Making a backup with PartImage and Ext4"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by Bao2 on 2009-02-10
I use Partimage (SystemRescueCD) to backup ubuntu.
I am trying Jaunty alpha4 and I installed using ext4 instead ext3. Now I find PartImage don't works when I try make a backup of my Jaunty alpha4. 

Is there some way of making a backup of Linux with a program that understands ext4? Am I the only one in the world making backups, Why I can't find this problem in Google?

---

### Post by PeterLohmann on 2009-02-22
I was wondering the same thing.
Does anyone know a tool that understands ext4 and can backup it in a similar way like partimage or better even dump do for ext2/ext3? Or does anybody know whether (and when) these two tools will support ext4?

Thanks
Peter

---

### Post by bertux on 2009-03-01
Hello,
You can use PartClone which official website is at [http://partclone.nchc.org.tw/](http://partclone.nchc.org.tw/)
It says: "Partclone provides utilities to back up and restore used-blocks of a partition and it is designed for higher compatibility of the file system by using existing library, e.g. e2fslibs is used to read and write the ext4 partition."
And since the simplest method to use it is to boot on a live CD which already includes it, you can try Clonezilla live CD available at [http://www.clonezilla.org/](http://www.clonezilla.org/)
The "experimental" version is already based on Ubuntu Jaunty Alpha 5, the precise download link is [http://downloads.sourceforge.net/clonezilla/clonezilla-live-20090226-jaunty.iso](http://downloads.sourceforge.net/clonezilla/clonezilla-live-20090226-jaunty.iso)
Hoping it will help you.
I'm trying to backup my Arch Linux using it.
Have a nice day !

---

### Post by Bao2 on 2009-03-22
Many thanks bertux, I will try your links, that Clonezilla seems wonderful.

---

### Post by kumoshk on 2009-04-07
So, it's been a few months, now. How has Partclone worked for you all?

I'm wanting to use it to make a bootable ISO image of a 32-bit Ext4 Jaunty installation that I have on a USB flash drive (I just use it so I can have a 32-bit OS for PowerDVD since my main hard drive has a 64-bit installation and PowerDVD is 32-bit only), and then put it on a partition of an external hard drive I have on order.

I'm borrowing the flash drive&#8212;I figure it might be faster to image it over than to reinstall everything and do the updates again. Anyway, is there something I should know?

---

### Post by cornflake000 on 2009-04-22
Yeah... I used clonezilla.  It worked but not nearly as well as partimage.  These are full partition or hard drive images not iso. It will compress but it won't make a nice iso that only stores the used data in which case it's H***ish slow.  If you have a 100gb partition it gives you a full 100gb backup even if you only have 20kb of data.  It took a 35 minutes to copy a 58gb ext4 partition that had 6gb of data using the fastest non-compressed method.  It used to take about 3 minutes in partimage for the same partition when it was ext3.  I have a fairly fast box.

---

### Post by johnhenry on 2009-04-26
fsarchiver works well with ext4. It is on the SystemRescueCD, for example, too - and probably other utility disks. The -h option shows a good selection of common syntaxes. It seems just as fast as partimage, and does a good compression. For example, it compressed a 20G partition of mine to 1.4G, and did a good, quite fast restore. Its only disadvantage compared to partimage is that it is a commandline program, and lacks the progress display of partimage. But it works very effectively, in my relatively short test time.

---

### Post by Pumpino on 2009-04-26
Interesting that you mentioned fsarchiver. I emailed one of the listed developers of PartImage yesterday to ask if they would be supporting ext4 in future PartImage releases. He explained that he no longer works on PartImage himself, but has been working on his new project, fsarchiver, which supports ext4. The downside is that it's only a command line tool. However, he's planning to give it a GUI once it's more refined.

I'm a little reluctant to switch to ext4 for minor speed improvements when it means no longer being able to use PartImage, as I love PartImage. However, if fsarchiver turns out to be easy to use, then I'm prepared to make the switch.

EDIT: The syntax is this quickstart guide looks pretty straight forward. I'm prepared to give it a go. [http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)

---

