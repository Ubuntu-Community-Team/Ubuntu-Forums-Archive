---
title: "Usb 3.0 external hard drive crashes ubuntu when plugged into usb 3.0 port"
date: 2011-06-19
forum: Hardware
---

### Post by kimangroo on 2011-06-19
I bought this Iomega prestige 1 tb usb 3.0 portable external hard drive from amazon, but am having problems in natty.

First off when I plugged it with windows, I noticed a virtual cd with Iomega software and a hard drive icon came up. Well I don't want the Iomega software so I booted up Ubuntu to format the drive and get rid of it.

However when I plugged the drive in in Ubuntu it just hard crashed, gave me a black screen with a lot of esoteric writing on it.

I then rebooted Ubuntu with the drive plugged into a usb 2.0 port and it worked but with the virtual cd and the harddrive seperate again.

So then I thought this cd thing might be the cause of the crash and ran partition editor, to try and repartition the drive. This time gparted only saw one hard drive with one partition and a bit of empty space at the end. I deleted the partition and created a new one using up all the space this time, minus 1 or 2 megs on either end.

However, this hasn't solved a thing, I still have the virtual cd and the hard drive seperate, and ubuntu still dies a horrible death the second I plug the drive into the usb 3.0 port...

So does anyone know how to get rid of the virtual cd, and how to make this work with usb 3.0 in ubuntu?...

Thanks!

---

### Post by kimangroo on 2011-06-24
Well I ended up returning the drive because on windows chdsk revealed a shed load of bad sectors and other errors.

On the replacement drive, I was able to solve part of the problem by deleting the virtual cd partition using an updated Iomega utility 1.3.

This has removed the virtual cd in both windows and ubuntu, however ubuntu now just won't recognise the drive when plugged into a usb 3.0 port... which I've posted about in[ another thread]("http://ubuntuforums.org/search.php?searchid=81679099").

---

