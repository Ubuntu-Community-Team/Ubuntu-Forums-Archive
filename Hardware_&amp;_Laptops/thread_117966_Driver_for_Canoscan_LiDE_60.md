---
title: "Driver for Canoscan LiDE 60"
date: 2006-01-15
forum: Hardware &amp; Laptops
---

### Post by mikemain on 2006-01-15
Is there a driver for my scanner CanoScan LiDE 60?  I have just installed Ubuntu 5.04 and it recognises the scanner through the USB but doesn't seem to know how to drive it.
Keep it simple, I am new to this! :)

---

### Post by Sef on 2006-01-16
Found this about getting your scanner to work under Linux:

> Update

As at 22nd December 2005 the LiDE 60 works with the latest version of SANE (1.0.17). Support is not enabled by default in Debian Unstable (sid)! The steps to get an LiDE60 working are:
Install the SANE libraries and a suitable scanning application (xsane is popular):
# apt-get install libsane xsane
Edit the file '/etc/sane.d/hotplug/libsane.db' and add the lines:
# Canon Inc.|LIDE 60
0x04a9 0x221c root:scanner 0664
(This makes the hotplug system recognise the PCI ID of the LiDE60.)
Restart the hot plug system to pick up the change you just made:
# /etc/init.d/hotplug restart
Plug in your LiDE60 and start xsane. Xsane should detect your LiDE60 and you should be able to scan documents with it under Linux.

I suspect LiDE60 support won't be enabled by default until libsane has had more testing with the LiDE60. LiDE60 support in SANE is brand new, and hasn't widely used (yet)

Link:  [http://john.daltons.info/lide60/]("http://john.daltons.info/lide60/")

---

### Post by mikemain on 2006-01-16
Whoa!  After learning how to edit files in Linux (I really am a beginner at this) I found what seems to be the equivalent file as the path quoted didn't exist.  Made the changes but still won't work.  May have to wait for lisbane to do it for me.

Time to visit the beginner forum........

---

### Post by bluetoad on 2006-04-07
It now works in Breezy using the drivers from Dapper.  See 

[http://www.ubuntuforums.org/showthread.php?t=153933&highlight=LIDE+60](http://www.ubuntuforums.org/showthread.php?t=153933&highlight=LIDE+60)

---

