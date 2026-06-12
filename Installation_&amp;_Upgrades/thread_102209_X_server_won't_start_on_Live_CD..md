---
title: "X server won't start on Live CD."
date: 2005-12-11
forum: Installation &amp; Upgrades
---

### Post by tsiMental on 2005-12-11
Hi,

I tried to boot into Ubuntu from the 64bit LiveCD - When it tried to start the X server I got a message that X - can't start...

Then I tried the x86 32bit LiveCD and the exact same thing happened.

My hardware is:
AMD64 Venice 3000+ (socket 939)
DFI Lanparty UT nF4 SLI-D (PCI-E)
1GB DualChannel RAM
Sapphire ATI X700PRO 256MB

Dell 2405FPW LCD (1920x1200) on DVI
USB keyboard and mouse

Is there any reason why the ubuntu X-server wouldn't work with this hardware?

---

### Post by tsiMental on 2005-12-11
Just tried the Knoppix 4.0 Live CD, and this version works fine. Except it doesn't recognize the video/display-adapter and hence uses the vesa module.

---

### Post by Tim_Olaguna on 2005-12-12
First, a description of my system:  

•	HP Pavilion 514n PC, 
•	1 GB of RAM, 
•	Celeron processor running at 2.2 GHz, 
•	ATI Radeon 9250 graphics card,
•	Two internal Seagate physical hard drives:
o	The first a 60 GB hard drive supporting Windows professional XP, 
o	The second a 200 GB hard drive initially formatted as NTFS but subsequently reformatted to support fat and Linux partitions

I want to set up a Linux subsystem in order to support my web server development work.  I initially downloaded an ISO image of SimplyMEPIS, burned it to a CD, used its included utility “QTParted” to set up the required Linux partitions on my second hard drive, and installed and operated the software for a few days.  So I know I can install and operate a dual boot system.  I have also successfully downloaded and installed Knoppix 4.0.2, but would prefer a distro which easily provides Gnome.

I had the same experience you had.  The live CD boot fails when trying to start X Windows.  Another disappointing distro that will not perform as alleged.   I guess I will need to move on to try another.

---

