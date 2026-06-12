---
title: "Wanted: tips for building ubuntu/windows box"
date: 2005-10-03
forum: Hardware &amp; Laptops
---

### Post by nrwilk on 2005-10-03
Right now I'm dual-booting Kubuntu on my PPC machine.  But I want to harness the advantages that come with running it on an i386 chipset (I'm building the box anyway, I'd just like to build it with both Windows and ubuntu in mind from the start).  I'd just like some examples of stable hardware that's guaranteed to work with both Windows and ubuntu.  Simple stuff like:
Would it be too hard to get ubuntu to boot off a SATA drive?
I know almost everyon in any linux community agrees that nvidia is the better choice for a VPU because of the availability of drivers for their higher-end cards.  I have no experience with nvidia at all, I've always had ATI cards.  What are some nice semi-high-end nvidia cards that will give me nice 3D performance in both Windows and ubuntu?
Any other tips I should know about to build a working box the first time?
Thanks for any help!  I'm sure I'll come up with more questions, but feel free to post anything that may come to your mind.
Thanks again.

---

### Post by Biased turkey on 2005-10-04
All right, this is my " no sweat" windows/ubuntu rig:
Nforce4 chipset mobo ( Elitegroup KN1 extreme ) with an AMD 64 ( if you want a 32 bits AMD Athlon XP processor, get an Nvidia Nforce2 mobo )
2 Seagate 80 GB Barracuda SATA drives
Nvidia Geforce 6600 video card ( decent midrange card )
I use the onboard sound and Ethernet network chips.

Getting the 3D hardware acceleration working with Ubuntu is just a 2 steps 10 minutes process: Installing a package and editing 1 line in a config file.
ATI is fine, but imho their Linux support is not on par with the one from Nvidia
Audigy2 sound card requires somme smal tweaking too.

---

### Post by floyd27 on 2005-10-04
Try to stay away from cordless keyboards..
Iv had them working fine in both windows and ubuntu ..
However when you use grub/lilo to select OS's the cordless keyboard wont recognize until your in one oro the other, so you cant select unless you have a "slave" keyboard....just to select the OS.

It does work to get into BIOS but shortly after wont until your in a OS..
dont know if there is a fix...
p.s thisa is for dual boot on 1 HDD dont know about 2 HDD's....

---

### Post by JELaVallee on 2005-10-04
Here's my home workstation rig (a.k.a "Boxie"):

Shuttle SN41G2 XPC Cube Barebones Kit using an nForce2 mobo chipset that provides:
  - LAN 10/100 (Realtek 8201BL)
  - USB 2.0, Firewire 400
  - 5.1 Audio (Realtek ALC650)
  - 2 Ultra DMA 133 IDE interfaces
  - 1 AGP 4x/8x slot, 1 PCI slot
  - 2 Dual-channel DDR Slots (up to 400MHz FSB, 2GB max)
  - Built-in nVidea GeForce 4 MX Card w/ DualHead support(shared mem, kinda sux, but not bad for general use, I keep meaning to upgrade to an AGP card for games)

I put in an Athlon XP 2800+ CPU, 1Gb of Dualchannel RAM, a Maxtor 250Gb IDE drive (CompUSA had 'em for $80 after rebates back in June), and a 4x DVD +/- RW (Sony OEM I think). The Shuttle kit includes its own (rather ingenius) CPU cooling system and when all setup measures out at about 20cm x 20cm x 30cm.  The whole rig cost me just a little over $500US.

Installation went like this:
1) Used a Knoppix LiveCD and Qparted to partition up the drive like so:
    - 20GB ntfs: Windows Boot/System Partition
    - 20GB ext3: Ubuntu Boot/System Partition
    - 2GB swap: Ubuntu System Swap partition
    - 80GB fat32: Shared bulk file system 1 (MP3, Images, Divx's, games, etc)
    - 80GB fat32: Shared bulk file system 2 (MP3, Images, Divx's, games, etc)
    - 40GB ext3: Ubuntu System Backup LZ
2) Installed Windows 2K/XP into the ntfs partition
3) Installed Ubuntu into the ext3 partition (install should detect the 2GB swap)
4) Configured GRUB during the Ubuntu install to include a boot entry for the Windows system (it also detected this and gave me the option).
5) Once installed and logged in to Ubuntu, I created mount points in my fstab for the two fat32 partitions to be r/w and mounted on boot as /windows/e and /windows/f respectively.

It's a great system.  Very little hardware problems that couldn't be solved either here or via a google search.  I use it almost exclusively in Ubuntu except for games and scanning (my epson scanner is just easier to use with its very custom win32 drivers).  I also have a 4GB VMWare partition in my Ubuntu file system for running Win2k in VM mode and it works very smoothly (something of a RAM hog tho), so I can have IE for web dev testing and windows specific tools (Visio, Photoshop CS and Illustrator CS).

The Shuttle kit is discontinued, but still can be found on eBay and elsewhere reasonably cheap.

All and all, I'm very happy with this setup and can't wait to give Breezy a run on it.

cheers,
Etienne

---

### Post by ngms27 on 2005-10-04
Thats what I'm running!!!

Works a treat.

JonnyT

---

### Post by nrwilk on 2005-10-04
1. So, will SATA drives work out-of-the-box?

2. Can I run the i386 version of Kubuntu on an AMD 64 FX chip, even though the chip has 64bit architecture?  I know there is a ubuntu64 version, but I would like to run all the newest stuff (such as the new KDE 3.5 beta, which is only out for i386 architecture)

3. If yes to #2, will I notice a big loss in performance?  Or just a very small amount?  Are there any advantages to running the 64bit version on a 64bit processor over running the i386 version on a 64bit processor?

thanks!

---

### Post by Biased turkey on 2005-10-05
[QUOTE=Fealos]1. So, will SATA drives work out-of-the-box?
2. Can I run the i386 version of Kubuntu on an AMD 64 FX chip, even though the chip has 64bit architecture?  I know there is a ubuntu64 version, but I would like to run all the newest stuff (such as the new KDE 3.5 beta, which is only out for i386 architecture)
3. If yes to #2, will I notice a big loss in performance?  Or just a very small amount?  Are there any advantages to running the 64bit version on a 64bit processor over running the i386 version on a 64bit processor?
thanks![/QUOTE]

1) Yes
2) Yes. That's what I'm doing right now, running Ubuntu 32 bits version on my AMd 64 bits rig.
I triple boot: Windows 2000, Ubuntu 32 bits and Gentoo AMD64 bits versions

If ( yes to 2 ) then goto 3 :)
3) The only time I notice an obvious difference between the 32 and 64 bits versions is when compiling C++ programs using Kdevelop, but normal applications like gedit or mozilla don't run faster.
Maybe some graphics guru could tell us if applications like Povray run faster with the 64 bits version ( my guess is Yes )

---

### Post by floyd27 on 2005-10-05
so far kde 3.5 has no probs here either..
i love it................

---

### Post by agds on 2005-10-14
I apologize because this isn't a tip; I'm actually looking to tack a related question onto this thread.

I've been using Ubuntu for several months now, and I'm quite satisfied with it.  The only problem I've encountered has been a shortage of space on my Linux system partition.

I wanted to keep Windows on my machine because my IT work requires me to develop and run certain software only available for Windows.  Knowing the tendency of Windows applications to hog disk space, I gave my NTFS partition roughly half of an 80 GB drive.  The remainder is devoted to a large FAT32 partition for sharing data between Ubuntu and Windows, a Linux swap, and the comparatively tiny Linux system partition.  Recently I realized I wanted more disk space without compromising the amount allocated to any either OS, so I bought another HDD.

My question is what I should do with this new HDD to maximize the usefulness of the added disk space.  Any suggestions?  I'll be happy to clarify if my description of the situation was confusing.

---

### Post by nrwilk on 2005-10-14
agds, I bet that's a common question.  It'll be good for someone to answer it here.  (hey, I want to know too!)


Also, just to let everyone know, I got my machine built.

Specs:
Athlon 64 3500+ 2.2Ghz Venice
Abit AN8 Ultra MB
Samsung 200GB drive
1GB Corsair
Leadtek GeForce 6600 TD 256MB GPU

I've got Windows and Kubuntu dual-booting perfectly, and I'm really happy!

My first windows install, my first PC build, and all is fine.

The only hitch was that The Abit board came with a bunk Ethernet port.  Pissed me off to no end.  Just went out and got a cheap PCI ethernet card, and all is now fine.  I'm posting this from my new Kubuntu install!  Yay!

---

