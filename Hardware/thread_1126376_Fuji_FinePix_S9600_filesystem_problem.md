---
title: "Fuji FinePix S9600 filesystem problem"
date: 2009-04-15
forum: Hardware
---

### Post by ClemRutter on 2009-04-15
I use Hardy and the Fuji camera. It has a 2G xD card which shows up on desktop as 565.3 MB Media with a usb symbol in its icon. Over the last 18 months I have copied about 5000 images from here , by opening that folder and select and dragging them to named folders on Desktop.

Sunday, I repeated the process. It started and after downloading 471 of 608 it stopped and reported an 200 I/O error. I tried the process on a Windoze machine and it stopped at the same point. I didn't panic- I know that on Linux this is a challenge not a problem. I unplugged the camera and saw one of the missing photos- in fact I can see all of the photos on the camera, and even take more. 

So it looks if the camera is blissfully working using its own OS, but the VFAT directory corrupts on image 472. So it looks if the first few byte of the card are blown- I must have been working them too hard.

I have fiddled around with dd fsck testdisk with zero success. I have bought a Mikomi 56-1 reader in case that helps but I really need a working xD so I can check that it is working. 

So now I need some heavy duty hints on how to find the drive. How to use the tools to recover the remaining images or the last 125 or so. And like the card my memory function isn't a reliable as it was when I first used a Unix terminal 20 years ago. So don't omit the basics.

---

