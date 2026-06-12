---
title: "full partition of drive"
date: 2011-10-18
forum: Hardware
---

### Post by kaizen666 on 2011-10-18
Hi, I have a laptop and a netbook.
The laptop although over 4 years old is running the new Ubuntu 11.10 fine, and I am on my 3rd version of Ubuntu for it now.

My new netbook is another matter.  I previously installed the 10.10 netbook version of ubuntu untill recently everything froze and nothing would load, just a black screen with flashing cursor.

I now have decided to try the kubuntu 11.10 install from pen drive(USB stick), although I wanted to similarly run it alongside the windows7 not because I ever use windows these days, but because I had the other OS I managed to do a reboot from the original starting point when I bought the computer.  Although if there is another way to restore or reload from scratch, I wouldn't need windows7 anymore.

OK, so my main question is: (If I haven't lost you yet) :)

If I allow kubuntu to install on the whole drive, and take up all the partition space (overwriting the previous safe reboot point in windows) is there any way from the BIOS I can do another installation with just a USB stick (most probably the same one I am using now) or is it likely that I would just make the netbook completely jam up in the event of future problems?

---

### Post by Redblade20XX on 2011-10-18
See if your bios has any options for boot location. Usually when you start the computer and hit the bios screen you see at the bottom options for the bios.  You can make a bootable usb with either linux or windows installations, set the bios to boot from the usb location and start the installation.

Take a look at this for more info: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) ;)

-Red

---

### Post by kaizen666 on 2011-10-18
hey, thanks for the reply.

yes, it works that way, and I have already configured the boot to run from the correct USB.
What I was interested in was if the disk partition does a complete install (fully using the HDD) and then at a later time crashes, will I still have the BIOS and the option to just re-install from scratch (like the startup disc I get with a windows OS) or will the new installation also wipe the ability to install anything else.

It might sound like a really obvious answer, but I am still relatively new to all this :D

---

### Post by oldfred on 2011-10-18
I would still make a full Windows backup and make a full set of the recovery partition. Perhaps when you sell it the new user will only want Windows?

Backups ---------
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

How large is your hard drive? Most are larger now and you can make another 20GB partition with a full install.

---

### Post by kaizen666 on 2011-10-19
I have absolutely TONS of space to make partitions: 250 Gs.

It's getting a little confusing to work out which partition is which though, although I think I might be able to work it out with a little tinkering.

I will read the links, plus also try to find the one on manual partition of the disc again to see if that helps.
Thanks, not going to 'solve' the thread just yet though, as I'm still not installed with the kubuntu yet :)

---

### Post by oldfred on 2011-10-19
I prefer smaller system partitions for all systems and separate partitions for data or /home.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

---

### Post by kaizen666 on 2011-10-21
thanks for all the links there, and the extra advice :)

I think I have more than enough to do the whole thing now, and will *solve it, as I think I can take it from here and anything else would most probably need to be opened in a new thread.

once again, thank you for spending your time clarifying for me.:popcorn:

---

### Post by satanselbow on 2011-10-21
> **kaizen666 said:**
> 

It's getting a little confusing to work out which partition is which though, although I think I might be able to work it out with a little tinkering.

You can **label** your partitions to make things slightly more sensible ;)

It can also make installation(s) more manageable by pre-creating your partitions (with labels!) and then just point the installer at your existing scheme :D

---

