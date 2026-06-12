---
title: "Problem installing Epson V30 Scanner on 9.04"
date: 2010-03-02
forum: Hardware
---

### Post by wonkyuk on 2010-03-02
I have just received an Epson V30 flatbed scanner. I bought this as many people online seem to have had an easy time installing the scanner and getting it to work.

I went to the avasys site and downloaded the two debian packages for iscan and drivers for the scanner and they installed perfectly it seems. I also added "epkowa" to the dll.conf file as instructed.

lsusb can see the scanner but sane-find-scanner does not. So the end result is that iscan, xsane, gimp etc cannot see the scanner. I have ensire permissions to the drivers and conf files associated witht he install are available and created a scanner group and assigned my user name ot that group too. Sadly, none of this works. It is the same problem -- sanhe just cannot see any usb scanner even though lsusb does.

So I am guessing the it is not a permission issue. It is something in the way SANE is configured that it does not see this particular scanner on this machine. any suggestions?

thanks!
M

---

### Post by ellgor on 2010-03-03
Hi,

There was a dodgy package at the "Avasys" site and as it was from last year I take it it could be the one you got, beats me why they still let people download it knowingly, anyway check this out if you would, and as for Imagescan, I'm surprised that it hasn't worked for you, after a reboot it worked first time for mine, it is also a standalone package so click on its own icon where its own window will pop-up.

Regards, Ellgor.

---

### Post by wonkyuk on 2010-03-03
Check what out?
the deb packages they recommended I uinstall are:
DEB 32bit package [libltdl7] (for Ubuntu 8.10 or later):
iscan_2.24.0-4.ltdl7_i386.deb
esci-interpreter-gt-f720_0.0.1-2_i386.deb

These are the ones I have installed. I have also added the usb line to epkowa.conf to identify my specific scanner and added the line "epkowa" in dll.conf and commented out the other lines. 

After having rebooted, lsusb can see the scanner but sane-fins-scanner cannot. And iscan, Xsane etc cannot find the scanner either of course as they rely upon SANE. I have a feeling there is something wrong in the sane installation on my machine.

so what am I to check out?

---

### Post by ellgor on 2010-03-04
Hi again,

The dodgy package, if memory serves was listed in the FAQ at the Avasys site along with help on rectifying things, as a thought check in synaptic for a package called usbmount, usb's even if seen sometimes fail to work, hope this of use.

Regards, Ellgor.

---

