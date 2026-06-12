---
title: "ubuntu hangs during installation"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by sunyudai on 2009-09-22
Hello,
I am attempting to install Ubuntu 9.04 on my previously windows only PC.

During the installation process, I get a black screen with the Ubunto logo and a progress bar, when the progress bar completes, I get an orange background looking screen and nothing else. Non responsive. (can't even get a caps-lock light on the keyboard)
Forced to hard-reset.


Hardware:
-Motherboard: ECS PM89OT-M
-Processor: x86 family 15 model 4 stepping 3 genuinintel ~3182 MHz
-Ram: 4 GB DDR2
-Hard Drive 1 (Original windows drive): Western Digital 250GB SATA Drive
     -Default XP Main+Recovery Partitions
-Hard Drive 2 (Going to be my OS Drive): Western Digital 250GB SATA Drive
     -Patitioned to 3 149 GB Primary partitions, all blank and unused.
     -Also contains 1 18.75 GB Secondary partition for later use as a paging file + MBR,   
           currently blank.

Process:
-Downloaded iso image for 9.04 from official site.
-ran the .iso chach checksum utility on the .iso image, checked out okay.
-burned to standard 700 mg CD-R
-Reset computer, booted from CD, ran the on-disk checking utility, checked out okay.
-exited disk and shut down.
-removed original hard-drive, attached new blank hard-drive, and attempted to installation. Got above result. Let it sit about half an hour, then hard-reset.
-Attached original hard drive in open sata port, booted into windows xp.
-initialized 2nd DH, and partitioned it to 3 primary partitions, 149 GB each, and 1 18.75 gb logical partition remaining.
-reset computer, booted into CD.
-ran on-disc checker again, checked okay.
-Attempted to install again, got same result as above, waited approx 1.5 hours, then hardreset to get hardware information for this post.

Resources I have checked:
Google:
"Ubuntu installation troubleshooting"
"ubuntu freezes during installation"
"ubuntu hangs during installation"
"Ubuntu 9.04 installation troubleshooting"
"ubuntu 9.04 freezes during installation"
"ubuntu 9.04 hangs during installation"
"ubuntu hangs on background screen during installation"
"ubuntu 9.04 hangs on background screen during installation"
This Forum: (Searched both installation help and beginners forum for all:)
-same searches as Google above.

None of these searches resulted in much that was relevent, although one post did suggest that the issue might be too much ram, and thus passing a parameter to the installer of "mem=512". I am unsure how to do this. 

Question:
Can some one give me any pointers as how to fix this, or at least get some feedback from the installer as to what it is trying to do that's causing an issue? 

Also, please let me know if more information is needed.

Thank you for your time.

---

### Post by yaroto98 on 2009-09-22
Are you running the 64 bit version of ubuntu?

If you're running the 32 bit version, i could see why it might hang on your hardware.

---

### Post by sunyudai on 2009-09-22
Ah, I had been trying to install 32 bit, I'm downloading 64 bit now, will post here with results later tonight (after work.)

Thank you. :)

---

### Post by sunyudai on 2009-09-23
No, does not appear to be the case, hangs at same point on 64 bit version as well.

I should probably also not that attempting to use the "Try Ubuntu without making changes to your PC" option also hangs at the same point, except that it does not load the pretty orange wallpaper-looking screen, instead loads a (functional) mouse pointer on a black screen.

Thanks anyway, I'll keep looking.

---

### Post by sunyudai on 2009-09-23
[solved]

Still unsure of what exactly the problem was, but a friend at work mentioned that I should try loading with the graphical safe mode on, which did the trick, I'm up and running.

If it matters to any later with the same issue, found under the F4 menu on the CD's main menu, prior to running installation.

Was running an nvidea 8400 series w/ dual monitor (although secondary was disconnected for install.)

Thank you for the help,
-Josh

---

