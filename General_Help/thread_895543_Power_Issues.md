---
title: "Power Issues"
date: 2008-08-20
forum: General Help
---

### Post by trashjunkid on 2008-08-20
Hello-

I am new to linux in general. I am setting up a server using ubuntu on a new dell quad core computer.

I got it setup nicely late last night, updated, booting up great.

I had rebooted and left it at the login screen over night (shouldn't have done that, I know).

This afternoon, I turned on the monitor and see that something not right has occurred. I believe the computer powered down/went into sleep mode or whatever due to inactivity and when I came back it was infinitely working it's way through starting back up, hung up on "failed to recover some devices" ata2....

When I started up in recover mode same problem.

I tried booting up using the ubuntu 8.04 livecd and following the advice here:
[http://ubuntuforums.org/archive/index.php/t-422523.html](http://ubuntuforums.org/archive/index.php/t-422523.html)

combined with the advice regarding "sudo: unable to resolve host ubuntu"

I could not get the install repaired so I ended up reinstalling...

But this leaves me wondering what could I have really done to fix the problem? How do you really use the livecd to help repair an install? What are the basic troubleshooting approaches in Ubuntu?

I am terribly new so please forgive me if these are terribly obvious questions,
Trashjunkid

---

### Post by tgalati4 on 2008-08-20
If this is brand-new hardware, then it's possible there are some hardware issues.  It's quite alright to leave the login screen up.

What is the motherboard and graphics card?  If you are not using the correct graphics card driver then you could have issues when the video goes to sleep.

Failed to recover some ata2 devices could be a power-up issue.  What is the size of the power supply and how many disk drives are in this machine?

Have you run memcheck overnight to verify RAM integrity?  You might need to verify that all of the hardware is running correctly before commissioning as a 24/7 server.

Quad-core might be overkill for a server.  What is the intended purpose of this machine?

As far as the live disk:  It gives you a fully-working operating system from a bootable CD.  This allows you to separately mount your disk drives to examine them or repair them.  It gives you networking so you can download patches, and gives you all of the native linux tools for standard troubleshooting.

Unfortunately, you need linux experience to use the Live CD for repair.  There are some tutorials floating around, but basically you use it when your system won't boot normally and you need a working system to examine log files and disks.

---

### Post by trashjunkid on 2008-08-22
First, thanks for replying.

It is all new gear except the monitor. I know, it is overkill as a server, but.... well, I guess I was hoping that this machine would be multiply capable for us, as a basic server and an occassional desktop, and maybe working my way towards a media server/pvr device.

The machine is double booting windows home xp and ubuntu.

It is a dell inspiron 530 quad core, Q6600. Here's a selection of information about the system from wikipedia:

Inspiron 530

The Inspiron 530 uses a Foxconn built OEM motherboard based on the Intel G33/ICH9R chipset and can be equipped with the following options:

Processor:

    * Intel CoreTM 2 Quad Q6600 (2.4 GHz, 1066 MHz FSB)

Operating Systems:

    * Genuine Windows® XP Home Edition
    * Ubuntu 8.04

Graphics:

    * Integrated Intel Graphics Media Accelerator 3100 (Intel GMA 3100)
    
Sound: Integrated 7.1 channel sound provided by an onboard Realtek ALC888 codec Creative Sound Blaster X-fi ExtremeGamer

Memory: 4GB of DDR2 RAM 800 MHz.

When ordered with an Intel Q6600 Core 2 Quad processor, the 530 is equipped with a FoxConn G33m03 motherboard and a LiteOn 375W power supply. 

Storage: 500GB,S2,#1 Unleaded,WD-ZEUS
Up to 750GB 7200 RPM Serial ATA hard drive. 16X DVD+/-RW Serial ATA optical drive.

The hard drive controller supports RAID 1, and up to 1 TB (1012 B) of storage. The hard drive controller also supports supports raid 0, raid 0+1 and raid 5 via a patched bios that can be found here.

It would serve as the only desktop in the house (replacing ancient dusty P3's running windows 98, rarely booted up).



Anything look awfully suspicious there? I simply installed the OS- I accepted the default settings for all drivers.

When you say:
> Unfortunately, you need linux experience to use the Live CD for repair. There are some tutorials floating around, but basically you use it when your system won't boot normally and you need a working system to examine log files and disks.

Where would you point a new fellow to gain some of that experience? Any tutorials you approve of?

I am cobbling together my time to get this accomplished so forgive my late reply. Thanks again,

-Trashjunkid

---

### Post by jeffrey2009 on 2009-08-11
Did you ever find a resolution for this?  I am having a similar problem where my system is not able to come out of sleep mode.

---

