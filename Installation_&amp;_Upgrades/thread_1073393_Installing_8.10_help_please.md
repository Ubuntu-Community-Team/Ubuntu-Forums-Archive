---
title: "Installing 8.10 help please"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by gordoha on 2009-02-18
I have 6.06 or whatever it is on an old laptop.  I can not upgrade to 8.04, when I try, it says there is an error with the network or the server.

So, I download all the files for 8.10.  The question is, can I just run the install, or do I have to make a boot CD?

If a boot CD, how do I do that?  I have a CD-R, and a blank CD somewhere..; the problem is that I don't know how to take those files and put them on the CD in ubuntu.. thanks

---

### Post by hopikrishnan on 2009-02-18
> **gordoha said:**
> I have 6.06 or whatever it is on an old laptop.  I can not upgrade to 8.04, when I try, it says there is an error with the network or the server.

So, I download all the files for 8.10.  The question is, can I just run the install, or do I have to make a boot CD?

If a boot CD, how do I do that?  I have a CD-R, and a blank CD somewhere..; the problem is that I don't know how to take those files and put them on the CD in ubuntu.. thanks

Hello Gordo,  "whatever it is" on the old laptop -- need to be able to burn an iso image using a software that usually does that sort of thing.  You might find it somewhere on the menu  of that 6.06 thing.  If you have made any CD's using that old laptop, then you are Ok to go ahead.  You do not need to download "all the files" for 8.10.  You need to download only ONE large file that ends with the extension ISO.  Go to the ubuntu download site and see what to download and how to burn an ISO file into a LIVE BOOT CD.  Unless people in the forum know what that old laptop is, there is no telling whether or not you can succeed in this upgrade. However, you can do this at the cost of a CD media and some time messing with the computer.   Good luck.

---

### Post by gordoha on 2009-02-18
OK, I downloaded the big ISO file on another computer and burned it to a CD.  When I put it in the laptop that I want to have ubuntu, it just wants to unpack the ISO file into other files.  now what?

---

### Post by dstew on 2009-02-18
You can't just copy the .iso file to a CD, you need to burn it as an image. See [this How-To]("https://help.ubuntu.com/community/BurningIsoHowto"). Once you have the CD image, you need to make sure your BIOS is set to boot the CD. Look at the first screen that comes up when you turn on your computer, it might tell you what key to press to get into your BIOS to change the boot disk options. Often it is F2 or F10.

---

### Post by Therion on 2009-02-18
> **gordoha said:**
> OK, I downloaded the big ISO file on another computer and burned it to a CD.  When I put it in the laptop that I want to have ubuntu, it just wants to unpack the ISO file into other files.  now what?
When you burn the .iso file you downloaded, you need to burn it to a CD or DVD as an *image file*.  If you burn the disc and see only one file (ending with a .iso extension) you have not burned the disc correctly and you won't be able to boot from it.

See this tutorial:  [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by gordoha on 2009-02-18
thanks, i got it! had to change bios.. seems to be installing.  thank u everybody!

---

