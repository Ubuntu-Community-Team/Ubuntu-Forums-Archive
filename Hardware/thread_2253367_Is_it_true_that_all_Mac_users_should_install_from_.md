---
title: "Is it true that all Mac users should install from the x86 .iso?"
date: 2014-11-19
forum: Hardware
---

### Post by Quantum Anomaly on 2014-11-19
I'm reading up on how to install Ubuntu on a Mac (dual boot) and getting conflicting info on whether Mac users all need the ...i386.iso or whether the ...amd64.iso is fine to use.
You know, [these two options]("http://releases.ubuntu.com/14.04/")...
Could you guys please clear up the uncertainty?

I made a partition (from the amd64.iso) on a USB flash drive for installing but get a "No bootable device" message when I select that partition in rEFIt. Not sure if that problem is related.  :-/
Downloading the Intel x86 image now just in case.

Thanks

---

### Post by Lars Noodén on 2014-11-19
I don't know about booting from USB on Intel Macintoshes but once you install things should be fine -- for most models.  Some of the earlier models do have trouble booting AMD64, so you could find an older AMD64+mac and use that for those machines.  I have one like that but use i386 on it instead.  For newer machines, AMD64 should work ok.

---

### Post by coldraven on 2014-11-19
I don't know if this advice is still current but I found this which may have some clues. I don't have a Mac so I have never tried it.
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)

---

### Post by Quantum Anomaly on 2014-11-20
Thanks.
Lars, what would you define as "old" or "new"? (Mine is late 2009)

I'm wondering if maybe the partition is the wrong format. I left it as OS X Journaled. when I run **diskutil list** it shows up as Apple_HFS.
Does it need to be FAT? I thought imaging it would make it exactly as it needed to be, but thinking about it now the formatting may be separate from the imaging. 
I just know that FAT is a crappy format for its 4GB limit, so I try to avoid it. Did I make a mistake here?

---

### Post by Lars Noodén on 2014-11-20
I would say that 2009 is "new".  Did it boot with the regular amd64 DVD?  I always get DVD RW so I can reuse the disc.

If you are erasing the whole hard drive, let the installer choose ext4 for you.  If you want a shared partition between OS X and Ubuntu, it will have to be HFS+ but with journalling turned off.  FAT should be avoided for any system partitions.

---

### Post by Quantum Anomaly on 2014-11-21
> **Lars Noodén said:**
> Did it boot with the regular amd64 DVD?  I always get DVD RW so I can reuse the disc.
No, it did not boot. I am following the instructions on [this page]("http://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/") but I'm stuck at the step where it says "Select the USB or disc drive containing the Linux system and boot it on your Mac." Instead of booting I get the error message: "No bootable device".

> **Lars Noodén said:**
> If you are erasing the whole hard drive, let the installer choose ext4 for you.  If you want a shared partition between OS X and Ubuntu, it will have to be HFS+ but with journalling turned off.  FAT should be avoided for any system partitions.
Thanks, that explains what to choose when installing. 
Do you think I made the installer USB flash drive correctly though? I first tried the amd64.iso on a Mac OS X Journaled partition - didn't work. Then I tried the amd64.iso on a FAT partition - also didn't work.

Possibilities I can think of:
- I need to use the x86.iso instead
- I need to select a different format for the flash drive partition
- I cannot use a multi-partition flash drive, I need to make it single-partition in order to boot from it
- I need to start up while holding the 'c' key and boot from the installer DVD, bypassing rEFIt (I don't think this is the answer)

---

