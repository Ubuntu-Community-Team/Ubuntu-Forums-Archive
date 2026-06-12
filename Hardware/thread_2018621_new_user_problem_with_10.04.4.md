---
title: "new user problem with 10.04.4"
date: 2012-07-06
forum: Hardware
---

### Post by Lewjay on 2012-07-06
Spent most of yesterday trying to get Ubuntu to work on my Dell Latitude D610.I had loaded 8.04 on it with no problem.  Tried to later load 12.04 but it would never complete the load.  Got the beginning screen, little lights going from white to red then nothing.   so I downloaded and burned 10.04.  It would not work either.  Tried Fedora 17 same problems.  Finally was able to repartion and wipe the hard drive and try to install 10.04 again.  Kept getting error about couldn't read file:  You need to load the kernel first.  
Somehow it finally loaded and worked.  So I was up till midnight, adding some of the apps, setting up Firefox, etc.   Shut down and went to bed.

Now trying to  play with the laptop again and getting the same error message"
Error: couldn't read file
Error: you need to load the kernel first.   
Failed to boot both default and fallback entries.
Press any key to continue.

What is going on.  I am not a Unix/Linux programmer, just trying to be a user.

---

### Post by Lewjay on 2012-07-06
Ok, I tried the live version and loaded boot repair.  I purged and replaced the kernel and when I rebooted I got the errror: Loading Linus 2.6.32-41 generic...
error: couldn't read file.
Loading initial ramdisk
error: you need to load the kernel first
Press any key to continue.....

the log info is [http://paste.ubuntu.com/1078755/](http://paste.ubuntu.com/1078755/)

---

### Post by Lewjay on 2012-07-07
Ok, I finally got this problem licked.  Browsed thru the forums and found something. Created the boot disc on my USB and it started and saved the 10.04 version.  Was able to reinstall it and it worked now doing updates but I downloaded the 12.04 to my USB and will install it from the USB.  :popcorn:

---

