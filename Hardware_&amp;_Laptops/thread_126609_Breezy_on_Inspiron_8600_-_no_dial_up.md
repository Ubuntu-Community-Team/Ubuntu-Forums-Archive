---
title: "Breezy on Inspiron 8600 - no dial up"
date: 2006-02-06
forum: Hardware &amp; Laptops
---

### Post by Combi on 2006-02-06
Trying to run breezy on the 8600 for the first time, but unable to access the on-board modem for dial-up.  Modem unit is a Broadcom, carrying BCM4309 chip set (as shipped by Dell).  Have tried the standard ttyS options, but no luck. 
 
Microschmuck XP indicates the modem sits on Com 3, but plog shows three attempts and gives up without finding the modem.

I assume I need a driver, but does one exist?

Have searched heaps of Linux forums (including Debian) - no joy.
Broadcom's site is useless, with no tech detail at all on the 4309.
No joy on the Dell site either.
Had similar problems with Damnsmall too.  

Am I the only one trying 56k dial-up through Broadcom chips?

---

### Post by jasmuz on 2006-02-07
Im sorry to say, but laptop modems are "Winmodems", as they really arent modems at all. but joy, there is some solution to such, read [http://www.linmodems.org]("http://www.linmodems.org") for more help

---

### Post by Combi on 2006-02-08
Thanks Jasmuz.  Now I'm really confused.  I'd checked the linmodems site and looked inside the hardware (big chip visible 4309kfb tg0410 p30) and convinced myself that it was a hard modem.  So now I'm trying to get scanModem off my ntfs and on to my linux partition.  Trouble is I can't get the partition to mount.  Perhaps my installation was not clean, so a reinstall is the next move.  Makes me hanker after the good old days of XENIX nearly 20 years ago. I'd swear there were less conflicts and more up-time.

---

### Post by Bartender on 2006-02-09
Combi -
You mention that you can't get to your ntfs partition...that's how it's supposed to be.  Linux messes up ntfs.  Did you just build your dual-boot recently?  Do a quick search for any of aysiu's posts and follow his link for dual-booting to that "hermanzone" site.  Directions there for dual-booting and creating a FAT32 partition where the two OS'es can share data.  Worked great for me.
Windows will automatically recognize the FAT32 partition, but you'll probly have to edit your fstab to get Ubuntu working with what it sees as the "vfat" partition.  If you go to "Administration" in the top panel, then go to "Disks" (or is it Disk Management?) you can scroll thru the partitions that Linux sees.  If it sees vfat but you can't click on the little button to enable it you'll have to do the fstab thing.  There are directions all over the place for what to type into fstab.  If I could stumble thru it you can.

---

### Post by Combi on 2006-02-11
Thanks for your interest Bartender.  I wrestled with fdisk, fstab and remounted along the lines you suggested.  Now I can see (and copy from) the ntfs partition.

Which means I copied over scanModem ...

Which tells me, as JasMus suggested, that I have a soft modem.  Apparently the Inspiron 8600 is carrying an Intel 8086:24c6 14e4:4d64.

Searching other forums I found "Jaques" recent advice regarding the use of SLMODEMD driver.  see [http://linmodems.technion.ac.il/archive-sixth/msg00330.html](http://linmodems.technion.ac.il/archive-sixth/msg00330.html)

Using his recipe and the SLMODEMD text I got as far as sending to the port, but then repeatedly received "No carrier Try again".  By this time I was really tired and frustrated.  So, until I can find another post that gives a more definitive instruction list, I'm stuck with Microsmuck.... aaaargh

Buying an external modem is a possibility, but it's yet more gear to carry around, and yet another bill to pay.

---

