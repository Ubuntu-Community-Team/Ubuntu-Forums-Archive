---
title: "New DVD burner not working"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by dylanologist on 2007-10-26
I just bought a new DVD burner and installed it in my desktop computer running Gutsy.  I placed it in a 5.25" slot below an existing CD burner, but since I won't be using that older device anymore, I simply took the cables out of the old CD drive and connected them to the new DVD drive.  I also set the jumper to the same setting:  CS (cable select?).

In other words, I only have one drive connected now, and it is set up exactly the way the old drive was set up, and the old drive worked just fine.  My problem is I am fairly new to Linux and I have no idea how to troubleshoot an optical drive.

All I've tried so far is booting an Ubuntu Live CD in the new drive.  When I do this, I see the MB splash screen and then get a blank screen.  I also noticed that the drive seems to be recognized when I enter the system BIOS.

Are there CLI commands I can use to check the status of the drive?  Or other basic troubleshooting procedures I should be trying?

Thanks in advance for any suggestions.

---

### Post by ddrichardson on 2007-10-26
Check in BIOS first to see if the drive is registered. Usually, IDE devices are connected as master or slave, in your case if it's on a cable on it's own set it to master. It's most likely that your bios simply has the settings for the old drive and not the new one.

---

### Post by dylanologist on 2007-10-26
I changed the jumper from CS to Master, but to no effect.  Drive still doesn't work in Gutsy (64bit), and when I tried booting from an Ubuntu Live CD in the drive, after the MB splash screen, I got a black screen with a cursor in the top left corner.

In the BIOS, here's how the drive (a Philips model SPD2413BD) turns up:

PATA Primary Master

Device : ARMD
Vendor: @H@L@P@ @P@2 1 P  (I presume this is trying to say: "Philips SPD2 1 P")
LBA Mode : Not Supported
PIO Mode : 2
Async DMA : Not Supported
Ultra DMA : Ultra DMA-4

PIO Mode   [Auto]
32 Bit Data Transfer   [Enabled]
ARMD Emulation Type   [Auto]


I'm not sure if anything here is out of the ordinary, but if I can't boot from the Live CD, does that mean that my installed version of Ubuntu is not the problem (or at least not the main problem anyway)?

Unfortunately, I'm not dual booting Windows on this machine (and don't want to), and I don't have access to any other desktop to test this burner on, but it's brand new, so chances are the hardware should work.

---

### Post by ddrichardson on 2007-10-27
When you say you get a blank screen, how far into the live cd is it? Can you <CTRL><ALT><F2> to get a terminal? Have you tried booting with pressing F6 on the menu and adding "noapic" to the line?

---

### Post by dylanologist on 2007-10-27
I'll try those suggestions tomorrow morning and let you know what happens.

---

### Post by dylanologist on 2007-10-29
When I try booting from the Live CD I get a blank screen w/ cursor in top left, and Ctrl+Alt+F2 does not bring me to a terminal.  So far as I can tell, all that works at this point is Ctrl+Alt+Del restarts the computer.  As for the second suggestion, I'm not familiar with what you're suggesting.  Is that while trying to boot from the Live CD?

When do I press F6?  Press and hold F6 from the time I turn on the computer?  Which boot screen are you referring to?  Could you give me a bit more info?

---

### Post by ddrichardson on 2007-10-29
Press F6 on the Live CD boot menu.

---

### Post by dylanologist on 2007-10-31
So things have gotten strange.

I bought a new rounded IDE cable, just to see if the old cable I was using was the source of the problem.  The new cable is long enough to connect both my new DVD burner and my old CD burner, so I figured why not try connecting both?  I set the CD drive as master and the DVD as slave because the CD drive is the first device on the cable (I don't know if that matters or not).

Now both drives "work" in Ubuntu, up to a point.  Any disk, no matter what type, is now detected as an "Audio Disc" and the Sound Juicer program automatically pops-up when a disk is inserted.  This is true, not only of actual audio discs, but also of data-DVDs and DVD-videos, as well as data-CDs.

When I enter the BIOS I noticed that both drives are detected in the IDE section, but both are listed as "Device:  Tape Drive".  [Previously the device of the DVD burner was listed as "ARMD".]  And yet it seems to detect the proper make and model of my new DVD burner.  Any thoughts on what might be happening here.

Oh, yeah, and neither drive is able to boot a Live CD - I hit the black screen, Ctrl+Alt+F2 is ineffective, and I don't ever see a Live CD boot menu at which to press F6.

---

### Post by ddrichardson on 2007-10-31
I'd pop off an email to your BIOS vendor and try updating to the latest BIOS.

---

