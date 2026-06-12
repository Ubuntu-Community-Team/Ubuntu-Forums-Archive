---
title: "gets lost on final HD boot and quits"
date: 2006-01-31
forum: Installation &amp; Upgrades
---

### Post by RKF on 2006-01-31
AMD Athlon XP

Only one clean HD inserted, all others are out. 

Initial CD boot and load sent to erase and format. All goes well till booting from the HD. Gets to big brown screen 'loading modules' then quits. 

Messages:

#Alert!/dev/hdg1 does not exist


#can't get past /bin/sh: 

The type # help provides gibberish to the non-programmer

This has been the same on two separate HDs with two different installation discs, one of which is known to be good. Eventually getting to all peripherals off and Network unplugged. 4 installs all the same error.

Only thing left that I can think of is the Athlon AMD Chip, AMD_-_x86_FAMILY_6_MODEL_10\_10

help would be appreciated

---

### Post by amohanty on 2006-01-31
> Only one clean HD inserted, all others are out. 

Ok I am a bit confused here. Are you using hot-plug hdds?
If not where and when did you install grub or any other boot-loader you are using?

AM

---

### Post by RKF on 2006-01-31
After getting lost in Suse, and crashing my main windows drive a few weeks ago I decided to use swappable racks for IDEs so I could play safely.

When loading the ubutu all that was in the computer was a single 40Gig IDE HD. Same same loading Windows from scratch. Everything is clean and fresh :) No peripherals, nothing. Just the motherboard the CD/DVD drives and the HD.

Set up is such that one rack can only have a Windows OS or a Linux OS and the others are not interchangeable.  The Grub loader is whatever came off of the Ubuntu disc/s.

Cheers

---

### Post by amohanty on 2006-01-31
The thing is that if grub is loaded in the mbr it expects a specific hdd configuration and partition setup. If you swap drive sin and out and they do not have the same kind of information grub will be kind of lost (as would be expected). So if you are going to swap drives, I suggest you install grub on the boot sector of each hdd that can be used as the primary master hdd. 

AM

---

### Post by RKF on 2006-01-31
The drives are not swapped hot. 

The ubuntu has been loaded to a virgin drive which is the primary master drive.  The Ubunto does its own partioning for its own per the CD, and I would have expected it to install its own accessable appropriate boot sector 

Are you saying that the grub loader is expecting to see a Windows OS somewhere in one of the partions?????

How does one load a separate boot sector. Don't know how to do it for windows let alone Linux.

Cheers

---

### Post by amohanty on 2006-01-31
> The drives are not swapped hot. 

That doesnt matter. What happens is by default (if not done otherwise) GRUB is installed in the MBR, which is not affected by drive swapping. Once installed there it expects the primary master drive or other drives that it saw during the install to be in the same place with the same kind of partition table. Think of it this way:

1. computer boots
2. BIOS loads whatever is in MBR (in this case GRUB)
3. GRUB reads config file
4. GRUB looks for partition table of the drive which has the default bootup OS (could be primary master or slave or secondary and so on)
5. Then it loads up the boot loader or the OS image on the partition specified in its config file.

Now in this scenario if you swapped the hdds (cold swap) all of a sudden the partition specifications in GRUB's config file are no longer valid.

So in such a situation it is advisable to install GRUB in the boot sector of HDD, you have to explicitely ask the installer to do so, by default it puts it in the MBR.

I would suggest that you plug in all your HDDs and restore GRUB using instructions here:
[http://ubuntuforums.org/showthread.php?t=76652&highlight=restore+GRUB](http://ubuntuforums.org/showthread.php?t=76652&highlight=restore+GRUB)

You prolly dont need to worry about a total crash as I have never had that happen. To be doubly safe mount the windows partition in your /etc/fstab as read-only.

HTH
AM

---

### Post by RKF on 2006-01-31
Thanks

Accept what you say and will try all that when I get back to my computer. 

What's an MBR?

However, while trying not to appear to be too thick, no drives were changed out between the time the CD loaded and the modules wouldn't load, so wouldn't the Grub look for the boot sector or whatever else, in the positions/locations already allocated by the CD/Format/Load. 

I don't have a Windows partition, that is what I have been trying to say; the HD is partitioned only for Ubuntu/Linux so how could he Grub/boot sector be lost.

Anyway have printed out all of the thread you mentioned above about restoring the Grub and will suck it and see :) 

Ta

---

### Post by amohanty on 2006-01-31
> What's an MBR?

[http://www.ata-atapi.com/hiwmbr.htm](http://www.ata-atapi.com/hiwmbr.htm)

> However, while trying not to appear to be too thick, no drives were changed out between the time the CD loaded and the modules wouldn't load, so wouldn't the Grub look for the boot sector or whatever else, in the positions/locations already allocated by the CD/Format/Load.


Ok, then it should have booted fine.. however if you are getting a message like could not find /dev/hdg... usually indicates a partition table mismatch/trouble etc. hence the direction I took.

Ok then the error messages would be really helpful.
Also the _exact_ HDD setup and whats installed where would also be very helpful to figure out what is happening.

Of course a reinstall only takes 25 mins :)

AM

---

### Post by RKF on 2006-01-31
Hello again

The only error messages were the ones I provided initially at the top of the thread.  

Been reinstalled 4 times each with different virgin HDD and/or different installation discs. Same Error message each time.

Computer consists of AMD Athlon chip, std motherboard, two DVD read/writes, 1.4 meg floppy drive, and 3 removable drives. Two IDEs and one SATA. All printers, networking, routers etc, imaging devices etc. disconnected after the first time failure. 

The IDEs are:

1. The Master drive (c:) one for Windows only, and one for Linux only. Only one of which can be in the case at any one time. It is set up so one cannot be installed unless the other is removed (same slot)

2. Data drive for my 4wd (truck) which backs up my laptop drive when I'm bush. Carries al of my GPS mapping crap and photos etc. etc. It is a different brand and physical carrier/tray to the Master drive. Other rack is under the front seat of my truck.  Not interchangeable with the master drive - _has been out while all of this has been going on._

The SATA drive is the computer main data drive - storage only no operating system software at all.  It too has been uninstalled (out of its slot)  as well.

Hope this all helps 

Cheers

---

### Post by RKF on 2006-02-01
OK - been there done that as far as I can follow the instructions. Seemed to go OK but ended up with the same error message/s.

However, did notice while stepping throught the various "continue" pages, on which said there is not another operating system on this disc.

Suspect that the CD with its formatting and loading is expecting to see another OS boot sector or whatever as well as the ubuntu. When the grub doesn't see it if craps out. 

Is there a disc or whatever which loads Ubuntu to a computer where it will be the only operating system. This is the way mine is set up. One Master drive with Windows and a separate master drive to take the Linux. Ne'er the two shall meet. Only one or the other can be inserted at one time.

RKF

---

### Post by amohanty on 2006-02-01
> Suspect that the CD with its formatting and loading is expecting to see another OS boot sector or whatever as well as the ubuntu. When the grub doesn't see it if craps out.

Ok so, you have one IDE in the system. When you install Ubuntu and are setting up GRUB it detects another OS? 
My understanding of the way that works is that it scans all HDDs to find any recognizable os image. Since you only have one HDD it shouldnt do that. 
What is the OS id string that the installer offers?
You could try a clean install ie. Plug in the Ubuntu drive.
Insert Win98 SE boot floppy ([www.bootdisk.de)](www.bootdisk.de)). Use **fdisk** to remove all partition information on the drive. Use **fdisk /mbr** to clean out the MBR. (You can do the same using a live cd too).
Then install Ubuntu. It _should not_ prompt you about an existing non-ubuntu OS, under any circumstances.

HTH
AM

---

### Post by RKF on 2006-02-02
OK Has gone in and loaded.

Used FDISK and then tired the LVM (is it option) Everything went as I suppsoe is advertised except for the networking, though it still connected to 

Bound to be more to come, but this problem is resolved.

Ta

Cheers

---

