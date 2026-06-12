---
title: "Can I install image from CD?"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by markw10 on 2009-05-11
I am ready to install Ubuntu Netbook Remix on a Netbook. I have downloaded the image and realize that it is supposed to be burned to a USB Flash Drive.
My question:  Since I have an external Optical DVD Drive that I can plug into the netbook and my USB Flash Drive is not big enough for the image, can I just burn that image to a DVD to install UNR?  
If not, is there an image available that is meant to be burned to a DVD?

---

### Post by lisati on 2009-05-11
If it's an "ISO" file, it can usually be burned to a CD (if it fits) or a DVD. Remember to burn it as a disk image, not as a file.

---

### Post by logos34 on 2009-05-11
The [UNR .img]("https://help.ubuntu.com/community/Installation/FromImgFiles") is designed for USB flash.  For dvd I believe you need[.iso format]("https://answers.launchpad.net/ubuntu/+question/70261"). AFAIK there's no iso yet for 9.04 Jaunty (only [Hardy]("http://oem-images.canonical.com/unr/"))

Convert it to iso with ccd2iso or similar program. Then burn to dvd as an *image.*

If you have a ubuntu live cd, you could boot that, install [ccd2iso]("https://help.ubuntu.com/community/ManageDiscImages#Usage") (enable Universe repos in Synaptic if necessary) and convert it. 

[https://wiki.ubuntu.com/UNR#Downloading%20&%20Installing%20the%20UNR%20Hardy%20Image](https://wiki.ubuntu.com/UNR#Downloading%20&%20Installing%20the%20UNR%20Hardy%20Image)

---

