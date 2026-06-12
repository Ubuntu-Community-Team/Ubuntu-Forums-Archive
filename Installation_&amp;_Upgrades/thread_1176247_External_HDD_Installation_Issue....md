---
title: "External HDD Installation Issue..."
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by AWraithe on 2009-06-02
Hi All...

  I've been in the IT field for 20 years, dealt with Unix flavors (Irix, etc) back in the 90s, and recently decided to give Ubuntu a try.  Thus far I like it, I have set up an 8.04 HH (Desktop version) server at work for our Internet Cafe (small side responsibility) with relatively little problems, using WebMin, etc and all is well.

  I have since decided to install the latest **9.04 JJ** (Server version) to allow me to become more proficient with it, and deemed it would be more convenient to put it on an bootable external drive, that way I can use it at home, and also bring it to work to play with when I have downtime.  Eventually I would like to run VMWare / VirtualBox on it and host multiple VMs (i.e. an Ubuntu one that I can't screw up/break, XP, Win7, etc), but for now I just want to get it up and running.

  After searching the forums until my eyes are bleeding, I'm not coming up with the right sequence of things to do, and reinstalling it every time, only to have it fail again is getting most frustrating.

  My basic problem is as follows:

   It appears to be installing correct, yet it comes up with.

    [B]No Bootable Device --  insert boot disk and press any key
   [/B] (after pressing any key, it then says):[B]
    GRUB Loading Stage 1.5.
    Error 21[/B]

  Here is the information up to this point:
    1.  Gateway 6610D, 4GB RAM/666MHz, BIOS LA97510J.15A.0285.2007, 2.66GHz CPU
    2.  I have triple checked the BIOS for:
         A.  USB Bootable (BIOS=Boot to HDD and USB Boot both enabled)
         B.  It sees the External (WD 320GB Passport) HDD
         C.  It stacks the External HDD in the boot order (CDRom, External HDD)
         D.  Tried 1. Auto, 2. All Removable, 3. All Fixed Disc for USB Mass Stg Emulation
    3.  Even disconnected the internal SATA HDD
    4.  Using **9.04 JJ** **Server Version** (which installs correctly on an Internal HDD)

 Here are the troubleshooting steps up to this point:
    1.  Disconnected Internal HDD  / Connected External HDD
    2.  Placed 9.04 JJ Sever CD into box and booted
    3.  Selected English, etc.  Got to Partitioning Stage and selected:
      SCSI5 (0,0,0) (sda) - 320.1gb
[SIZE=1][B]     #1  Pri      10gb    ext3     /                <--  selected 'Bootable Flag On'
     #5  Log     10gb    ext3     /usr
     #6  Log      5gb     ext3     /var
     #7  Log      5gb     ext3     /tmp
     #8  Log    10gb     ext3     /home
     #9  Log   172gb    ext3     /vm          <-- For the Virtual Machine storage later
     #3  Pri    100gb    fat32    /data       <-- For storing data from VMs (Linux/Win)
     #2  Pri       8gb    SWAP    SWAP[/B][/SIZE]
   4.  Obviously the installer is seeing the HDD, allowing me to partition it, even formatting it (as I see each time I load up the installer, the new partition sizes are there, file systems, etc, only missing the mount points)
   5.  Entered in a name, password, etc and when given the options for installation packages, I selected 'VM'  (in the past I had done LAMP for my internet server)
   6.  It formats, downloads packages, etc and 10 minutes later I'm rebooting.  I take the CD out and allow it to reboot and it comes up with the following:

    [B]No Bootable Device --  insert boot disk and press any key
   [/B]      (after pressing any key, it then says):[B]
    GRUB Loading Stage 1.5.
    Error 21[/B]

 In summation, I'm positive I'm just making some newb error, but from what I'm reading, this A.  Can be done.  and B.  Doesn't need any /boot or anything to get it to run.

  Any help, or even pointing me in the right direction would be most appreciated, and thanks in advance!

~AW

---

### Post by dandnsmith on 2009-06-02
*3. Even disconnected the internal SATA HDD*

Therein lies your problem I think - at the GRUB install the parameters set are for the HDD setup at the time.

Have you tried booting with just the external HDD connected?

You can probably sort it out with Super Grub Disk.

---

