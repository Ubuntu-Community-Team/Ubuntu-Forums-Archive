---
title: "Dumping Windows"
date: 2007-09-24
forum: Hardware &amp; Laptops
---

### Post by JRV on 2007-09-24
I am in the process of switching to Ubuntu and I want to completely eliminate windows from my home network eventually.  

My network consists of:

My main computer which dual boots Windows XP and Ubuntu.  I use Ubuntu for everything except burning DVDs.  
I can't seem to get programs for ripping, creating menus, and burning DVDs that work as well as Nero in Windows.  
Is there a program to do printable CD/DVDs in an Epson R200 printer?
Is there an easy way to transfer my address book from outlook Express to Evolution?

My backup machine runs Ubuntu with no problems.

I have a VIA EN-1500 based computer hooked into my entertainment system for playing audio and video files.  Ubuntu was very slow on this system, it could not display full screen video.  I had to re-install Windows.  I did look in the restricted driver manager and there was nothing there.  Is there something I missed?  Ubuntu seems a little faster on the two machines mentioned above.  Is the code just not optimized for the VIA processor?

I have another VIA Mini-ITX which is my DHCP server, file server, firewall, and downloading machine.  It is still running Windows.  I will be switching it over to Ubuntu soon.  This should not present any problems.

And now for my laptop.  It is a Fujitsu P1050.  Booting from the live CD took about 15 minutes.  (Really, this is no exaggeration).  Is it going to be that slow If I install?
Is there a driver for the touch screen?
The wireless didn't seem to work booting off of the live CD, but I didn't try very hard because of all the other problems. I think I can figure that out.

Please help with any of these problems if you can.

Thankyou

JRV

---

### Post by shak541 on 2007-09-24
hello. I'm happy to hear that you are going to leave windows. I did the same about 2 months ago. Now i can;t stand windows or any microsoft product. Try out nerolinux! its pretty much nero for linux. But it does not have some features. The trial is worth a shot. It can copy dvd's as far as i know.

As for booting off the live cd. Your cd rom drive is slow. But ubuntu will be really fast once its installed. i had the same issue. 5min to boot off the live cd. Then when i installed it. It took no time at all. Logging in literally takes me 2 seconds on an AMD Athlon 1800+ 1.53 Ghz , 256 MD ram, Ati Radeon 7000 . 
As for wireless... get wifiradar.... It works great and its super easy.. as easy as windows wifi manager!

---

### Post by Linder on 2007-09-25
Also, lack of memory could be the issue with the live-cd on the lappy. If you have anything around 256 Mb RAM then you're in for a rough ride, ESPECIALLY if that memory is shared by the graphic card. Then you can hardly boot from a live-cd at all. Try the alternative disc to see if it alleviates the problem.

---

### Post by JRV on 2007-09-27
Linder,

Where do I find the alternative CD? 
I found another problem.  With my 1024x600 resolution I can't see the bottom of some of the dialogue boxes in the installer.
I've heard of a text based installer.  Where do I get it?

Thank you

JRV

Never mind, I found it.

---

### Post by lisati on 2007-09-27
The "alternate" cd is downloaded separately from the LiveCd

---

### Post by sorc18UK on 2007-09-27
> **shak541 said:**
> hello. I'm happy to hear that you are going to leave windows. I did the same about 2 months ago. Now i can;t stand windows or any microsoft product. Try out nerolinux! its pretty much nero for linux. But it does not have some features. The trial is worth a shot. It can copy dvd's as far as i know.

As for booting off the live cd. Your cd rom drive is slow. But ubuntu will be really fast once its installed. i had the same issue. 5min to boot off the live cd. Then when i installed it. It took no time at all. Logging in literally takes me 2 seconds on an AMD Athlon 1800+ 1.53 Ghz , 256 MD ram, Ati Radeon 7000 . 
As for wireless... get wifiradar.... It works great and its super easy.. as easy as windows wifi manager!

Where do I find this wifiradar and how do I get it onto my non internet connected laptop?

---

### Post by w4ett on 2007-09-27
> **JRV said:**
> Linder,

Where do I find the alternative CD? 
I found another problem.  With my 1024x600 resolution I can't see the bottom of some of the dialogue boxes in the installer.
I've heard of a text based installer.  Where do I get it?

Thank you

JRV

Never mind, I found it.

To move a dialog box, <alt> + right click and drag.

---

### Post by shak541 on 2007-09-29
wifi radar can be found from [http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/) .
You could put it on a flash drive, cd or external hard drive

---

### Post by mrojas73 on 2007-09-29
GnomeBaker is great program for burning cds, dvd, images and lots more.  i used to be a Nero fan for many years and when I dumped 
windows about 2 years ago I started using GnomeBaker and that is all I use now.

---

### Post by Natr0n on 2007-09-29
Moving your address book doesn't seem like it will be a problem. Here's a link with one method of how to do it: [[COLOR="Blue"]Moving email from Windows to Linux[/COLOR]]("http://www.softwareinreview.com/cms/content/view/29/"). Skip to the part where it says "Mozilla Thunderbird", I assume you don't want to pay for a new program to do this. I think there might be a better way because [[COLOR="Blue"]this page[/COLOR]]("http://linuxplanet.com/linuxplanet/reviews/5323/4/") says > The Evolution address book can import LDAP, Outlook Express, vcard and .CVS files. Export is similar with .CVS and vcard 3.0 files. You can save files in the vcard format.but I wasn't able to find specific instructions. As for burning DVD's and whatnot, I've found that k3b works excellently. I used to use Nero as well, but in my opinion, k3b actually works better.

---

### Post by Natr0n on 2007-09-29
> I think there might be a better wayActually, maybe not according to the [[COLOR="Blue"]Evolution Documentation[/COLOR]]("http://www.gnome.org/projects/evolution/documentation.shtml").> Microsoft Outlook and versions of Outlook Express after version 4 use proprietary formats that Evolution cannot read or import. One migration method that works well is to use the Outport application. See outport.sourceforge.net ([http://outport.sourceforge.net](http://outport.sourceforge.net)) for additional information. You can also import data into another Windows mail client such as Mozilla. Oh well, using the Mozilla Thunderbird method should work.

---

