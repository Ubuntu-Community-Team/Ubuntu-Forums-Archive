---
title: "issues with MSI P35D3 and optical drives."
date: 2009-03-24
forum: Hardware
---

### Post by DeadlyFoez on 2009-03-24
I'll start off by dumping my whole system specs.

Mobo: MSI P35D3 Platinum (Intel P35 and ICH9)
cpu: E6750
RAM: 2gb (2x1GB) DDR3 1333 MHz Corsiar
Video card: XFX 8800 GTS 640 MB
Drives;
  2 x 500gb Seagate sata II in raid 0 on intel ICH9 for data
  2 x 74gb WD Raptor in raid 0 on intel ICH9 for my Windows installation
  1 x 74gb WD Raptor on Marvell Controller
  1 x 80gb Seagate IDE on Marvell Controller used for Ubuntu 8.10
  1 x Plextor DVD-RW IDE on Marvell Controller

I also have a spare Lite-On DVD-RW Sata II that I connect when needed for OS installations.


My couple of issues;

It took a lot of effort to get this board to run anything other than Windows os's. I bought this board when it first came out and have been struggling since.

Apparently there is an issue with the ACPI implementation in all MSI motherboards that use the P35 chipset. I was able to finally get my hands on a modded firmware for my board which did some good for halfway fixing the issue.

I've tried nearly ever distro of linux out there and have tried every configuration with my board as for as what peripherals are attatched. What I finally was able to get it to install Ubuntu 8.10 to either my single 74gb raptor or my 80gb IDE drive. After installing completes, Ubuntu will not load unless I disconnect my 74 GB Sata Raptor that is on the Marvell controller. Error sequences written below.

I am fully able to have my RAIDS connected after installation completes, and I use my Windows Raid 0 running the vista boot loader to load all my other OS's. Ubuntu will boot as long as that optical drive is not connected.

After select Ubuntu from the vista boot loader this is what I get on my screen:

**BootPart 2.60 Bootsector  **{and wesite info}[B]
Loading new partition
Boot Sector from C.H. Hochstatter
Cannot load from hard disk.
Insert Systemdisk and press any key.
[/B]

I press a key and...

[B]Grub loading stage 1.5
[/B]
Then is shows the graphical loading ticker and then drops to text


[B]Boot from (hd0,0) ext3 09fffda-......-....-...
Starting up
loading please wait
Boot args (cat /proc/cmdline)
- check root delay=
- check root=
missing modules (cat /proc/modules; ls /dev)
Alert! /dev/disk/by-uuid/09fffda-.....-.....-... does not exist
Dropping to shell


Busy box built in shell (ash)
(initramfs) ata 8; SRST failed (errno=-16)
ata 8; SRST failed (errno=-16)
ata 8; reset failed, giving up
ata 8; SRST failed (errno=-16)
ata 8; SRST failed (errno=-16)
ata 8; SRST failed (errno=-16)
ata 8; SRST failed (errno=-16)
ata 8; reset failed, giving up
Buffer I/O error on device sdb1, logical block 145227392
Buffer I/O error on device sdb1, logical block 145227393
Buffer I/O error on device sdb1, logical block 145227394
Buffer I/O error on device sdb1, logical block 145227395
Buffer I/O error on device sdb1, logical block 145227396
Buffer I/O error on device sdb1, logical block 145227397
Buffer I/O error on device sdb1, logical block 145227398
Buffer I/O error on device sdb1, logical block 145227399
Buffer I/O error on device sdb1, logical block 145227392
Buffer I/O error on device sdb1, logical block 145227393
Buffer I/O error on device sdb1, logical block 145227394[/B]

I have omitted some stuff as far as web site info or the timing info on some of the errors because I could not write fast enough.



So my first question is, how can I make it that Ubuntu will either work with my other hard drive that is on the Marvell controller? I think the issue is that is trying to read from my raptor drive instead of my IDE.

My second question is how can I get Ubuntu to see my Raid 0 arrays that have the NTFS filesystem? The issue so far is that Ubuntu does not recognize the Raid 0 arrays as existing.

My last question, which may be better asked on the EasyBCD (Vista boot loader management software) forum; When I select the boot loader to load Ubuntu, it first gives me a longer than normal "System disk error" and I have to hit any key to continue, but then it will boot Ubuntu. Setting the BIOS to boot my linux drive first does not does not give me that error. What can I to to stop this error from coming up? and What linux partition actually has the boot information on it? 


If I tell the boot loader to boot the swap partition it will boot Ubuntu, but only with that error first. If I have it boot off the system partition it will not boot at all. And EasyBCD does not give me the option of selecting the MBR of that drive. 


As you can tell, I am a noob to linux. I just have never had the chance since it has been 2 years before I could get it to install. I actually did get Fedora 10 to installand have nearly the same issues, but I'd prefer to just go with Ubuntu.

I am pc technician professionally and know my way around a Windows OS better than most others. But linux is a different kind of beast. I am actually wanting to try BSD also so I can be more familiar with all systems.

I sure hope someone can give me a hand with this.
Thank you very much.

---

### Post by DeadlyFoez on 2009-03-25
Bump.

Anyone?

---

### Post by DeadlyFoez on 2009-03-25
Ok, SO what I have found so far is that I can have anything connected in all the ports on my motherboard except a hard drive in the sata port of the marvell controller, And it will work during installation and after installation as long as that hard drive is not connected on that port.

There is not an issue with the hard drive itself because I have plugged in a different one and tried it and it still wont work.

Anyone have any ideas??

---

### Post by DeadlyFoez on 2009-03-26
I think I may just have to move this to another area of the forum.

---

### Post by DeadlyFoez on 2009-03-30
Come on. Someone has to know something here. This is getting a little ridiculous.

Here I've been a windows user all my life and I am trying to convert and I can't get an inch of help from anyone. I almost dont see the point of wasting my time.

---

### Post by DeadlyFoez on 2009-03-31
Edit..

---

