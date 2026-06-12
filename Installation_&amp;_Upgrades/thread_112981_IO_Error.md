---
title: "I/O Error ?"
date: 2006-01-05
forum: Installation &amp; Upgrades
---

### Post by ronlondre on 2006-01-05
I am at the point in the installation process where the packages are being installed. I have had to install them after reboot due to either a lack of room on my HD or problems reading the disc; I don't know which it is.

Now I am receiving I/O error on device hda (sector etc...)

Is this a problem with the iso image on the disc, a problem with my HD, or what?

Any advice would be appreciated

---

### Post by hod139 on 2006-01-05
Before guessing, could you post the exact error message?

---

### Post by ronlondre on 2006-01-05
I stopped the process, however, I received multiple error messages during the downloading of the packages from the disc prior to them actually being installed (I think).

They were short error messages that continually poped up toward the end of the downloading process.
To the best of my knowledge they read:

I/O error on device hda (Sector 29xxxxxx)

---

### Post by hod139 on 2006-01-05
I would sugest burning a new cd (a slower burn speed sometimes helps) and try the install process again.  Make sure you format the partition that you will be installing ubuntu on, and write down any error messages that appear and when they occured.

---

### Post by ronlondre on 2006-01-05
I have burned a new CD and am installing the packages.  The installation proccess is at 5% and remains at 5% while it is downloading files, a total of 850.  At around file 100 or so files downloaded, I receive the following errors:

[928.175000] Buffer I/O error on device hdc, logical block 291648
[4295257.541000] Buffer I/O error on device hdc, logical block 282862

Again when the process is near 840 files downloaded I get a large amount of the same errors with different beginning numbers and different logical block numbers, then the process simply continues to run giving me more errors.

---

### Post by ronlondre on 2006-01-05
Now finally after reporting a number of I/O errors the instalation process is at 57% and stalled while preparing to configure slocate. Finally, I receive notification of installation error. The error suggests that either there is too little space on the HD (unlikely) or there are other problems.

Advise Please?

---

### Post by Ocxic on 2006-01-05
possible Problem's:1st. RESET BIOS, and check settings. Then retry using the device. If the device is still not functioning properly check the following......

2nd. hdc drive is going to die, check and replace if nessasary replace. 
3rd. another drive in the sytem could be dieing and causing problems, check and/or replace if nessasary. 
4th. IDE cables/power cable bad/defective/notseated properly, check and replace if older then 3-4 yrs with 80-Conductor cable. 
5th. At worst you're IDE controlly is dieing, get a new motherboard. 

TIP: Try reformating the drive, if that doesn't work do a zero fill,
and if that still doesn't work do a low level format (WARNING: A LOW LEVEL FORMAT WILL VOID YOU'RE WARRENTEE.)
if a low level format does not fix your drive then it is prolly going. (most companies offer a diagnostic utility for there drives check you manufactures website)

---

