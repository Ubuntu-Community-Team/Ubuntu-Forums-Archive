---
title: "How to install with multiple partitions on USB key?"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by Fastfwd on 2009-01-19
What I would like is to use my work laptop from home without the currently installed OS and all its restrictions. Basically I want to boot from usb-ubuntu but I also want to keep a FAT32 partition on my usb key for all my files that I use in both windows and linux.

I deally I would have a 2GB partition for ubuntu, don't care about which filesystem. And 6GB for FAT32 that is accessible by both windows and linux.

As of yet I have been unable to do that. I can create a live-usb but this does not let me have a 2nd partition and any files I put on the FAT32 endup as read-only in /cdrom

Any ideas?

---

### Post by Fastfwd on 2009-01-19
I seem to have made some progress but definitely not there yet.

I booted from the live-cd and did a manual partitioning scheme to create a 5.5GB FAT23 partition first for windows and then wanted to use the remaining 2.xGB for ubuntu as ext3.

I received a warning about not having any swap partition but he installer started anyway. About 75% in it told me I was out of space for files. I assume this means my ext3 partition was already full and has nothing to do with the swap space.

Do I really need to use more than 2GB to install a basic ubuntu 8.10?
Will I be able to run simple software with 1GB of ram and no swap. vlc, firefox, ssh?

---

### Post by Archmage on 2009-01-19
Yes, I think that 2 GB is pretty tight. I assume that Ubuntu would need more.

When you are using the usb-creator for a live CD and active persistante space. Can't Windows read this?

---

### Post by Fastfwd on 2009-01-19
> **Archmage said:**
> Yes, I think that 2 GB is pretty tight. I assume that Ubuntu would need more.

When you are using the usb-creator for a live CD and active persistante space. Can't Windows read this?

Yes windows can read the FAT32 on the live-usb but linux himself can only read files that are there and not modify them because they end up omn the /cdrom partititon.

---

### Post by Fastfwd on 2009-01-19
I finally got it to work.

1- Use lexar bootit or other tool to flip the bit to mark usb key as non-removable drive.
2- Boot from ubuntu 8.10 live CD
3- Insert usb key
4- Choose install from menu
5- manually create partitions(first is primary fat32, second in ext3 mounted as "/") I was successful with 4GB ext3 but I think 3GB would have worked too from the available space I have now.
6- At confirm sreen go into advanced and tell grub to install on sdb(or whatever else is your usb key)

That's it. I now have a USB key that has a 4GB fat32 partition that I can read and write from windows. And a 4GB partition that I can boot into with a persistent install of ubuntu 8.10.

Too bad that I needed more space. I guess it's time to buy a key that is bigger than 8GB  :)

---

### Post by underwhelmed on 2009-01-19
Looks like you've done well!
Now what I've done is got a good persistent install on an 8gbusb  disk, but haven't partitioned it so windows can't see it.  Can anyone tell me if i can retro partition it (say 4gb) as fat32 without losing data and settings on the original half??
similarly can i make an installed usb into a live disk retrospectively?
I'll try the above moves with another usb, but would really like to keep the original, but with the above mods, without b*ggering it all up.
any ideas? cheers g

---

