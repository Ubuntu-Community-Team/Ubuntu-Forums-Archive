---
title: "HP C6380 Printer drivers"
date: 2008-10-21
forum: General Help
---

### Post by Nitewalker on 2008-10-21
I have just installed a HP C6380 Photosmart printer on my Ubuntu 8.04 system, and it seems to work alright, except that I can not get it to print "borderless" 4/6 inch photo's.  Ubuntu 8.04 doesn't list the printer in the "printer install" area of the system.  What do I need to do to get it to print correctly?:confused:

---

### Post by shirilover on 2008-10-21
I couldn't find your printer listed on the HPLIP website; but, I would first use the latest hplip, which is 2.8.9.
It is available from [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
Installation instrctions can be found at that site as well.

---

### Post by wolfen69 on 2008-10-21
do a search in synaptic for "hplip gui". it gives you advanced printing options. it will show up in system>preferences as hplip toolbox.

---

### Post by Nitewalker on 2008-10-21
do a search in synaptic for "hplip gui". it gives you advanced printing options. it will show up in system>preferences as hplip toolbox.

Installed the "hplip gui" from synaptic, and when I run it it says
"Error, no device found or unsupported device"  it does show a "HP Photosmart c6300 series with a red x above it in the side panel?

Any suggestions or do I need to get a different printer that is equivalent to this one?  I need it to be "Ethernet plus wires capable. :confused:

---

### Post by Maxwell7 on 2008-11-20
I'm about to buy this model myself (at least if it works) and I wondered if you (or someone else) got it working on Intrepid Ibex 8.10 ?

Thanks! 

Maxwell

---

### Post by hfdragon on 2008-11-28
I've just seen that the printer is supported with the new hplip version (2.8.10). (see link above)

Could anyone try it ?
Maybe I'll buy one if it's working properly :)

---

### Post by capkid2a on 2008-12-05
> **hfdragon said:**
> I've just seen that the printer is supported with the new hplip version (2.8.10). (see link above)

Could anyone try it ?
Maybe I'll buy one if it's working properly :)

It works fine with 8.0.4 with hplip 2.8.10 -- over wireless as well

---

### Post by Mr_L_Prosser on 2008-12-13
> **hfdragon said:**
> I've just seen that the printer is supported with the new hplip version (2.8.10). (see link above)

Could anyone try it ?
Maybe I'll buy one if it's working properly :)

Just bought and installed a C6380 on Ubuntu 8.10 about 1/2 an hour ago.

Obviously I've not tested it thoroughly yet, but I have at least managed to print test pages over the wireless network :p  Not tried using the ethernet or usb connections though.  

I was happily surprised to find that the scanner (using XSane) also seems to work with no further setup -although one time it crashed the C6380 for some reason :confused:  I gave it a few mins before pulling the plug and it seems to be working fine now.

You do need hplip-2.8.10 (synaptic installed 2.8.7 and this wouldn't detect the printer, and produced errors if I configured the printer manually).  I just followed the instructions from [hplipopensource]("http://hplipopensource.com/hplip-web/models/photosmart/photosmart_c6300_series.html") and it worked a charm!

---

### Post by jeffreyldavidson on 2009-01-03
I have the same printer and it seems to work well printing and scanning with two exceptions. 

1) I cannot get the photos to print from the photo tray. Even if I change the picture size there is not an option to print to the tray instead it prints to the regular paper.

2) If I select scan manually from the lcd display on the printer it will ask me where I want the output to go. I have two laptops that connect wirelessly - Mac & Ubuntu. The Mac computer shows on the display to output the scan to but my Ubuntu machine does not.

All else works wirelessly without any problems including choosing scanning from my laptop to scan from the printer.

---

### Post by TheRingmaster on 2009-04-03
I have this printer as well and everything works fine as far as printing and copying goes,but xsane gives me an error that it didn't find any scanners. so therefore I can not scan with this printer. I'll try to install libsane-extras package and see if that makes any difference tomorrow.

anyone else not able to use xsane with this All-in-one printer?

---

### Post by stir-crazy on 2009-04-03
Just got mine today, seem to be able to print fine, xsane just returns "No devices found"; have installed libsane-extras package, no love.

---

### Post by stir-crazy on 2009-04-04
Okay, the version of hplip in the ubuntu repositories isn't up to date, and is why there are problems with this.  I just downloaded and installed the latest hplip from HP **[COLOR="Navy"][here]("http://hplipopensource.com/hplip-web/downloads.html")[/COLOR]**

Just follow the instructions, it's a piece of cake.  Now I have full functionality of this printer, Xsane recognizes it, can scan, etc.

Woo-hoo!  Oh, you probably want to uninstall hplip prior to installing the latest from the link above.

---

### Post by TheRingmaster on 2009-04-04
> **stir-crazy said:**
> Okay, the version of hplip in the ubuntu repositories isn't up to date, and is why there are problems with this.  I just downloaded and installed the latest hplip from HP **[COLOR=Navy][here]("http://hplipopensource.com/hplip-web/downloads.html")[/COLOR]**

Just follow the instructions, it's a piece of cake.  Now I have full functionality of this printer, Xsane recognizes it, can scan, etc.

Woo-hoo!  Oh, you probably want to uninstall hplip prior to installing the latest from the link above.


Thanks so much, I hadn't realized that I was out of date!! Everything is fine here now.):P

---

### Post by AJI on 2009-04-12
Oh the irony.

Installing hplip from 8.04's repository gave me printing, but the scanner would not work.

Uninstalled the package, installed the latest hplip, and after several times trying to get all the "required but we did not bother to tell you" packages in place, I ended up **able to scan** but **unable to print**.

I eventually had to let the new hplip installation fail, then manually run ```
./configure --enable-foomatic-rip-hplip-install
``` from within the source directory, then ```
make
checkinstall
```.

Now it works, printing, scanning and all.

---

### Post by shiellb on 2009-05-26
Thank you all for the information posted.  From it, I've been able to get my new C6380 to print, scan and copy.  As noted earlier, the machine will not print a photo from the photo paper tray.  I'm using 8.04 along with hplip-3.9.4b.

---

### Post by shiellb on 2009-06-02
I've been able t print a photo from the photo tray.  I went to System - Administration - printing - highlighted photosmart C6380 - printer options - print out mode - photo (on photo paper) and it worked.

---

### Post by marius76 on 2009-08-13
Hello
I'm about to buy this model myself (HP C6380 photosmart all-in-one) and I wondered if somebody got it working on Jaunty jackalope 9.04 ?
I want to work with an ethernal switch (RJ 45) with 2 computeurs on jaunty !

Thanks!

---

### Post by serfcx on 2009-08-14
> **marius76 said:**
> Hello
I'm about to buy this model myself (HP C6380 photosmart all-in-one) and I wondered if somebody got it working on Jaunty jackalope 9.04 ?
I want to work with an ethernal switch (RJ 45) with 2 computeurs on jaunty !

Thanks!

I'm not sure about this model but upgrading to jaunty with hplip-3.9.2 broke my printing to CD's with my HP C5280 multi-function. Apparently its fixed in the Karmic repos :(

---

### Post by marius76 on 2009-08-14
Thank you for this information.
I hope that it is not the same with C6380...
I'm really about to buy this model.
Some people one french ubuntu forum seem to be happy with this model...
You can read all reply here :
[http://forum.ubuntu-fr.org/viewtopic.php?pid=2868631#p2868631](http://forum.ubuntu-fr.org/viewtopic.php?pid=2868631#p2868631)

Thank's

---

### Post by themusicwave on 2010-02-21
I got it working in 9.10 using the version of hplip in the repository.  I can scan and print wirelessly.  Copy works, because you don't need a driver for that.

---

### Post by kellemes on 2010-02-23
> **themusicwave said:**
> I got it working in 9.10 using the version of hplip in the repository.  I can scan and print wirelessly.  Copy works, because you don't need a driver for that.

Well, only scanning didn't work for me on (K)ubuntu 9.10
As said by **stir-crazy** (thanks for that) .. [Downloading and installing the latest hplip]("http://hplipopensource.com/hplip-web/downloads.html") works, for me anyway..
I upgraded hplip from version 3.9.8-1 to version 3.9.12

---

### Post by kellemes on 2010-03-10
Scanning did stop working again.. for some reason hplip seems to have vanished/not installed, pretty strange..
Anyway, I used **The HPLIP Automatic Installer** to install hplip-3.10.2, [I got it here]("http://hplipopensource.com/hplip-web/downloads.html"). All good for now.

---

