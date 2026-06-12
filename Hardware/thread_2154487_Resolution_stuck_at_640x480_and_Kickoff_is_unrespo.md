---
title: "Resolution stuck at 640x480 and Kickoff is unresponsive with nVidia drivers"
date: 2013-06-14
forum: Hardware
---

### Post by parallelcircuit on 2013-06-14
Ok, so, there may or may not be several issues at hand here. I'll give as much info as possible.

I've got an XPC Shuttle that I decided to use as a HTPC. Had it up and running for a few months with minimal issues but then decided I should update the nVidia drivers because I would occasionally get MASSIVE frame rate drop when playing Minecraft (as in from 120+ to 4~5 FPS). Woe unto me!

After installing the drivers my resolution was stuck at 640x480, and also wasn't centering in any workable way; I couldn't even see the Kickoff Plasmoid in the corner or anything else that close to the edge. I ran around the internet trying one command line fix after another before talking to a friend who said it may be because I had a 7800 GT, and that I might try an 8 series or newer. Well, I just happened to have a PNY 8600 GS laying on my desk so I decided to nuke the install and start from scratch. 

After swapping out cards I booted up from my disc and installed a brand new copy of Kubuntu 13.04; everything went pretty smoothly until I tried to install the nVidia drivers for my card (does this happen to everyone?) As soon as I did that and rebooted my computer I get the familiar 640x480 desktop; coupled with an unresponsive Kickoff menu. I can click the Plasmoid and open it up, but I can't switch panes or launch any programs from it. I did get into the terminal and made sure everything apt-get could update was up to snuff, but no change. 

Strangest part ~ when I plug in my 22'' monitor instead of my TV as a monitor and boot up everything launches in a decent resolution, but still an unresponsive Kickoff.

I have edited my grub settings to bot with nomodeset, it doesn't seem to change anything. 

I am more than happy to experiment here, cause I'd like to have a functioning computer. Also, with no usable GUI it makes it a little harder to do log dumps (obviously) but if there's anything specific I can look for I'll do it.

Specs: XPC Shuttle, Intel 930 core I7, 16GB Corsair 1333MHZ RAM, PNY GeForce 8600GTS 256MB

Thank you in advance, whoever can fix this!

---

