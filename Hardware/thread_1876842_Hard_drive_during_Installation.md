---
title: "Hard drive during Installation"
date: 2011-11-06
forum: Hardware
---

### Post by pyro226 on 2011-11-06
I recently built a computer and am trying to install Ubuntu (Opensuse and puppy linux also have failed to install).  I am using the 64 bit version of the alternate installer for Ubuntu 11.10.  I am installing from a USB drive.  I was able to successfully install XP 32 bit, so I'm guessing that this is a compatibility problem.

During installation, it could not detect the hard drive.  I have since removed the DVD drive and it doesn't make a difference (if drive is empty, it refuses to continue to boot to the USB).  I have tried installing a jumper on the back of the hard drive to limit the data transfer to 1.5Gb/s and it doesn't seem to make a difference.  I have also tried several of the options in the mother board without luck.

Then I changed from the sata3 to the sata2 port and had to change both the boot priority and hard disk priority.  When I put the USB drive over the Sata drive in the Hard disk priority, it then removes the sata drive from the boot priority list and puts a UEFI USB disk and a standard USB disk to boot from.  This way it is able to detect the hard drive and partition it, but it now it keeps failing at the "Select and Install Software" stage.

When I go back and rerun "Select and Install Software" I can choose not to do automatic updates, I see a line that says something like "taskel" and it flashes "clean up" and then red-screens stating that it failed that step.

I have not tried to physically pull the graphics card yet, but I have  tried to install using internal graphics and it did the same thing.

My main hardware components are 

[LIST]
[*]ASRock H61M/U3S3 LGA 1155 Intel H61 (It says UEFI when booting)
[*]SAPPHIRE 100315L Radeon HD 6850
[*]Intel Core i5-2400 Sandy Bridge 3.1GHz
[*]G.SKILL Value Series 8GB (2 x 4GB) DDR3 1333 (PC3 10600)
[*]Seagate Barracuda ST31000524AS 1TB 7200 RPM 32MB Cache SATA 6.0Gb/s Internal Hard Drive
[*]SAMSUNG 22X DVD Burner
[/LIST]

---

### Post by Redblade20XX on 2011-11-07
Is your BIOs updated? Usually thats the first suspect for installations! 
:)

- Red

---

### Post by pyro226 on 2011-11-07
Ok, just updated the bios, but the problem remains.  I was able to get it to detect the hard drive still (even when on the Sata3 ports by switching around the options in Hard Disk BBS - bios boot sequence? and the boot priority), but it still freezes on the "Select and Install Software" stage.

---

### Post by pyro226 on 2011-11-07
I guess I'll try mounting it in an external USB enclosure and see if that makes a difference.  My current guess is that the hard drive is for some reason incompatible (I didn't know this was possible), but I don't have a different sata hard drive to test it with.  Any other ideas on what to test or try?

---

