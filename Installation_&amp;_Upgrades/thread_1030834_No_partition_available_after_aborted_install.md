---
title: "No partition available after aborted install"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by Greg1234 on 2009-01-04
Hi everyone.

I've had a few issues caused by an ill-informed Ubuntu 8.04 Installation on my ACER Extensa 5620Z Laptop. Here's my situation:

Where I was;
-1 80GB hard drive
-1 40GB partition with Windows Vista Home Basic ( C : )
-1 40GB partition that was empty ( D : )

Where I am;
-1 79.6 GB Media, which no longer has my original Vista Installation, only some Ubuntu related folders (cdrom, etc, lost+found, media, var)
-1 Image of my original installation
-1 USB Drive with a back up all my personal files

How I got there;

I downloaded and wrote Ubuntu 8.04 to a disk, booted it as a LiveCD and had a bit of a look around.  My original plan was to read a lot more about installation and partitioning before installing but I gave into curiosity and went ahead anyway.  

A few screens in I was asked where I'd like to install. In hindsight I think I chose something along the lines of "Install to entire disk", and as I shake my head now, all I can think is "It seemed like a good idea at the time".

About 10 seconds after I started the installation I realised what I was doing, panicked, resisted the urge for a few seconds, before giving in and manually aborting the installation by turning my laptop off.

Attempting to boot from the hard drive left me with a blinking cursor on a black screen immediately after the BIOS (no suprises there).  Booting from the LiveCD informed me I had a 76.9 GB Media, but no C or D drive.

Finally I dug out the image of my Vista Installation (how I love back-ups) and attempted to boot from the disc. I'm presented with a black screen and a message "Windows is loading files..." and a grey loading bar across the bottom of the screen for 2 minutes.  The loading completes and the loading screen of the normal Vista Installation displays(with the green loading bar that normally displays between the BIOS and the log-in), before an graphic "Acer" screen displays with a message box; title "Error", prompt "No partition available" and button "OK".  Clicking "OK" returns me to the BIOS screen.

Where I'd like to be;
-My original Vista Installation restored, on the net, learning how to not make the same mistakes again

How to get there;

I am unsure about how to proceed from here.  Hopefully it as simple as using a utility on the Live CD to "restore the partition structure" of my hard drive in order to restore my system from the image.

---

### Post by DforVendetta on 2009-01-04
I may have done that once upon a time. Look on the bright side, you have a lot of free space.

---

### Post by spcwingo on 2009-01-04
From my limited experience I have gathered that Windows install disks will not recognize linux formatted partitions.  To solve this just reboot with the Ubuntu live CD, fire up gparted, repartition however you see fit, then retry the Windows install.  Let me know if this does the trick.

---

### Post by Greg1234 on 2009-01-05
Thanks spcwingo, I'm at work at the moment, I'll try that in a few hours.  I suppose I just needed someone one to point me to the right utility on my LiveCD to get me started.

---

