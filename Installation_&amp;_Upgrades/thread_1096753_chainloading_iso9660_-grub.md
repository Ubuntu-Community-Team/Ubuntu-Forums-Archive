---
title: "chainloading iso9660 -grub"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by TheLocalGraveDigger on 2009-03-15
as fun as booting directly from an .iso image would be , dd'ing the file into an unused partition(I use my swap partition for this)and choosing the kernel and initrd file is suitable for me. having tested this and used it to install Damn Small Linux on a few old laptops I know it can work from Grub4Dos. however i would like a way to just chain load into the 9660 partition without selecting the kernel and just booting it that way. is this possible?
(hd0,0)/boot
(hd0,1)9660
(hd0,2)keeper of all other ISOs
any help would be appreciated

---

### Post by meierfra. on 2009-03-15
I'm not sure I understand the question. 

The kernel has to be loaded at some stage.   Grub can chainload any  boot code in the boot sector of 9660 partition.   If 9660 is an ext partition, grub  can also chainload  any boot code in any file on  9660. But the chainloaded boot code must contain instruction to load the kernel somewhere down the road.


For example you can install Grub to the boot sector of the 9660 partition and then chainload the boot sector via "chainloader (hd0,1)+1"

I hope this makes some sense.

---

### Post by TheLocalGraveDigger on 2009-03-20
I,m sorry for not explaining this. ISO 9660 is the standard format used in cds, thus it is not an ext partition.

my interest is when you boot from a CD some boot process occurs that selects the kernel, boot options and other information without any user intervention, usually giving a menu to continue booting. this process must take information from the CD and thus would be on the 9660 partition.I want to know were this information is so when i put a new image into the partition I don't need to try every file in the /boot /isolinux and other directory's until i find a multi boot compliant kernel. as for 
chainloader (hd0,1)+1 i have tried but it does not work in this case.

---

### Post by meierfra. on 2009-03-20
Grub is not able to boot CDs. So I don't think grub will be able to boot  a 9660 partition.
Grub can boot CDs indirectly by using SBM, See for example
[http://cutecomputer.wordpress.com/2006/10/10/boot-cdrom-through-grub/](http://cutecomputer.wordpress.com/2006/10/10/boot-cdrom-through-grub/)
Maybe SBM can also be used to boot a iso9660 partition. But I'm not sure.

I know that Grub2 supports iso9660. So you might give Grub2 a try.

---

### Post by TheLocalGraveDigger on 2009-03-24
I tried to use grub 2 a month back, but it broke my menu.lst setup and i could not figure out how to fix it. grub4dos (fork of grub legacy) can boot from an iso 9660 partition and any distribution that does not complain about a lack of cds in the drive will boot(my Debian isos were a not proceeding for this reason). SMB looks interesting and i will try it on the weekend.

---

### Post by Albert Net on 2009-12-14
How to boot from a iso9660 partition using grub4dos? I use this

root (hd0,5)    
//filesystem type is iso9660, partition type 0x0B
chainloader (hd0,5)
//invalid or unsupported executable format
boot



but it doesn't work. 
what is the correct way?

---

### Post by oldfred on 2009-12-14
Do not know grub4dos, but did you copy your command wrong.
chainloader (hd0.5)

I spent a lifetime thirty years ago trying to figure out why some code did not work and it was comma not period.

---

### Post by Albert Net on 2009-12-14
Thank your for your remind. I just made that mistake here.
The command is right.

After "chainloader (hd0,5)+1", it gives me "invalid or unsupported executable format"

What I am trying to do is to boot from iso file in hard drive without burning it to CD. It seems that format one partition to iso9660 is one solution, but it does not work on my computer. I have no idea why.

---

### Post by flabdablet on 2010-01-05
The standard for bootable CD-ROMs is called El Torito, and its boot process looks different enough from that for hard disks that simple chain-loading is unlikely to fly.

If an El Torito CD-ROM is set up in one of the so-called "emulation modes", then the BIOS will create a "fake" write-protected floppy disk drive from a contiguous 1.2, 1.44 or 2.88 MB chunk of disc data (which is identified by a special "boot catalog" and isn't necessarily also exposed as a normal ISO9660-accessible file) and make it accessible via Int 13H as device 0, the number usually assigned to the first floppy disk drive.

This fake drive, like a typical real floppy drive, will identify itself as having 512-byte sectors, and any code that would normally use Int 13H "read sectors" commands to read from a floppy will work just fine off the fake drive as well. This is how the Windows 98SE CD-ROM boots, and it's why you can boot from that disc "without CD-ROM support" and still see a bunch of files on drive A:.

El Torito also allows a bootable CD-ROM to be set up in "no emulation" mode. The Windows XP setup disc and anything that uses Isolinux work this way.

A disc laid out in no-emulation mode will not cause the BIOS to create a fake floppy disk; instead, the BIOS simply reads the specified number of sectors from the boot region (which, again, need not be and in fact is usually not exposed as an ISO9660 file) and transfers control to the boot code so read.

This sounds a lot like what GRUB does in a typical chain-loading scenario, so provided you can find which block your non-emulation CD-ROM image's boot code starts on, you should be able to chain-load from your CD-ROM image without any trouble, right?

Wrong.

You might well be able to read the first-stage boot loader from the CD-ROM image (though my experiments with GRUB have lead me to believe that chain-loading anything more than a single 512-byte sector tends not to work well). But once the CD-ROM's own boot loader takes control, it will fail, and fail badly.

Why?

Two reasons.

The Int 13H read requests that typical non-emulation CD-ROM boot code relies on don't know squat about partition tables. If boot code asks Int 13H for block N from the current boot device, it will be handed the Nth block relative to the start of the whole hard disk, not relative to the start of the partition you thought you were booting from. 

Second, CD-ROMs use 2048-byte sectors rather than the 512-byte sectors that hard disks use, and Int 13H specifies data quantities in sectors, not bytes. So not only is the CD-ROM's boot loader going to get unexpected sectors, it's going to get only a quarter of the data quantity it was expecting. Yes, there's another Int 13H call to tell you what the sector size is on the drive you're interested in, but I've never seen CD-ROM boot code that uses it; it all just assumes 2048 bytes.

I'm currently in the process of writing a little pre-booter for CD-ROM images on hard disks, which I hope will overcome all this difficulty. My plan is to hook Int 13H with a bit of code that creates a "fake" CD-ROM in much the same way as the BIOS's own El Torito support creates its "fake" floppy, and then perform a normal El Torito boot sequence (including the creation of a second fake drive for any emulated floppies). Hopefully this will all fit in 512 bytes, so it can get stuck over sector 0 after an ISO9660 image is put on a partition, and then chain-loaded in the usual way (maybe by GRUB, maybe by a DOS or Windows NT MBR).

I'm still not sure of the best place in the real-mode memory map to stick my hook driver to minimize the chances of it being overwritten before the boot process is far enough along that nobody cares about Int 13h any more. This might in fact mean that it has to stay available indefinitely, if you were for example booting a Windows 98SE installer CD-ROM image: Windows 98 is built on DOS and DOS does all its disk I/O via BIOS calls.

It's also been a lot of years since I wrote 8086 assembly code in anger. So it may all come to nothing. But if it works for me, I'll make it all available for other people to test, break and improve.

Naturally, if anybody can point me to a project that already *does* this, I'd be grateful.

---

### Post by Arbiel on 2012-03-19
Hi

I hope this thread to still be open. 

@ [flabdablet]("http://ubuntuforums.org/member.php?u=58952")

Where are you with this project ?

Arbiel

---

### Post by oldfred on 2012-03-20
I am closing this thread as it is old but linking to another closed thread just for reference.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
and this one.
This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

If you still have issues start a new thread as grub is now grub2 and many changes have occurred.

---

