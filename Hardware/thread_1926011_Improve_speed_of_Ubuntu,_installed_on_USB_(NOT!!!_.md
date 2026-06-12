---
title: "Improve speed of Ubuntu, installed on USB (NOT!!! a live USB )"
date: 2012-02-15
forum: Hardware
---

### Post by deckoff on 2012-02-15
**The setup:**
Thinkpad x40 without harddisk, 1GB of RAM. The hard-disks for these models are very slow, rare and expensive. This is why I installed
Ubuntu 11.10 onto the USB. The system will be used for net - FF, and some office docs editing. If possible, I might setup a second PC, used for XBMC 
I have tried live Ubuntu USBs with the same PC and USB, and the setup is OK. I am limited to 4 GBs, though. This is why I chose to perform normal install.
**The problems:**
The system feels slow, and freezes every other second. I have no swap, only one root partition.
**What I have tried:**
```

sudo aptitude install preload

```

```

Use memory instead of disk

Add these lines to /etc/sysctl.conf, and reboot.

vm.swappiness = 0
vm.dirty_background_ratio = 20
vm.dirty_expire_centisecs = 0
vm.dirty_ratio = 80
vm.dirty_writeback_centisecs = 0

```


*Mount /tmp onto ramdisk*
```


mkdir /dev/shm/tmp
chmod 1777 /dev/shm/tmp
mount --bind /dev/shm/tmp /tmp

```
Still, the system is slow to the point of being unusable. Are there any other tweaks that can be done. I read that some parts of the system might be mounted into RAM, and that would be beneficial, but which parts and how to do that. I also read that compressing parts of the system might help, I dont know how to do that , too

---

### Post by ahallubuntu on 2012-02-15
Any reason you can't upgrade to an 8GB flash drive?  They are regularly available on sale for under $10 USD now.  I have a couple of 8GB Sandisk Cruisers and they are pretty fast.

I have installed various versions of Ubuntu on 8GB flash drives (full installs, not "live").  They can be slow.  Some flash drives are slower than others.  But, 8GB gives you enough space to have at least a small swap space and and some breathing room.  Remember, any OS needs some "scratch space" to work effectively.  If your hard drive is 95% full, you should NOT thing, "I have 5% left!"  At 95% the OS will have to slow down trying to find free space to store larger files, etc.  Better to have at least a little free space.

One tip is to install using the ext2 filesystem (non-journaling) which I haven't done.   Apparently the journaling puts extra constraints on the filesystem and causes increased accesses.  Remember, USB flash drives are NOT SSDs with load balancing; flash drives WILL wear out eventually after so many writes to the same sector.  SSDs attempt to balance the load to avoid early failure because of this.  I figure an 8GB USB flash drive that costs under $10 is disposable, anyway.

---

### Post by deckoff on 2012-02-15
I was not clear enough, probably :) I use 16GB USB flash drives. This is why I want a persistent install in first place. Live install can add up to 4GB of free space, this is what I mean. 
I will try ext2 file system, meanwhile I will try these scripts found here :
[http://www.systemateka.com/usbboot.html]("http://www.systemateka.com/usbboot.html")

---

