---
title: "Digital Camera Advice PTP vs. UMS"
date: 2006-09-04
forum: Hardware &amp; Laptops
---

### Post by rmjb on 2006-09-04
Hi, I'm looking to finally getting a proper digital camera. In my research I noticed that a lot of cameras support PTP (Picture Transfer Protocol) and libgphoto2 provides this functionality in Ubuntu. Infact, my current camera, a hacked Dakota Digital Single Use Camera from Ritz Digital works great; when I plug it in Ubuntu tells me it detected a camera and do I want to see the photos on it to import. I'm guessing this is how all PTP cameras work.

However, how does a USB Mass Storage camera work in Linux? Will it just mount the camera as another mount point and I'll have to start my photo manager? Or will gphoto and gThumb automatically detect it's a camera and launch?

To see what camera is what you can check here:
[http://www.teaser.fr/~hfiguiere/linux/digicam.html](http://www.teaser.fr/~hfiguiere/linux/digicam.html)
There's a list at the bottom of the page.

- rmjb

---

### Post by jpkotta on 2006-09-04
I have a Sony DSC-W30.  It has several transfer options: PictBridge, PTP, Mass Storage, and Auto.  The only one that has worked for me is PTP.  I use gthumb to transfer pictures, because it was the first thing I tried that worked.  I've tried setting it to mass storage, and it comes up in lsusb, but I can't mount it like a USB drive. It doesn't show up in /dev/ like my key drive.

---

### Post by jpkotta on 2006-09-04
I got curious about this, so I searched some more.  I'd really like to get my camera to look like a drive, but it looks like support for this is a per-camera thing.  Some older Sony cameras (and others) work fine as a mass storage device, but it's certainly not consistant.  In other words, some camera maufacturers are lazy and don't implement the protocol properly, and don't care if it doesn't work on Linux.  The only way you can know for sure is if someone else has gotten it to work (of just try it yourself).

---

