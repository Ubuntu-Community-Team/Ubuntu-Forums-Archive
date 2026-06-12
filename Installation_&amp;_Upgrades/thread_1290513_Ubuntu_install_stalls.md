---
title: "Ubuntu install stalls"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by janosm on 2009-10-13
I'm trying to install Ubuntu 9.04 and it stalls after the select region and city screen. I can boot to the CD okay but it won't install. The computer is an older Compaq laptop

---

### Post by presence1960 on 2009-10-13
what are the specs on your machine?

---

### Post by janosm on 2009-10-13
Compaq nx6310 - Celeron - 1Gb ram - new 160Gb HDD. The disk currently has Win7 on it. It however boots fine to the live CD

---

### Post by presence1960 on 2009-10-13
> **janosm said:**
> Compaq nx6310 - Celeron - 1Gb ram - new 160Gb HDD. The disk currently has Win7 on it. It however boots fine to the live CD

Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso you downloaded?

If the hashes match exactly your iso is good. If they do not match exactly your iso is corrupted. Try downloading the iso from a torrent rather than a direct download mirror.

Burn the iso to CD as an image at 4x-8x speed. 

Boot the CD and choose check disk for defects prior to trying to install or choosing "try ubuntu without any changes".

If all else fails try the alternate text based installer. Get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

---

### Post by janosm on 2009-10-14
I've use the same ISO to create a virtual linux so I am happy that the ISO is okay. I've booted to the "without any changes" and that came up okay. I've noticed that somebody else had the same problem back in May but there was no resolution. I'm checking the disk now. Would the alternative make any difference? I thought because I get the desktop that it wasn't a graphics problem.

---

### Post by presence1960 on 2009-10-14
> **janosm said:**
> I've use the same ISO to create a virtual linux so I am happy that the ISO is okay. I've booted to the "without any changes" and that came up okay. I've noticed that somebody else had the same problem back in May but there was no resolution. I'm checking the disk now. Would the alternative make any difference? I thought because I get the desktop that it wasn't a graphics problem.
The alternative installer works a lot of times where the Live CD does not.

---

### Post by janosm on 2009-10-14
Solved it. As I knew that the next step was the keyboard selection stage, I wondered if it was having problems querying the keyboard. I stuck a USB keyboard into the laptop and it managed to carry on.

---

### Post by Greg Xix on 2009-10-14
I would HIGHLY recommend that you install from a LIVE USB drive instead of a CD. I too had issues with CD/DVD installs. But USB has always worked great and my installs generally take around 10-15 mins using an old 1gb-USB 1.1 Flash drive. This all depends if your computer has USB bootable capabilities of course.

I can post a simple crash course on how to make a Live USB upon request. :guitar:

---

### Post by janosm on 2009-10-14
> **Greg Xix said:**
> I would HIGHLY recommend that you install from a LIVE USB drive instead of a CD. I too had issues with CD/DVD installs. But USB has always worked great and my installs generally take around 10-15 mins using an old 1gb-USB 1.1 Flash drive. This all depends if your computer has USB bootable capabilities of course.

I can post a simple crash course on how to make a Live USB upon request. :guitar:

Please do. I do windows support and use a boot repair USB all the time now. Very few computers will not boot to a USB.

---

