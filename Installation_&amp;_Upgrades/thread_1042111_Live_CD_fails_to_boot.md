---
title: "Live CD fails to boot"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by thezood on 2009-01-17
I'm trying to install Ubuntu Intrepid from the live CD (actually from a separate partition with the live CD on it). It starts okay in text mode but then gets stuck in the boot process displaying this over and over:

[time] kjournald starting. Commit interval 5 seconds
[time] EXT3-fs: mounted filesystem with ordered data mode.
[time] kjournald starting. Commit interval 5 seconds
[time] EXT3-fs: mounted filesystem with writeback data mode.
[time] kjournald starting. Commit interval 5 seconds
[time] EXT3-fs: mounted filesystem with ordered data mode.
[time] kjournald starting. Commit interval 5 seconds
[time] EXT3-fs: mounted filesystem with writeback data mode.

...and so on until I get tired of it and reboot. Every other says "mounted filesystem with writeback data mode" and every other says "ordered data mode". I've googled this and there have been reports of this before but no solutions that I could find.

You should also know that I have an Asus EEE 904HD (80Gb hard disk, not SSD) running Easy Peasy (a Ubuntu 8.10 variant). The EEE has some non-standard hardware but the hard disk is supposed to be quite plain as far as I know.

I've also tried using the alternative CD but that doesn't seem to be able to handle installing from a hard drive (it doesn't allow any partitions to be mounted on the target drive).

Any suggestions would be greatly appreciated.

---

### Post by thezood on 2009-01-18
Bump.

---

### Post by thezood on 2009-01-20
Bump again. Anyone?

---

### Post by dabl on 2009-01-20
Prolly a bad CD.

Linux Live CDs use extreme compression, resulting in the necessity of achieving a perfect bit-for-bit true burn, and an optical drive that reads it with zero errors.  So here is the procedure:

- check the md5 sum on your downloaded ISO file against the md5 sum listed for it on the download site
- set the burn mode to Disk At Once (DAO) mode if it is available
- set the burn speed to 4X -- no faster!
- if you're still making coasters, try a different brand of blank media
- clean the lens on your optical drive
- don't assume that the "Check CD For Defects" function is 100% reliable
- verify suspected bad CDs on another computer/optical drive (is it the CD or the drive that is causing the problem?)
- understand that everyone makes a coaster once in awhile

;)

---

### Post by Pumalite on 2009-01-20
ADD: don't use CD-RW

---

### Post by pkg1313 on 2009-01-20
I had a similar problem, solved it by burning a new image on +R cd at low speed, was banging my head against the wall for the past 2 days!

run an MD5SUM check, [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by thezood on 2009-01-20
Thanks for trying, but please read the post thoroughly before answering. I wrote that I booted the live CD from a *partition on my hard drive*, not the CD. The reason for this is that I'm trying to install Ubuntu on my netbook that doesn't have a CD-ROM drive.

I will check the md5, though, even though it's extremely unlikely that it would cause this. 
Edit: md5 checks out.

---

### Post by boof1988 on 2009-01-20
Which method did you use to put the iso as a bootable image on a HDD partition?

I have had some success using unetbootin to put the iso on a HDD partition and make it bootable.  I didn't (in my case) work for Ubuntu 8.10 but it did work for Ubuntu 8.04.1 so that is what I am running right now.  Also... not all of the usual features of the LiveCD boot menu work properly.  (In my case) only the "Try CD without any changes to computer", the "Install" and the "Check CD integrity" work from the HDD-LiveCD created by Unetbootin.

I haven't figured out all the subtleties of doing it manually yet so I still use the *automatic* applications.

---

### Post by thezood on 2009-01-22
> **boof1988 said:**
> Which method did you use to put the iso as a bootable image on a HDD partition?

I have had some success using unetbootin to put the iso on a HDD partition and make it bootable.  I didn't (in my case) work for Ubuntu 8.10 but it did work for Ubuntu 8.04.1 so that is what I am running right now.  Also... not all of the usual features of the LiveCD boot menu work properly.  (In my case) only the "Try CD without any changes to computer", the "Install" and the "Check CD integrity" work from the HDD-LiveCD created by Unetbootin.

I haven't figured out all the subtleties of doing it manually yet so I still use the *automatic* applications.

Well, I simply extracted the contents of the ISO on an empty partition and added it to Grub, following directions I got in another thread ([http://ubuntuforums.org/showthread.php?t=1039127](http://ubuntuforums.org/showthread.php?t=1039127)). It worked for that person, and I don't see any reason as to why it wouldn't work for me. It seems straightforward enough.

It could be because of the somewhat strange hardware in my machine is not recognized (it's an Asus EEE 904HD). I'm going to buy a SD card and try booting the installation media from that instead. I think the alternative CD could work if I boot from another drive.

Now that I think of it, the live CD menu where you choose from live boot or installation doesn't show either. Very strange. I'll have to investigate some more. I'll try unetbootin too. Thanks for all your help.

---

### Post by boof1988 on 2009-01-22
> **thezood said:**
> Well, I simply extracted the contents of the ISO on an empty partition and added it to Grub, following directions I got in another thread ([http://ubuntuforums.org/showthread.php?t=1039127](http://ubuntuforums.org/showthread.php?t=1039127)). It worked for that person, and I don't see any reason as to why it wouldn't work for me. It seems straightforward enough.

I tried that method as well...  The install icon did show up on the desktop (on my machine when I booted to the installer).  But I like to have the option to check the integrity of the install media.  That's why I went with Unetbootin.

Another question...

So you have a working GrUB Bootloader on your machine?  And GrUB is what booted (or tried to boot) the installer?  So you get that repeating (...Commit interval...) message after a GrUB menu?

---

### Post by dabl on 2009-01-22
I followed post #54 on this thread and it worked perfectly (for a different Linux distro) -- it might help if the problem is the USB stick installation.

[http://kubuntuforums.net/forums/index.php?topic=3089474.45](http://kubuntuforums.net/forums/index.php?topic=3089474.45)

---

### Post by thezood on 2009-01-23
[QUOTE=boof1988] 
So you have a working GrUB Bootloader on your machine?  And GrUB is what booted (or tried to boot) the installer?  So you get that repeating (...Commit interval...) message after a GrUB menu?[/QUOTE]

I used md5sum to check the install media integrity.

Yes, I do have a grub installed. I'm using Easy Peasy now (which, for the record, is Ubuntu 8.10 tailored to the Asus EEE netbook) but I want to go back to vanilla Ubuntu.

The repeating message shows up after the grub menu but it's not the first message. The kernel seem to be booting fine up until that point. It seems as if it tries to mount a filesystem but can't decide on which journal method to mount it with. Perhaps kjournald crashes for some reason. Another possibility is that there's something wrong with my parameters to the kernel, since I'm skipping the grub on the live CD. I'll check that out too, when I have the time.

[quote=dabl]I followed post #54 on this thread and it worked perfectly (for a different Linux distro) -- it might help if the problem is the USB stick installation.[/quote]

Thanks for that link. I'll save it for when I try this again.

---

### Post by boof1988 on 2009-01-23
> **thezood said:**
> The repeating message shows up after the grub menu but it's not the first message. The kernel seem to be booting fine up until that point. It seems as if it tries to mount a filesystem but can't decide on which journal method to mount it with. Or perhaps it gets confused because the file system already is mounted. Another possibility is that there's something wrong with my parameters to the kernel, since I'm skipping the grub on the live CD. I'll check that out too, when I have the time.

You could maybe check the GrUB entry again to make sure it is correct.

If you're not able to get the current partition to boot properly, one other option you could try, is use Unetbootin to put the desktop-installer on the partition.  The only thing I don't like about Unetbootin is that it's not in the repositories, so I can't uninstall as easily as packages that are in the repositories.

---

### Post by gjoellee on 2009-01-23
> **Pumalite said:**
> ADD: don't use CD-RW
CD-RW and DVD-RW works fine, I have like 9 different Linux distros that works properly on different DVD/CD-RW, I have some on CD-R as well

---

