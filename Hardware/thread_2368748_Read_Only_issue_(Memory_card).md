---
title: "Read Only issue (Memory card)"
date: 2017-08-14
forum: Hardware
---

### Post by mahdoob on 2017-08-14
Hello i have a memory card that i wanna format but when i try to i get this error message
Error wiping device: Command-line `wipefs -a "/dev/sdb1"' exited with non-zero exit status 1: wipefs: error: /dev/sdb1: probing initialization failed: Read-only file system
 (udisks-error-quark, 0)
i searched online and found out that it's a common problem
i tried several times before giving up > [COLOR=#333333][FONT=&amp]sudo hdparm -r0 /dev/sdb[/FONT][/COLOR]

and the methode shown in this video > [https://www.youtube.com/watch?v=F4lAlb74mGs](https://www.youtube.com/watch?v=F4lAlb74mGs)
but no luck ! Please i need help and sorry for my English :P

---

### Post by TheFu on 2017-08-14
SDHC devices have a physical "lock" - check that is in the 'unlocked' position.
Your specific flash may not be completely dead, but it is probably getting picky BEFORE completely dying.  Time to move forward - new storage.

Flash storage fails after use.  All storage wears out, eventually.  Sometimes it is after a month and sometimes it is after 10 yrs, but it all wears out.  Move to a new storage device and restore everything from that backup you have.

That is what I'd do.

BTW, I have a USB3 titanium 64G device that was new last December.  It started being picky about the devices it will work in about 2 weeks ago after under 300 write cycles.  It works on 6 out of 7 devices, so there is still a use for it here, if I can't get it replaced.

---

### Post by TheFu on 2017-08-14
SDHC devices have a physical "lock" - check that is in the 'unlocked' position. Probably not it, but you never know.

Your specific flash may not be completely dead, but it is probably getting picky BEFORE completely dying.  Time to move forward - new storage.

I'd wipe it with dd first, then create a new MSDOS partition table, create a new partition and format that with either FAT32 or some other Linux friendly file system designed for flash storage that also supports POSIX file permissions.  Then I'd test across all my devices to see which like it and which don't.

Flash storage fails after use.  All storage wears out, eventually.  Sometimes it is after a month and sometimes it is after 10 yrs, but it all wears out and that happens when it isn't convenient almost always.  Move to a new storage device and restore everything from that backup you have.

That is what I'd do.

BTW, I have a USB3 titanium 64G device that was new last December.  It started being picky about the devices it will work in about 2 weeks ago after under 300 write cycles.  It works on 6 out of 7 devices, so there is still a use for it here, if I can't get it replaced. I wiped it using dd, then tried to get GPT partitioning working - it never did on the main computer I wanted to use it with, so then used MBR/MS-DOS partition tabcle and tried NTFS (didn't work) and finally FAT32.  It worked a few times, then stopped working on that main device.  Pretty frustrating, since it was working on every other system I tried it in just fine.  

In the end, I hooked up an external 64G SSD via USB3 and used that on the 1 device (MBR partitioning with NTFS as the file system) that didn't work with the other flash storage. It is working well and that SSD was under utilized before.

---

