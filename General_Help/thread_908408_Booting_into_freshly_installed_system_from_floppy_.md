---
title: "Booting into freshly installed system from floppy disk just will not work"
date: 2008-09-02
forum: General Help
---

### Post by duckdown on 2008-09-02
Greetings, everyone!

I am a novice user who has run into an issue here.

I boot the 8.04 desktop CD, and choose to install the system to the partitions of my choice.

Everything goes OK, and the system is done installing, but I do not want to modify my MBR and install GRUB to it; mainly because Ubuntu is failing to recognize my /dev/sda and /dev/sdb as one single RAID0 partition; instead its seeing it as two individual drives.  Not a big deal, but I don't want to play around with taking the chance of windows not being able to boot.

So I installed to my lone unraided /dev/sdc instead.  But here is where things go haywire.

When it asks where to install the MBR, I inputted manually /dev/fd0 instead of a /dev/sdX device, because according to some older guides this is a perfectly good way of using a boot disk to get into your linux.  So it finishes installing the system and I guess makes the disk, and I choose to reboot.

On system reboot, with my "boot disk" in the floppy drive, I see the "Booting from floppy" appear on my screen and it tries the disk, and then after that all I see is "GRUB" appear on my screen, but it locks up after that.

It just shows GRUB and NOTHING else.  I can't even alt+ctrl+del or anything, I have to hard reset the computer, and remove the floppy disk.

Can anyone tell me what the heck is going on?  It is obviously doing something wrong or not writing to the floppy disk properly but I cannot find a solution or any help...  So I am here begging for assistance :)

Any help would be GREATLY appreciated, because I really do not want to play around with installing GRUB to my MBR because it can't even see my windows RAID0 device, only sees the raw /dev/sda and /dev/sdb instead of one solid device.

Thanks again!  Sorry if this is confusing.

Cheers

---

### Post by duckdown on 2008-09-02
Bump for help please :(

Another question, maybe this will be easier.

Can I boot into my freshly installed system through the BOOT CD?  Maybe if I press F6 for "Additional Parameters" is there something I can enter there to make it boot from hard disk instead?

Basically I am looking for a way to boot into my Ubuntu via either floppy disk, or via CD.

Thanks!

---

