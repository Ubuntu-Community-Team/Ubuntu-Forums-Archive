---
title: "Help with xawtv"
date: 2006-03-09
forum: Hardware &amp; Laptops
---

### Post by Princey on 2006-03-09
I'm trying to get my logitech webcam messenger installed using the thread located at [http://www.ubuntuforums.org/showthread.php?t=126053]("http://www.ubuntuforums.org/showthread.php?t=126053") but I am stalled at installing xawtv. When I type in:

sudo apt-get install xawtv gcc-3.4 

I keep getting the error message : 

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xawtv

I've checked adept and synaptic and they report it being installed namely with liblircclient0, libmjpegtools0 and mjpegtools. Is that just it:-k or is something else missing? Any help will be appreciated. I've been fighting with this for over a week now.

---

### Post by retsaw on 2006-03-10
Have you enabled the Universe repositories?

You can do this using Adept.  Go into the Adept -> Manage Repositories menu item.  You will then get a list of your repositories, you will see a few lines that have Universe in the components column, if they are grey then they are disabled, right click on these lines and select Enable for each of them, then click Apply at the bottom, then click Fetch Updates to get an updated list of packages, when this is done you should be able to install xawtv.

---

### Post by Princey on 2006-03-11
[QUOTE=retsaw]Have you enabled the Universe repositories?

You can do this using Adept.  Go into the Adept -> Manage Repositories menu item.  You will then get a list of your repositories, you will see a few lines that have Universe in the components column, if they are grey then they are disabled, right click on these lines and select Enable for each of them, then click Apply at the bottom, then click Fetch Updates to get an updated list of packages, when this is done you should be able to install xawtv.[/QUOTE]

Thanks. I deleted all of my entries in my sources.list and restored the original I had backed up. That worked but I'm still having problems setting up my camera. Strange thing is I read in the forums that persons with exact models like mine get theirs working. One difference is that they're running gnome, not kde like I'm doing. Should that make a difference? My lsusb reveals exact models as even one of those writting the thread. 

princey@MCES:~$ lsusb
Bus 002 Device 003: ID 0458:2014 KYE Systems Corp. (Mouse Systems)
Bus 002 Device 002: ID 03f0:0604 Hewlett-Packard DeskJet 840c
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 046d:08f0 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000

I've reformatted and started with a clean install. Done everything step by step, but still stuck.:???: :???: :???:

____________________________________________________________________________________
Edit:

Got it to work finally.

---

