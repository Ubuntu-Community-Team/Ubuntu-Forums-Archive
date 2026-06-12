---
title: "Installation Troubles"
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by zzzBrett on 2009-07-17
I am attempting to install 9.04 on a new desktop pc (custom built).  The motherboard and processor are both new, and the hard drive was taken out of a computer in which it was functioning fine.

I go through the install fine, setting manual partitions of 70 gb / 70 gb / 100 gb / 5 gb for root, home, unused, and swap (respectively).

When the install finishes and i reboot, I can't get it to boot at all.  I get the error 'invalid boot disk' .. 'insert system disk and press enter'.

The BIOS boot configuration is set to the correct HDD, and just to verify, I unplugged all other HDDs / Disc drives.

I am not totally new with ubuntu and have done 5+ install, but I very well could be missing something simple.

Any recommendations?

Thanks!

---

### Post by merlinus on 2009-07-17
Did you install grub, and if so, to where?  But it would seem you are not even getting that far...

You might check the hdd connectors, etc.

Also, if you can run from the live cd, open a terminal and post results of

```
sudo fdisk -l
```

---

### Post by zzzBrett on 2009-07-17
> **merlinus said:**
> Did you install grub, and if so, to where?

All other of the installs I've done installed grub automatically (i'm assuming to /boot).  I let the installer take care of that.  There was no separate partition for /boot.

All physical connections are in place.

---

### Post by oldfred on 2009-07-17
When you unplugged the other drives you probably renumbered the drives and partitions. Boot with live CD and Check sudo fdisk - l for numbers where root is and then check your /boot/grub/menu.lst for numbers. Grub numbers count from zero where linux counts from one, so sda1 will be (HD0,0) in GRUB.

---

### Post by zzzBrett on 2009-07-17
> **oldfred said:**
> When you unplugged the other drives you probably renumbered the drives and partitions. Boot with live CD and Check sudo fdisk - l for numbers where root is and then check your /boot/grub/menu.lst for numbers. Grub numbers count from zero where linux counts from one, so sda1 will be (HD0,0) in GRUB.

I unplugged the drive in an attempt to get it to boot.  It was after I experienced it not working.  But I will try booting into the Live cd and see if that is the problem.

Thanks for the suggestion.

---

### Post by zzzBrett on 2009-07-17
I got it working.. I'm not entirely sure what was wrong, but I ended up using the alternate disc and letting the installer automatically configure the partitions for me ... although i don't know what I could have been doing wrong.  Thanks for the suggestions.

---

