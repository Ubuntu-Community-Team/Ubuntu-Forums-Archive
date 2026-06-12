---
title: "Printing from Xubunto to via Windows server"
date: 2014-10-01
forum: Hardware
---

### Post by gordon99 on 2014-10-01
I am able to print documents from Xubuntu, via a Homegroup network, using a Canon printer which runs off a Windows 7 PC  However,  a 13 kb document takes 60 seconds to print in this manner whereas if print the same document from a Windows OS client it takes just 10 seconds. I have tried to speed up the printing process from Xubuntu by following a number of suggestions I have received in other forums, all without success. One other idea comes to mind which I would be glad to receive advice on. 
The Canon printer has a usb connection to my wife's Windows PC and I am reluctant to interfere with that. However, the printer is suitable for wireless operation.
Would it be possible to print documents from my Xubuntu Notebook using a direct wireless connection to the printer while leaving the usb connection to my wife's PC intact? I assume I would need to uncouple the Homegroup printer connection in case it interfered with the wireless connection.

---

### Post by Vladlenin5000 on 2014-10-01
Certainly you understand that must be differences when printing to a locally (USB) connected printer and other or the same printer via network and yours currently depends on a Windows PC as a print server to makes things worse... Network printing depends on many factors most of then network rather than OS specific. In a nutshell, the network, not Xubuntu or Windows, is the culprit for any delayed start and slowliness.
In a properly configured network, remote printing should work almost as fast as local, never as fast.

It would be awesome at this point if you understood the basics of networking but from your post I deduct you don't. Considering this, I'll have to elaborate about a few concepts and related 'best practices':

**1.** Starting with the best practices, in any home or SOHO network environments, use any network enabled printer directly to the router, not through another computer.
Your current setup has the printer connected to a Windows PC which in turn acts as a print server, *sharing* the printer with any other PC or similar in the same network. Use this setup only if you need to remotely print to printer without network features.

**2. **Network enabled printers usually have Ehternet, WiFi or both. Use only one and prefer the former whenever possible. Cable or WiFi have the same end result - connecting to a network - but performance varies. Again, in a properly configured network, there shouldn't be any significant delays compared to USB. A standalone network printer is equally accessible from any computer in the same network. As such your wife should see no difference and you can even move the printer to a more convenient place instead of having it tied up with the PC. And if the new place precludes the use of a cable to the router then by all means use WiFi instead as it shouldn't make any significant different either. Now, if you really don't want to disconnect the USB the good knew is you probably don't need to as most printers can have both simultaneously -> You wife would still print to a local printer, same as always (she would also have the choice of new network printer, which is the same obviously, but she won't use that), whereas everybody else would be remotely printing as well.
Case in point, a network printer in the aforementioned scenario has its own IP address like any other computer and for all intended purposes it's just another device in that network, at the same "level" of the PCs, tablets, phones, etc. No *ad-hoc* wireless connection involved although some printers allow such for certain devices.
Lastly... Yes, you figured out correctly that after having your printer properly networked as per the "best practices" above there's no point in keeping it shared in Windows. Actually it's recommend not to.


Your homework now is confirm whether or not your printer can have both network and local connections simultaneously. If not, networking as mentioned above is still recommended; properly configured your wife won't notice the difference.

---

### Post by gordon99 on 2014-10-03
Good afternoon vladlenin. After reading your reply to my enquiry I did more research. I found that my printer, although having wifi facility, is not really network enabled having no ethernet connection facility. Also my router, a Netgear WNR1000 v.3 is not printer driver enabled as some routers are.

I went onto the Canon Forum and enquired if it would be possible to connect to the printer's wifi from my Xubuntu OS laptop while keeping the usb connection to my wife's PC. The reply i received was that there is no Linux printer driver for the Canon Pixma MG3100  and I have to stick with the Windows Homegroup in order to print from the laptop. This is all very disappointing. 

Although I don't really follow the technicalities, I understand the slowness of printing from my laptop may be due to having to use SAMBA to connect Linux to Windows for printing purposes. I've read quite a few threads regarding this but have not seen a solution that might apply to my set up.

Thank you for giving me your time.

---

### Post by Vladlenin5000 on 2014-10-03
You got some incorrect replies. Here's my modest attempt to correct them:

1. If your printer has no driver for Linux, native open source or proprietary, you wouldn't be printing from a Linux machine. Period.
The different communication path - network instead of USB cable - doesn't change the "nature" of the end-device. **It's still the same printer requiring the exact same drivers to work**.
Windows doesn't magically turns an unsupported printer in Linux into a supported one. It just shares the printer to the network like any other OS could do. Any device printing remotely to that printer will have to use its own drivers, the same drivers it would use for the same printer connected locally.

2. **Any WiFi enabled printer IS a network enabled printer** regardless of supporting or not additional network connections like Ethernet. Having a printer shared by a PC acting as a print server is **exactly **the same as having the same printer as standalone device in the network, except that the latter setup *should* be more reliable and faster (not much; often the gain is imperceptible) than the former, the one you currently have.
The setup for the "client" devices, ie, the devices you'll remotely printing from, is also exactly the same but with a different internal IP address, the printer's own IP address. Currently you're printing to the printer's print server (Windows PC) IP address.
The important point - again - is whether or not your print can be simultaneously in the network (WiFi) and locally connected to one of the PCs. Some printers allow it, other don't. That's the question you should have addressed to the Canon's forum, irrespective of the OSs used in the network. And this is important ONLY because YOU want it to be by insisting in keeping the USB connection as well.
Don't confused those poor souls at Canon's, most of them Windows only users, with the details of the OSs present in your network.
Don't worry about the drivers because you already have them working. Perhaps there are better drivers but you already have one that works.

3. Indeed, the slowness can be caused by the network setup and SAMBA playing a huge part in it. However, it mostly depends on the Windows PC acting as the print server, ie, on how it works in network in general, its network demanding apps running concurrently, malware, etc. You know, bandwidth is finite. 
**That's precisely the reason why putting the printer as a standalone device in the network is ALWAYS the best option.**

---

### Post by pdc on 2014-10-03
I will leave Vladlenin5000 to lead the guidance here; I need to work through his detailed guidance for my own benefit;

all I would chip in with is that **Canon provide linux drivers for the MG3100**: we have an MG3100 running very well with Canon debian drivers (they come in 32bit and 64bit variants):

so if it is a matter of a usb cable from printer to computer; I am happy to offer guidance on getting those drivers installed;

---

### Post by Vladlenin5000 on 2014-10-04
Thank you, @pdc.

As I commented before the drivers are the same and those proprietary drivers you mentioned might just be the thing missing in gordon99's Xubuntu in order to have a better performance, even keeping the current setup. So, please, post here the links and procedure you used and we'll see about that.

---

### Post by pdc on 2014-10-04
so I am thinking this is an invite to describe how to install the Canon MG3100 drivers onto a debian system (as ubuntu uses)

so go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100393702.html?r=s&q=](http://support-asia.canon-asia.com/contents/ASIA/EN/0100393702.html?r=s&q=) and download and SAVE what is [COLOR="#008000"]cnijfilter-mg3100series-3.60-1-deb.tar.gz
[/COLOR]
___________________

as it is the 3.6 version, it needs libtiff 4 that ubuntu has withdrawn, so get the libtiff4 from Debian [ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/) and go about 14 down the list to find either the 32 or 64bit 

__________________

with libtiff4 installed, open a terminal and paste these commands; line by line; hitting ENTER after each paste 

[COLOR="#FF0000"]cd Downloads
tar -zxvf cnijfilter-mg3100series-3.60-1-deb.tar.gz
cd cnijfilter-mg3100series-3.60-1-deb
./install.sh [/COLOR]

and that will start the install script

---

### Post by gordon99 on 2014-10-04
gordon@Gordon-HP:~$ cd Downloads
gordon@Gordon-HP:~/Downloads$ tar -zxvf cnijfilter-mg3100series-3.60-1-deb.tar.gz
cnijfilter-mg3100series-3.60-1-deb/
cnijfilter-mg3100series-3.60-1-deb/packages/
cnijfilter-mg3100series-3.60-1-deb/packages/cnijfilter-common_3.60-1_amd64.deb
cnijfilter-mg3100series-3.60-1-deb/packages/cnijfilter-mg3100series_3.60-1_amd64.deb
cnijfilter-mg3100series-3.60-1-deb/packages/cnijfilter-mg3100series_3.60-1_i386.deb
cnijfilter-mg3100series-3.60-1-deb/packages/cnijfilter-common_3.60-1_i386.deb
cnijfilter-mg3100series-3.60-1-deb/resources/
cnijfilter-mg3100series-3.60-1-deb/resources/printer_zh_utf8.lc
cnijfilter-mg3100series-3.60-1-deb/resources/printer_ja_utf8.lc
cnijfilter-mg3100series-3.60-1-deb/resources/printer_fr_utf8.lc
cnijfilter-mg3100series-3.60-1-deb/install.sh
gordon@Gordon-HP:~/Downloads$ cd cnijfilter-mg3100series-3.60-1-deb
gordon@Gordon-HP:~/Downloads/cnijfilter-mg3100series-3.60-1-deb$ ./install.sh
==================================================


Canon Inkjet Printer Driver
Version 3.60
Copyright CANON INC. 2001-2011
All Rights Reserved.


==================================================
An error occurred. The package management system cannot be identified.
gordon@Gordon-HP:~/Downloads/cnijfilter-mg3100series-3.60-1-deb$

---

### Post by gordon99 on 2014-10-04
Sorry pdc & vladlenin, I must have pressed the wrong button and posted the above before adding a message. You will see I even have problems using the Forum.
I simply downloaded libtiff4. This may not meet the requirement to install it. 
I deleted the problem printer from 'Settings/Printers-localhost' before following pdc's guide in case it interfered with any new installation. 
Please advise what I might try next if you have time.

---

### Post by pdc on 2014-10-05
> An error occurred. The package management system cannot be identified.

.......... this is usually said to occur when the install script finds evidence of rpm on the system; and doesn't go with the debian install: so a manual install is needed

.........but I can't advise you on the details, as I don't know if you have a 32bit or 64bit system ............... please reveal that now ........................

---

### Post by gordon99 on 2014-10-05
64 bit , amd processor.

G.

---

### Post by pdc on 2014-10-05
thanks;


if you open a terminal, and paste these commands ......hit ENTER after each paste .........

.............first can we check that libtiff4 is installed > [COLOR="#FF0000"]dpkg -l | grep libtiff4[/COLOR]

............if you get a yes, then move on to the below ......

> [COLOR="#FF0000"]cd Downloads/cnijfilter-mg3100series-3.60-1-deb/packages/[/COLOR]

> [COLOR="#FF0000"]sudo dpkg -i cnijfilter-common_3.60-1_amd64.deb[/COLOR]

> [COLOR="#FF0000"]sudo dpkg -i cnijfilter-mg3100series_3.60-1_amd64.deb[/COLOR]

......... that should install the drivers and should create the needed entries.............any joy?

---

### Post by gordon99 on 2014-10-06
Hello again pdc and vladlenin, I am very pleased to be able to say that my printer is now printing at its normal speed.  When I entered[COLOR=#FF0000]* '*[/COLOR]dpkg -l | grep libtiff4' I did not get an answer in the affirmative. However, I pressed on and at some stage a message saying "libtiff4 has no installation candidate" appeared. I therefore went back and tried to install 'libtiff4' again but seemed to be getting nowhere. Eventually, after some googling, I fell upon the following website which seemed to be fairly recent "http://tutorialforlinux.com/2014/06/16/how-to-install-libtiff4-for-ubuntu-14-04-trusty-lts-linux-easy-guide/". I therefore did what it said and then returned to pdc's guide. This time, on entering 'dpkg -l | grep libtiff4' in terminal a more positive message returned so I carried on to completion. I then went through the normal "add printer" routine and saw I had the option to select the MG3100 v 3.60 driver which I did. This has done the trick.
I am very grateful to you both for sorting this out for me.  Thank you for time and trouble.

---

### Post by pdc on 2014-10-06
thanks Gordon; glad it is all working

..........sorry to hear of your problems with libtiff4 ..............in post #7 I mentioned how to get it from the Debian repository; there, you click on the file you want and it is downloaded for you and the tip on adding the older ubuntu repository is very useful

---

### Post by Michael_McKenney on 2014-10-06
Setup Windows Server Print Services with IP printers.  I have never tried installing Linux drivers in Windows Print Services.  The printers will broadcast with IP address and you manually install the drivers.

---

### Post by gordon99 on 2014-10-10
Michael, sorry I have not responded sooner. 
As you will know from my earlier reply to pdc and vladlenin my printing is now up to speed having followed pdc's guidelines. I do not have sufficient knowledge to know what is involved in setting up the arrangement that works well for you. However, I seem to remember that, at one stage, I had tried a method that involved using the IPv4 address of the Host PC (my wife's computer), without any success I hasten to add. This may well have been because I went astray somewhere along the line, but in any case it may have no connection with your method.
If you would care to expand on the set-up procedure you use I would be more than happy to give it a go

---

### Post by Vladlenin5000 on 2014-10-10
What really changed was the use of proprietary drivers instead of the default open-source ones (openprinting community). A proprietary driver from the manufacturer is always supposed to do a better job and in this case apparently (and fortunately) those drivers are *au pair* with the Windows ones.
My suggestion regarding the optimal network configuration still stands but if the current state is good enough for you, by all means, keep it.

---

