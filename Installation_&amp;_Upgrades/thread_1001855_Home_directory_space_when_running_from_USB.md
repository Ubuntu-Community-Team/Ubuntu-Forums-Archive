---
title: "Home directory space when running from USB"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by geokker on 2008-12-04
I've installed Xubuntu 8.10 onto a 16GB USB flash stick. It runs fine but there is only 3GB in my home directory/file system usable. The rest of the space is mounted as a '16GB Removable Volume' containing the casper loop and live cd goodies but it's all owned by root and I can't chown or chmod anything to 'ubuntu' user.

I created the installation using the 'usb-creator' app but was completely confused with the slider for 'reserved space'. I assumed if I pushed it to the max, that's what I'd be getting in the /home directory. 

As the filesystem seems to be FAT32 according to gparted, I'm wondering if this is the effect of some sort of 4GB limit.

Any ideas?

---

### Post by mikewhatever on 2008-12-04
Not quite sure what's the question here, but if you aren't happy with partitions' sizes, just resize with GPARTED. Now, one thing to bare in mind is, you can't run Gparted from usb while resizing because partitions need to be unmounted, so use the live cd or gparted installed on the main Ubuntu system. I rather doubt 4 gb limit has anything to do with partitions sizes, it was probably the confusion while allocating the space. I happen to have a WD usb hdd with 320 bg fat32 partition, so it should be possible so enlarge it.
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1                    298G  6.9G  292G   3% /media/WD

---

