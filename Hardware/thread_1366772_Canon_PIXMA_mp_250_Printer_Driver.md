---
title: "Canon PIXMA mp 250 Printer Driver"
date: 2009-12-28
forum: Hardware
---

### Post by vchapman on 2009-12-28
Where can I find a driver for this printer?

If there is one available, how do I install it.

TIA.

---

### Post by spyderpride on 2009-12-28
[http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&binning-state=model%3d%3dPIXMA%20MP250%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&](http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&binning-state=model%3d%3dPIXMA%20MP250%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&)

32-bit debs, currently working perfectly for me in Karmic.

---

### Post by vchapman on 2009-12-28
> **spyderpride said:**
> [http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&binning-state=model%3d%3dPIXMA%20MP250%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&]("http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&binning-state=model%3d%3dPIXMA%20MP250%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&")

32-bit debs, currently working perfectly for me in Karmic.

Thank you. 

Which one of the 6 packages do I download and *then* how do I go about installing it. 

I need some gentle hand holding help with this. Thank you.:smile:

---

### Post by spyderpride on 2009-12-29
If I remember correctly, you just download the first one which is a couple of .deb files for the driver.  There is another set of .deb files for scangear, which only allows you to scan in GIMP.  I got scanning working in xsane, but that required building from the latest sane-backends.  Whole 'nother can 'o worms, so I wont get into that now (its a good learning experience though).

The way DEB files work is that you just download them and double-click them, which opens up gdebi.  From there you just click "Install" then enjoy.

For this particular situation, you get 2 debs and a script in a tarball.  You may be able to just install the debs directly, but I used the script which may actually be required. Extract the whole folder into your home directory.  Fire up a terminal, 

cd cnijfilter-mp250series-3.20-1-i386-deb
./install.sh

Not sure if it requires root privileges, just add sudo before the ./install.sh if it does.

Good luck.

---

### Post by vchapman on 2009-12-29
Thank you for your assistance. I now have a working printer.

---

### Post by spyderpride on 2009-12-29
No problem, glad I could help.

[http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html](http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html)

That is how you get the scanner working.

---

### Post by pirogueguy on 2010-01-16
Hi spyderpride and vchapman, I have a question about your Canon PIXMA mp 250 install.  I referenced your thread, and downloaded and installed the driver.  Everything appears to have worked properly.  I can see the installed package through the Synaptic Package Manager as well. 

However, when I go to 'add a printer' and pick from the list of print drivers, the pixma 250 is not there.  Have I missed a step to add this?  I have restarted but that did not make a difference.  Any words of wisdom would be appreciated!  

One other note, I'm printing to a shared printer on a windows pc using SAMBA - I don't know if this would make any difference.

---

### Post by spyderpride on 2010-01-18
I could be wrong, but I think if you are using a network printer that you do not need the driver on the "client" machines, just the "server" machine.  The key is to make the printer visible from windows to ubuntu, something I have struggled with in the past.  So, if I am right, your issue is a samba network printing issue and not a driver issue.

---

### Post by pirogueguy on 2010-01-22
Thanks for the reply spyderpride!  I'll dig in and do some more research focused in the Samba direction now!  Thanks!

---

### Post by rainforrestguy on 2010-08-31
I tried the posted site and it is no longer there, is there anywhere else I can find it or is there something else I can do to get my canom pixma mp250 working on ubuntu 10.04 lucid lynx?

---

### Post by nnebular22 on 2010-09-11
well.... any answers?

this is frustrating.  i've been trying for almost 2 months with no success.

---

### Post by eiolv on 2010-09-16
The drivers can be found at [http://support-au.canon.com.au/contents/AU/EN/0100236101.html]("http://support-au.canon.com.au/contents/AU/EN/0100236101.html"). The printer now works fine for me on Lucid Lynx. 

I can however not get the scanner working. I tried the link posted above [http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html]("http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html"), but get stuck because "Access to resource has been denied", and I cannot find the file /etc/udev/rules.d/40-basic-permissions.rules where I'm supposed to change the user permissions. 

Has the basic permissions been moved on this version of Ubuntu?

---

### Post by eiolv on 2010-09-18
I found a solution to my above stated question on the following post [http://ubuntuforums.org/archive/index.php/t-166944.html]("http://ubuntuforums.org/archive/index.php/t-166944.html")

What I did (in case someone should wonder) was typing lsusb, resulting in the following:

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04a9:173a Canon, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

As the scanner is the Canon, Inc. with bus number 001 and device number 002, I then typed the following:

sudo chmod a+w /dev/bus/usb/001/002

This solved the problem; both printer and scanner is working.

---

### Post by harbhag on 2010-09-23
I have posted a complete tutorial to get canon pixma mp250 printer scanner to work on Ubuntu. Check out the link below

[http://harbhag.wordpress.com/2010/04/09/canon-pixma-mp258-or-any-mp250-series-printer-on-ubuntu-debian-fedora-and-arch-linux/](http://harbhag.wordpress.com/2010/04/09/canon-pixma-mp258-or-any-mp250-series-printer-on-ubuntu-debian-fedora-and-arch-linux/)

---

### Post by aspiannur41 on 2011-03-09
Page no found,can you give me other adress or other way to install canon pixma mp 250 driver ?

---

### Post by ParadoxBlue on 2011-03-20
> **aspiannur41 said:**
> Page no found,can you give me other adress or other way to install canon pixma mp 250 driver ? This link [http://ubuntica.com/pixma-mp250-on-ubuntu.html](http://ubuntica.com/pixma-mp250-on-ubuntu.html) did the job for me. Printing and scanning functions seem to work quite well on my system running Lucid 10.04. I'm not sure if the links to the Canon driver pages still work but if not let me know. I've saved all the files needed for installation and I can send them to you. Good Luck!

---

### Post by daniroma on 2011-05-01
Yes. [http://ubuntica.com/pixma-mp250-on-ubuntu.html](http://ubuntica.com/pixma-mp250-on-ubuntu.html)
This working for me too on Lucid 10.4
Tip: after downloading files, just install necessary drivers (click on **.deb** files) from  /yourdownloadingfolder/cnijfilter-mp250series-3.40-1-deb/packages/
Tank you ParadoxBlue.

---

