---
title: "Recovering data from a notebook HDD"
date: 2010-05-24
forum: Hardware
---

### Post by yomnym on 2010-05-24
Hello, i've been using ubuntu for a bit now but im no expert when it comes to terminal commands and things like this, i need some help trying to recover some data from a friends notebook HDD.  I'm using my pc and luckilly the notebook HDD has the same sata data and power cable, im running a SSD on my pc so i have bios setup for AHCI.  What i did was unplug my SSD and connect the notebook's HDD powered up and ran the Live Ubuntu CD.. it all went ok till i got to the desktop and tried to mount the HDD, it couldn't.  Any ideas on how to do this.  Im basically trying to get into this HDD and get files out, like pictures and some documents.  This is a friend from work that has basically most of her children's life photography in there and i just wanted to try and help.  Any help would be very very appreciate.  Oh the other thing i did was plug in the HDD from the notebook and just try and boot up regularly, using its own OS but i got the "bootmgr is missing" error, i tried to repair it using the Vista cd but the OS wouldn't show up.  Thanks

---

### Post by viralmeme on 2010-05-24
> **yomnym said:**
>  it all went ok till i got to the desktop and tried to mount the HDD, it couldn't

What error msgs did you get when tryign to mound the HD. Boot from the Live CD and fire up Qparted and see if it can identify the drive.

---

### Post by dino99 on 2010-05-24
usefull tools:

[http://partedmagic.com/](http://partedmagic.com/)
[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

---

### Post by yomnym on 2010-05-24
ymitchell the error said something like "cannot mount because windows didn't shut down properly, try and force mount..." I'll get the exact message and post it.. 
Dino- I'll try and give that a shot, but parted magic, isn't that for rezising or editing partitions?  regardless i'll get it on a liveUSB to run it and see what i could work with that, but what i really need is to mount that HDD and try and save pics and data from it.

---

### Post by movieman on 2010-05-24
> **yomnym said:**
> ymitchell the error said something like "cannot mount because windows didn't shut down properly, try and force mount..."

You may still be able to mount it read-only; which you probably want to be doing anyway. I was running off a live CD yesterday and mount wouldn't mount the drive read-write because I'd hibernated Windows but it would mount it read-only.

---

### Post by aysiu on 2010-05-24
This should help you:
[[SOLVED] Cannot mount drive - windows not shut down safely](http://ubuntuforums.org/showthread.php?p=4309779#post4309779)

I know terminal commands can be a bit confusing, so if you need us to walk you through step by step or explain any particular part of a command, don't hesitate to ask.

---

### Post by yomnym on 2010-05-24
Guys i really appreciate your help alot, its for a good cause and it'll safe hopefully a great deal of memories for a friend.  I'll try these things when i get home.. thanks again for your help!  I'll post back.

---

### Post by yomnym on 2010-05-24
I tried the things about but still had no luck.. i couldn't even force mount it, does this mean the HDD is really screwed up?
Its basically saying " failed to read vcn 0x0, failed to mount dev/sda1..." "NTFS is either inconsistent or hardware fault" 
I think something may have been messed up when the laptop was dropped.

---

### Post by movieman on 2010-05-24
Personally I would use dd to copy the disk into a file on my Linux disk, and then see if there's some NTFS repair programs which can fix it to the point where it can be mounted; you could try ntfsfix, for example, but that won't fix serious corruption.

Working on a copy of the disk is much safer than working on the original disk, as you don't have to change anything on the original disk and risk trashing it.

---

### Post by tgalati4 on 2010-05-25
Somehow "dropped" was left out of the original post.  If the drive suffered a crash and physical damage to the heads, then recovery will be difficult.  Get a second drive of similar size or larger (probably a USB external drive) then use your laptop to try to image the drive (using the dd command) to the new USB external drive.  If you are able to do that, then you can use photorec to recover the files:

sudo apt-get install testdisk
man photorec

---

### Post by yomnym on 2010-05-25
I'll try that, i'll see if i could get the image on a seperate storage media and try and work with that.  I really appreciate all your help guys!

---

