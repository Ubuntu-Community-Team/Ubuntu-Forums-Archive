---
title: "mount: special device /dev/* does not exist."
date: 2009-03-02
forum: Hardware
---

### Post by rootless on 2009-03-02
I just got a new hard drive for my Thinkpad R40. The last one kicked the bucket right after I installed Ubuntu from a live CD. I just got a new CD/DVD today. I popped it in, and booted up. The drive spun, the light came on, and the IBM splash screen came up. I held my breath until it passed.

Ubuntu seemed to have booted successfully... but when I pop in a CD, the drive spins, yet nothing happens. When I try to mount the drive, it throws the error "mount: special device /dev/scd0 does not exist." The light on the CD drive is flashing. I checked /etc/fstab. It lists a device called /dev/sdc0, but that device is no longer in /dev/. I assume it was my old CD drive. 

I did a sudo lshw. no CD/DVD drive was listed amongst my hardware. My guess is that something needs to be configured for Ubuntu to detect this new drive, but I'm not sure how to proceed.

My problem seems very similar to [http://ubuntuforums.org/archive/index.php/t-839536.html](http://ubuntuforums.org/archive/index.php/t-839536.html) but it is unclear exactly how he managed to fix his problem.

Any help anyone can give me on this will be GREATLY appreciated. I hate to see my poor Ubuntu so sickly. While following a guide at [http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/) a while ago, a chmod command screwed everything up, and so I need to get my CD/DVD drive working so that I can do a reinstall.

---

### Post by rootless on 2009-03-03
Nobody has any ideas? At least some ideas for a workaround? Any way to wipe and reinstall ubuntu without a functional CD drive?

---

### Post by Perryg on 2009-03-03
> **rootless said:**
> Nobody has any ideas? At least some ideas for a workaround? Any way to wipe and reinstall ubuntu without a functional CD drive?

Have you tried to boot from a live cd to see if the hardware is detected properly after your install?

---

### Post by rootless on 2009-03-04
I've tried with a few different LiveCDs. The drive spins on startup, but after that, it boots as if a CD isn't mounted.

---

### Post by Perryg on 2009-03-04
> **rootless said:**
> I've tried with a few different LiveCDs. The drive spins on startup, but after that, it boots as if a CD isn't mounted.

Have you gone into the BIOS settings and tell it to boot from the CD first and then the HDD second?

---

### Post by rootless on 2009-03-04
Yes.

---

### Post by Perryg on 2009-03-05
> **rootless said:**
> Yes.

The only other thing I can add without actually seeing this is to check to be sure that the drive you installed is pinned correctly.  I do not know for sure because I am not familiar with your exact pc, but if it was not pinned correctly it is possible that it would cause this very problem.  Master/Slave kind of thing.

---

### Post by rootless on 2009-03-05
I doubt it's pinned incorrectly: thinkpads only have a place for 1 cd drive. They are totally modular. The way you insert the drive is pretty idiot proof... unless I'm an idiot. Maybe I'll check. haha.

Thanks for your help.

---

### Post by Perryg on 2009-03-05
> **rootless said:**
> I doubt it's pinned incorrectly: thinkpads only have a place for 1 cd drive. They are totally modular. The way you insert the drive is pretty idiot proof... unless I'm an idiot. Maybe I'll check. haha.

Thanks for your help.

I understand, but there is the possibility that they share the same IDE chain.  It has to be something that is common to your replacement of the drive if it is not defective

---

### Post by rootless on 2009-03-06
Well, the drive looks to be put in correctly to me, and the bios is set right.

---

### Post by rootless on 2009-03-07
My theory is that my last drive was a CD. Maybe Ubuntu had the drivers for that. This latest drive that I installed was a CD/DVD. Maybe I don't have the proper drivers? How do I install/upgrade drivers in Ubuntu?

---

### Post by Perryg on 2009-03-07
> **rootless said:**
> My theory is that my last drive was a CD. Maybe Ubuntu had the drivers for that. This latest drive that I installed was a CD/DVD. Maybe I don't have the proper drivers? How do I install/upgrade drivers in Ubuntu?

Well now there is the issue.  By default I would think Ubuntu would see that drive.  You might try commenting out the line that has the old drive listed in the fstab and do a complete power cycle of the laptop to see if it is recognized there.  The CD part of it should be anyway.  

In the meantime I did some snooping on the lenova site and they referenced the Grub loader as the culpret and that you should use lilo to do the loading.  Some of the people stated that it did in fact fix their problem. 

By I have to tell you that it not loading the live cd gives me more concern than anything else. To me this would indicate either a BIOS issue or a defective drive, if cabling and all have been ruled out.

---

### Post by rootless on 2009-03-07
The line that I commented out is in bold. Thank you so much for your help Perry. I'm going to power cycle, and see what happens. Any ideas on how to fix the BIOS? I wouldn't know the first thing about that, unfortunately.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=1fab1ce5-93f1-4f34-b1a2-d6406adaf0b2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=a0a4d8f2-4f42-4be6-837c-416b0272ad98 /home           ext3    relatime        0       2
# /dev/sda1
UUID=2c9631fa-24c3-4ae3-a1b4-6387b956aea6 none            swap    sw              0       0
**/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0**
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by Perryg on 2009-03-07
> **rootless said:**
> The line that I commented out is in bold. Thank you so much for your help Perry. I'm going to power cycle, and see what happens. Any ideas on how to fix the BIOS? I wouldn't know the first thing about that, unfortunately.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=1fab1ce5-93f1-4f34-b1a2-d6406adaf0b2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=a0a4d8f2-4f42-4be6-837c-416b0272ad98 /home           ext3    relatime        0       2
# /dev/sda1
UUID=2c9631fa-24c3-4ae3-a1b4-6387b956aea6 none            swap    sw              0       0
**/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0**
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Usually when you install new or replacement hardware you enter the BIOS mode when you first turn the system on and either auto detect or manually tell it what you have.  Some hot keys are the delete key, f1, or f2 key.  It more than likely tells you this are startup but may go by really quick.  That is where to start first.  When it sees your hardware you will be presented with an option to save and exit.  Follow the bouncing ball and do what it tells you then see if you can boot with the live cd.  If you can not boot with the live cd (after you tell bios the boot order of cd then hdd). you will more than likely not have a cd in Ubuntu.

---

### Post by rootless on 2009-03-07
Well, the cycle is done. Nothing has changed in fstab. I'm not sure what to do. I suppose I'll try to change to lilo... but it's hard to do anything without being able to boot from CD. 

I would suspect a defective drive... except I can hear it spinning, and the door opens fine. The supplier said it had been tested before he sold it... but maybe it really is broken?

Any ideas on how to fix the BIOS?

---

### Post by Perryg on 2009-03-07
> **rootless said:**
> Well, the cycle is done. Nothing has changed in fstab. I'm not sure what to do. I suppose I'll try to change to lilo... but it's hard to do anything without being able to boot from CD. 

I would suspect a defective drive... except I can hear it spinning, and the door opens fine. The supplier said it had been tested before he sold it... but maybe it really is broken?

Any ideas on how to fix the BIOS?

Just because it spins or the door opens does not mean it is ready to use.

First did you go into the BIOS configure screen and did it find it there?
Next if it did find it did you tell it to save and exit?

If you did this and it still does not work I don't think lilo will do you any good.  Funny thing about laptops is they usually are built with to operate with what came with them.  Changing the architecture can really mess with them.  Before I get you into doing anything with the BIOS I want to know the model of the new cd/dvd drive so I can see if it is compatible with your unit.

---

### Post by rootless on 2009-03-07
In the list of bootable devices in BIOS, the name of the device isn't listed under CD/DVD. I hunted around in there for a while, but I couldn't find a way to get it to autodetect, or manually input what kind of drive it was.

---

### Post by Perryg on 2009-03-07
> **rootless said:**
> In the list of bootable devices in BIOS, the name of the device isn't listed under CD/DVD. I hunted around in there for a while, but I couldn't find a way to get it to autodetect, or manually input what kind of drive it was.

That's what I was afraid of.  It may be that it is a windows only cd/dvd but in that case the cd is useless since it has to have pre-OS access to install anything.  I would see the person you bought it from about a refund or replacement.   In the mean time if you send me the make and model number of the drive I will see if there is anything else I can find out.

---

### Post by rootless on 2009-03-07
> **Perryg said:**
>  It may be that it is a windows only cd/dvd

I didn't know such a thing existed. You're talking about a cd/dvd drive that runs only with windows? That sort of annoys me that they would make such a thing.

On the drive, it says

> MODEL SR-8177-M     MBZ1    P

---

### Post by Perryg on 2009-03-07
> **rootless said:**
> I didn't know such a thing existed. You're talking about a cd/dvd drive that runs only with windows? That sort of annoys me that they would make such a thing.

On the drive, it says

First here is a link to the lenova site for your model of laptop

[http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-4YRPZ7](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-4YRPZ7)

You might also try taking the battery out of the unit for an hour or so to see if the BIOS will reset and maybe pickup the drive.  It really should see it automatically if it is in good working order

---

### Post by rootless on 2009-03-07
Hey, thanks. I'll try that. I'll let you know how it goes.

---

### Post by tg1w on 2009-11-06
How did it go :)? I'm facing a similar "special device" problem described on this thread [http://ubuntuforums.org/showthread.php?t=1313854]("http://ubuntuforums.org/showthread.php?t=1313854").

```

root@ubuntu:/# mount -a
mount: special device /dev/disk/by-uuid/9c30c2b1-7423-48c7-86c5-eceddd6d41f6 does not exist

```

Thanks

---

