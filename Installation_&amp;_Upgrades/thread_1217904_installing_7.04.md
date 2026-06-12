---
title: "installing 7.04"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by dport on 2009-07-20
Ok, so long story short I upgraded from 8.10 to 9.04 and had issues with my graphics ever sense, tried doing a bunch of things to fix it and attempted to update my graphics driver. Didn't work, and now i've had nothing but problems with my computer. I lost my 8.10 install disk and so i'm using a 7.10 CD and then plan on only updating to 8.10. Well the problem lies in once i start installing the OS. I boot into a live CD and start the install, gets to about 45-50% done and then comes up with an error of:

> The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.

I know when I went to upgrade my graphics card driver NVIDIA had to build its own kernel, could that have messed something major up on my computer? ever sense I updated the driver the driver wouldn't work at all on the computer.

Any help on figureing this out? I really don't want to load into a live user session every time.

---

### Post by Partyboi2 on 2009-07-20
Hi, check the cd for scratches and if you have a spare cd/dvd around try burning a new copy. I  have had a similar problem in the past which was fixed by burning another copy.

---

### Post by presence1960 on 2009-07-20
boot the live CD and choose "try ubuntu without any changes to your computer". Once the desktop loads open a terminal and run ```
ubiquity --no-migration-assistant
``` I saw that on a thread and tried it on a friend's machine when I ran into that same error message. It worked. The command will spawn the installer, but for some reason I didn't get that Errno 5 error that time.

If the code doesn't work without sudo just rerun it by putting sudo at the beginning of the command. I can't remember if that was necessary or not.

---

### Post by dport on 2009-07-20
I'll find a CD and try to download 8.10 like I want, I tried the code, both with and without sudo and it still fails. :-\

Any other ideas will be appreciated.

---

### Post by slakkie on 2009-07-20
You can check the integrety of your disk before launching the install. See if that helps..

---

