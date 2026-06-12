---
title: "How do I flash my bios?"
date: 2016-07-08
forum: Hardware
---

### Post by Evil Wayz on 2016-07-08
I have a rather old computer running 16.04 on it. Some recent issues made me go into the bios and found that it's about ten years old.  There is a newer bios that is only 5 years old, and I would like to try that before I start messing around under the hood.  Only I'm not sure how to go about it.  The new bios is in the form of an exe  file, and I assume its an archive file and an executable.   Would I use WINE to do this?  Or is there a way I can unpack it and flash?

---

### Post by squirrel3 on 2016-07-08
I would NOT use Wine to flash a bios because it could crash your computer rendering your computer useless. Furthermore, I don't think that updating the BIOS will benefit your computer.

---

### Post by deadflowr on 2016-07-08
Easiest way on Linux is to use a flash drive and usually put freedos on it and the bios file.
Then boot that. You need to know little dos so you can navigate to the file correctly.
I found unetbootin to be pretty easy to install a functional freedos with.

Of course the overall easiest method is to be using Windows.
The file is usually executable from within windows without all the hassle.
(Blame that on the wayward support hardware vendor give to linux)

Beyond that, without knowing much about the hardware at hand I can only point you towards this page:
[https://help.ubuntu.com/community/BIOSUpdate]("https://help.ubuntu.com/community/BIOSUpdate")

If nothing more, I hope it's a good starting point.

Good luck, in which ever direction you go.

---

### Post by Evil Wayz on 2016-07-09
Of course I have the computer that the company is actively blocking users from browsing to the support section. FML.

---

### Post by weatherman2 on 2016-07-09
It's dangerous to try to flash the BIOS from an exe file without using Windows directly.  You could easily brick your computer with a bad BIOS flash.  I wouldn't attempt using the USB flash drive method unless you really know what you are doing.  

A newer BIOS can fix some issues, but unless you have specific issues you are trying to fix, I wouldn't bother.  Sometimes BIOS updates don't fix anything you care about.  They may add the ability to run newer CPUs that you don't have.  They may fix very minor issues that don't concern you or even fix messages.

If you have access to any sort of windows installer disk and perhaps a spare hard drive, you could install Windows temporarily on it even without a product key.  You only need to boot Windows and run the exe file to update the BIOS and don't need to activate Windows to do that.

---

