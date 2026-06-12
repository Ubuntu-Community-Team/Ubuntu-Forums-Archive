---
title: "Computer gets screwed up with 2 hard drives installed"
date: 2013-12-04
forum: Hardware
---

### Post by jhilp on 2013-12-04
I have a custom built computer with an ASRock G41C-GS motherboard.  I'd like to set it up with two or three SATA hard drives hooked up directly to the motherboard (no external or USB hookup) so I can default to my main hard drive, and have the option to boot to one of the other HDDs from the BIOS at startup.  Trouble is, it seems like every time I do that it screws things up.  The first time I tried, I hooked up two SATA hard drives in addition to my main SSD.  Immediately after trying hooking everything up, the computer tried restarting itself, and then just sat there with a blank screen.  I had to reset the CMOS by removing the battery and then go back to just one HDD hooked up before it started functioning normally.  I gave up on the whole idea for a few weeks until last night I loaded (perish the thought!) Windows on an extra hard drive and hooked it up to my motherboard.  Everything seemed to work great.  I set up the BIOS to boot up to my preferred hard drive, and if I wanted to boot the second HDD I just chose a different one in the BIOS boot menu.  Then, while I was running Windows, I hooked up my smart phone to one of the USBs, and immediately the screen went blank and the computer seemed to be trying to restart.  As soon as I unplugged the USB and hit the manual restart, things seemed to work fine again.  This happened 2 or 3 times before I gave up, reset the CMOS and unhooked the second hard drive.  I know this problem was caused by the dual hard drive setup, because this was one of the same things that happened the first time I tried multiple hard drives. Can anyone tell me why this is happening? I've asked some computer techs I know and even people on this forum about setting up more than one hard drive, and I've been told it should work.  Am I missing something?  Any help is appreciated. Thanks!

Here is a link to the thread where I previously asked for advice about setting up multiple hard drives: [http://ubuntuforums.org/showthread.php?t=2187247](http://ubuntuforums.org/showthread.php?t=2187247)

---

### Post by sudodus on 2013-12-05
I have one computer with 2 internal SATA drives and one eSATA drive (which behaves like an internal drive): No problems. I have another (old) computer with two internal IDE (PATA) drives: No problems.

You should be able to select the boot order not only between different kinds of devices HDD, USB, optical, but also between the HDDs. All mass storage devices might be treated like HDDs (also SSDs, USB pendrives and flash cards). So change the boot order between them in the BIOS/UEFI menu system :-)

You might also need to change a setting to AHCI, see [https://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface](https://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface) to run several SATA drives.

---

### Post by oldfred on 2013-12-05
I do know that newer Asrock motherboards as Asmedia ports that cause major issues. Does yours have Asmedia ports?

 So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!

---

### Post by jhilp on 2013-12-05
I Googled Asmedia SATA and looked at images.  If Asmedia sata looks like most of the pictures that came up with that search, I don't have Asmedia ports.  Here is a picture of my motherboard: [http://www.ebay.com/ctg/ASRock-G41C-GS-LGA-775-Socket-T-Intel-Motherboard-/141740777](http://www.ebay.com/ctg/ASRock-G41C-GS-LGA-775-Socket-T-Intel-Motherboard-/141740777)

---

