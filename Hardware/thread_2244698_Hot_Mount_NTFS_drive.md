---
title: "Hot Mount NTFS drive"
date: 2014-09-18
forum: Hardware
---

### Post by Lappert on 2014-09-18
I have a relatively new build with a nice case that has a Hot Swap dock on the top. Usually I don't put a drive there, but I'm trying to copy an entire drive (NTFS) from an old windows box to a larger drive (ext4) on this kubuntu box. The dock is connected to the mobo by SATA, not USB. 

The drive mounts physically fine, it's in and humming away.

But how to mount it? I've read many posts about gparted and fstab, but that sort of negates the idea of hot-swapping. If I absolutely must reboot, is there a simpler way to do this?

Thank you.

---

### Post by ajgreeny on 2014-09-18
You should not need to do anything except double click on the icon for the old drive to mount it and be able to copy files from it.  I don't see why you would need gparted, but with the correct option (noauto) I think you could add a line to fstab to mount it automatically at boot.
```
UUID=66E53AEC54455DB2 /media/storage/    ntfs-3g        noauto,user,rw 0 0
```
You can get the UUID with```
sudo blkid -c /dev/null
```

---

### Post by Lappert on 2014-09-18
Thanks for your reply.

I don't know what you mean by "old drive" as this drive is in addition to the existing drives; it does not replace anything. There is no icon. Never was.

Before I had drives A, B, C, D, E and F. A & B are the OS (raid 1 SSD). C&D are primary storage (also raid 1). E and F are secondary storage, which I keep online.

Add to those there is Drive G, the CD/DVD (sata) and Drive H is the Hot Swap Dock, which up until now has been empty.

So now I want to temporarily add Drive H in the Hot Swap dock (I normally keep drive H off-line and it essentially is a mirror of E. Both E and H are NTFS having previously existing in a Vista box.

I will look at your solution ... but ... I did some additional research afer I first posted. There's a thing called AHCI that extends SATA. My bios supports it (ASUS P8Z77-V), so I made sure it was enabled (it was) and the temp drive in the Hot Swap dock had the BIOS Hot Swap enabled (I made sure it was). For some reason the BIOS reports only 6 drives of the 8, but I don't know if that's an issue yet with this problem.

So I rebooted with AHCI/Hot Swap enabled. I normally use Krusader as a File Manager, and that did not recognize Drive H (at least not initially).

However, I tried Dolphin, and sure enough, Drive H was there, although it seemed not to be mounted in the file system. It's called Media H - but not accessible from root or below, just as a device sitting out there apart from all the other drives.

Just to backtrack, drives A & B (raid) are mounted at root
drives C & D (raid) are mounted at /opt
drives E & F are mounted at /media/drive_SDE and /media/drive SDF

Looking around I finally found Drive H in the filesystem, at /media/username/Media H. Even Krusader has found it.

So I don't know how all that works with your solution, but it does seem to work. I did try blkid -c /dev/null, but that only reported the DVD drive, not the UUID of other drives.

---

### Post by ajgreeny on 2014-09-18
Sorry but I know nothing useful about raid setups and fear that may be the reason for your difficulty, but to clarify, by "old disk" I mean the disk from your "old windows box" as you described it; your words, not mine.

---

### Post by Lappert on 2014-09-18
Thanks for your reply. RAID has nothing to do with the issue. It does seem that AHCI has solved the problem.

---

