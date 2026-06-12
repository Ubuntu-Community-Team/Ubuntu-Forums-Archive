---
title: "Installing with HDMI out only"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by Villainous on 2009-10-09
I am trying to do a new installation of Ubuntu on a pc I have repurposed for a Media Center.  Unfortunately, I only have HDMI out available to this machine without doing a bunch of moving, disassembly and a few other things.

I start the system with the CD in, and I get the initial screen asking for language, followed by choosing 'Install Ubuntu' however, once the disc starts to boot, my display shows a no signal message, and I am stuck at a blank screen.

Is it possible to install Ubuntu with HDMI out as my only video source?

My Setup:

Dell Optiplex mainboard
P4 - 2.8 Dual Core
2GB RAM (need to upgrade that)
2 x 250 GB HDD

I have the system in a custom case I built for my TV stand, so it's not in a traditional 'box' nor is it still in the Dell case, so not moving it would be ideal, however, if I have to, I have to...

I am currently running Windows 7 on this machine, but would like to move it to linux instead, and ubuntu has always treated me right.

Any thoughts?  Is there a special start up sequence I can use, or an extra command before the boot?

Thanks

---

### Post by Villainous on 2009-10-09
I thought I had made some progress on this, but it still is failing shortly after the installation is supposed to bring up the graphical screen.

By progress, I mean it took the system an extra few minutes (which was noticeable), to go blank during the installation.  I tried playing with the installation options, but still apparently to no avail.  I do have a VGA port on the back of my TV, and am awaiting a cable that I can connect to the computer to try installation that way.  However, I don't want to be stuck in an 800x600 environment, as I am creating a machine for HTPC use.

Anyone have any thoughts on how to get this working using HDMI during installation, instead of VGA or DVI (as I don't have a DVI input on my TV)?

---

### Post by Villainous on 2009-10-15
ok, this time I made some more progress, but still unsure as to why this installation isn't happening.  Instead of giving up as soon as the screen went blank, I let the system sit for a while longer.  Now, I get lines that read:

[xxx.xxxxxx] end_request: i/o error... 
SQUASHFS errors
unable to start backend errors

So, I'm wondering if there's actually an issue with the system, or with the disc I'm trying to install from.  I'm waiting on another disc to burn, but in the meantime I'm going to try 32-bit instead of 64-bit ubuntu and see if that makes a difference.

---

### Post by Villainous on 2009-10-15
32-bit installation didn't make a difference.  I'm still getting the 'no signal' error on my display when it tries to switch to graphical mode.

I'll keep plugging away with different discs to see what I can come up with.

---

### Post by Mark Phelps on 2009-10-17
My guess would be that the open source drivers used during installation can't handle HDMI output.  You didn't mention what video card/chip your are using, but if it's one that DOES have current ATI/Nvidia restricted drivers, my suggestion would be to install using a monitor and then configure the HDMI out after you install the restricted drivers later.

---

### Post by Villainous on 2009-10-30
My bad, I didn't realize I forgot that part.  It's a Radeon HD 4350 card.  There are open source drivers (supposedly) for it that are part of ubuntu.

I'm going to tear it all down after this weekend, try installing first, then work on getting the HDMI to work.

---

