---
title: "Failed manual partition Ubuntu 9.0.4"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by notquitestr8t on 2009-08-05
Installed a  brand new 1TB drive. Nothing else is on it and I'm attempting to install Ubuntu 9.0.4-64 When I tried a manual partition the formatting fails at 5%. If I allow an auto format, it only gives Ubuntu 2.5 GB and any updates fail due to lack of disk space. 
The manual install attempted is
16 GB for swap (I have 8 GB of physical ram)
15 GB for Ubuntu / or root
The rest for /home

The failure is always on the /home partition. What am I doing wrong?:(

---

### Post by Possum Films on 2009-08-05
Are you formatting the drive from within the Ubuntu installer? You might want to try formatting the disk from GParted (System > Administration > Partition Editor). Even if it still fails you should at least get a more detailed error report. 

Also, there is the possibility that there are problems with the hard disk you are using. Since it's brand new if there are any problems with it they should be covered under warranty. 

I hope this helps.

---

### Post by slowMX5 on 2009-09-03
This is my first post. I have recently had windows blue screen on me in a major kind of way so have purchased a new HDD and want to take the opportunity to take the plunge into the world of ubuntu.

I've copied the .iso file to CD and tried to setup ubuntu but have come up against the same issue as the original poster here. I've tried to use partition editor but in the install crashes/freezes so have not learnt anything. :confused:

Can someone help? I don't want to fall at the first hurdle and give up on ubuntu this early!

Edit: This is on a Dell Dimension 8400 machine.

---

### Post by Bucky Ball on 2009-09-03
> **slowMX5 said:**
> This is my first post. I have recently had windows blue screen on me in a major kind of way so have purchased a new HDD and want to take the opportunity to take the plunge into the world of ubuntu.

I've copied the .iso file to CD and tried to setup ubuntu but have come up against the same issue as the original poster here. I've tried to use partition editor but in the install crashes/freezes so have not learnt anything. :confused:

Can someone help? I don't want to fall at the first hurdle and give up on ubuntu this early!

Please post a new thread with a descriptive title rather than crash this one. You will get more specific help that way. The title of this post deals specifically with the OPs problem, not yours. 

When you have done so post a link back here if you like. It causes great confusion if people start posting separate problems on one thread. 

:)

---

### Post by drs305 on 2009-09-03
> **notquitestr8t said:**
> If I allow an auto format, it only gives Ubuntu 2.5 GB and any updates fail due to lack of disk space. :(

This is a bug that is actively being worked on. When you get to Step 4 and select "side by side", you must then click on the partition bar depiction at the bottom. This will activate a slider so you can set an appropriate size.

The default was supposed to be about midway between 2.5GB and the available space available, but it currently defaults to 2.5GB.

Here is a small post about how to prevent the 2.5GB install:
[2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271#post7658271")

---

### Post by slowMX5 on 2009-09-03
I wasn't intending to 'crash' the thread as I felt that the problem appeared identical and it was natural follow on question after the 1st reply. I'll start a new thread - not sure which sub-forum though.

---

### Post by Bucky Ball on 2009-09-03
Just one thing: You do not need a /swap anywhere near 16Gb. With 8Gb of RAM you are going to go nowhere near /swap anyway and could probably safely run without one! (although not advisable). Usually recommended 2Gb max, regardless of amount of RAM (although the debate continues). Don't relate your thinking to the Windows idea of 'twice the RAM'. ;-)

Also:

/
/home
/swap

... is the best order to have them in. / is then on the fastest part of the drive with /home on the second fasted and a 2Gb /swap on the slowest. :)

---

### Post by notquitestr8t on 2009-09-04
Turns out I had a bad drive. I downloaded the drive utilities from the West Digital and verified it was bad. Once I returned it for a good one, I was OK except for the bug shown in this thread.

---

