---
title: "Installation problems and busybox"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by MadScotty on 2009-03-11
I'm a linux newbie with an installation issue.

First, here's my system specs:

Intel Core 2 Duo
2 GB Ram
Asus mobo
Memorex DVDRW Drive
NVIDIA GeForce 7300
320 GB HD (200 GB partitioned NTFS for WinXP, and the rest is unpartitioned, set aside for ubuntu)

My problem:

Every time I try to install, either by running the liveCD first, or just simply selecting "install Ubuntu" from the screen that appears at boot, I get a splash screen with the ubuntu logo and a progress bar that bounces back and forth.  After about a minute or so, I am dumped into a busybox console.

I've done some reading, and tried certain things that have been suggested in other forums, namely setting SATA to RAID in BIOS, (which I didn't think would do anything, both my HD and DVD drives are IDE) and adding a all_generic_ide string to the boot options (f6).

I have burned 4 CD's (two of 8.10, two of 8.4) at slow speeds using infrarecorder in WinXP.  Each time I used md5sum to check the hashes of the ISOs, and they checked out.  Both versions give me this same problem.  Any help would be much appreciated.

---

### Post by Whitewater001 on 2009-03-11
Yeah, same if not similar problem here too...

I have burnt two copies of (as of what was on the main page yesterday) ubuntu, both giving the same prob.

Im getting the SRST failed (error = -16) error
but i get it when i try to install / run the live desktop from my sata DVD drive, 
every second time i try to run the live desktop from my ide dvd drive
and every time i try to boot from my sata drive that has (i hope) an installed version of ubuntu on it (i managed to get it installed by running the live desktop from my ide dvd drive, and installing from there, which, it seemed was all good, it installed to 100% onto my sata drive).

System specs if it helps:
amd 5200+
Gigabyte GA590-SLI S5
2Gig ram
x1950 pro
5 various sata HDD's
1 Sata Pioneer DVD drive
1 generic ide Drive

I have also tried just about every combination with my Sata settings in bios... but no help there.

I asked one of my good mates who has been using ubuntu for years how hard it was to install this, and he said easier than windows...
So yeah, I am about as noob as it gets (but well keen) :/

---

