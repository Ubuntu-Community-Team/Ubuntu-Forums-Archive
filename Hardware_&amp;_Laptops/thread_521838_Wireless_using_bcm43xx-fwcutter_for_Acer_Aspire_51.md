---
title: "Wireless using bcm43xx-fwcutter for Acer Aspire 5100"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by kslagerman on 2007-08-09
Hello, 

I've got an Acer Aspire 5100 with a broadcom wireless chipset.  I originally was trying to use ndiswrapper to get things running, but I'm very new but through some googling and such, i've leared about the broadcom firmware fiasco on ubuntu and that i need to extract the firmware files using bcm43xx-fw-cutter.  

However, I am unsuccessful in installing it:

First of all, my lspci

```
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

When I attempt to install fw-cutter, either with aptitude install or when directly [downloading (http://packages.debian.org/unstable/utils/bcm43xx-fwcutter)]("http://packages.debian.org/unstable/utils/bcm43xx-fwcutter") it, i get a 404 error (I am connected to the internet with a working wired connection when installing)

here is the output for:

```
sudo aptitude install bcm43xx-fwcutter
```


```
keith@ubuntu:~$ sudo aptitude install bcm43xx-fwcutter
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  file libfreetype6 libgl1-mesa-glx libmagic1 libpng12-0 
  linux-image-generic linux-restricted-modules-common 
  linux-restricted-modules-generic mesa-utils 
The following packages have been kept back:
  app-install-data app-install-data-commercial apport apport-gtk bind9-host 
  capplets-data dbus dbus-1-utils dnsutils evolution-data-server 
  evolution-data-server-common firefox firefox-gnome-support gimp gimp-data 
  gimp-python gnome-app-install gnome-control-center gnome-panel 
  gnome-panel-data hwdb-client-common hwdb-client-gnome iptables 
  language-pack-en libbind9-0 libcamel1.2-10 libcurl3 libdbus-1-3 libdns22 
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 
  libedataserver1.2-9 libedataserverui1.2-8 libegroupwise1.2-13 
  libexchange-storage1.2-3 libexif12 libgimp2.0 libgl1-mesa-dri 
  libglu1-mesa libgnome-window-settings1 libisc11 libisccc0 libisccfg1 
  libkrb53 liblwres9 libmagick9 libmetacity0 libnspr4 libnss3 
  libpanel-applet2-0 libpoppler1 libpoppler1-glib libslab0 libsmbclient 
  linux-generic linux-headers-generic metacity metacity-common 
  openoffice.org openoffice.org-base openoffice.org-calc 
  openoffice.org-common openoffice.org-core openoffice.org-draw 
  openoffice.org-evolution openoffice.org-filter-mobiledev 
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress 
  openoffice.org-java-common openoffice.org-math openoffice.org-style-human 
  openoffice.org-writer poppler-utils python python-apport python-gdbm 
  python-launchpad-bugs python-minimal python-problem-report python-uno 
  python2.5 python2.5-minimal rdesktop samba-common smbclient tcpdump 
  ttf-opensymbol tzdata unattended-upgrades update-manager 
  update-manager-core vim-common vim-tiny xscreensaver-data xscreensaver-gl 
0 packages upgraded, 0 newly installed, 0 to remove and 107 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up bcm43xx-fwcutter (006-1) ...
--18:18:37--  http://boredklink.googlepages.com/wl_apsta.o
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
18:18:37 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up bcm43xx-fwcutter (006-1) ...
--18:18:40--  http://boredklink.googlepages.com/wl_apsta.o
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
18:18:40 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter

```



So basically, it looks like whatever its trying to download at [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o) isn't there.  



i checked out 72.14.203.118 and its just the english google search engine, and boredklink.googlepages.com is just some guy's website.  perhaps the creater's?

Any ideas of how to continue with this? Am I missing something or out of luck?  I am desperatly trying to get my wifi working on this laptop.

Thanks guys!

---

### Post by maxrisc on 2007-08-09
That just recently happened.  It worked last week.  I reimaged onto a larger hard drive and now I cannot get the firmware either.

I will find it and post it on a link somewhere on a google.com page.

---

### Post by maxrisc on 2007-08-09
I have the link and am extracting the firmware.  I will post it up shortly.

---

### Post by kslagerman on 2007-08-10
Thank you sir. Its very much appreciated.  Question though.  If the firmware resides somewhere else on the internet (thanks to you) other than where bcm43xx-fwcutter wants to look for it, can you tell me how to proceed with the install?

---

### Post by maxrisc on 2007-08-10
Actually yes I can.  Go to [http://boredklink.googlepages.com/ubuntuguide](http://boredklink.googlepages.com/ubuntuguide)

You will need to get the latest firmware from a link on that page and run all the commands yourself.  I just installed it and now I am using wifi. :0)

Or if that doesn't work I can just post a zip file of all the firmwares and you can extract it into /lib/firmware and it should work for you.

HTH.

---

### Post by kslagerman on 2007-08-10
absolutely amazing.   wifi working perfectly.  

I wasn't able to download wl_apsta.o, but used bcmwl5.sys instead and it works fine.  i guess thats where a lot of my confusion was coming from. 

and a note to anyone else, the guide says that if your lspci states:

> 06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

it wont work, but in fact, I have this exact chipset and its working fine. 


cheers and thanks


keith

---

### Post by Hoov on 2007-08-16
How do I run these commands manually? I'm desperately trying to get my sister's laptop fully functional but the bcm43xx-fwcutter does not work from package manager.

I downloaded the wl_apta.o file to the desktop but can't do anything else. When I run the cmd line to extract the firmware it says it cannot open the input file.

---

### Post by kslagerman on 2007-08-16
have you actually installed fwcutter yet?

easiest way would be to use ubuntu's package manager, search for "bcm43xx-fwcutter" and install. 

you will get the 404 error, but the packages *does *actually install. 

once it fails, ignore the error and close the package manager.

rather than using wl_apsta.o download this to your desktop instead:

[http://sidulus.textdrive.com/bcmwl5sys.zip](http://sidulus.textdrive.com/bcmwl5sys.zip)

Extract bcmwl5.sys to your desktop.

Then open a terminal and type:

```
sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/bcmwl5.sys
```

This will put a bunch of stuff in your/lib/firmware directory


Then you need to extract the firware to the directory in your /lib/firmware directory.

```
sudo bcm43xx-fwcutter -w /lib/firmware/x.x.x-x-x ~/Desktop/bcmwl5.sys
```

Replace the x's with name of the directory that is on your /lib/firmware directory.  it will look something  like this:   2.6.15-23-386



Reboot and you should be good to go.  
This is assuming that you are trying to get a broadcom wifi chipset going.  im pretty sure this only works for broadcom.

---

### Post by Dimitriid on 2007-08-19
Hello.

I tried some other steps ( a guide [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") that i followed but did not remembered I am running on a 64bit kubuntu install. First restart did not take but I was able to shoot down, second restart took but on kubuntu the wireless is just grayed out and i cannot connect to anything.

I have a Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01) ( with that lspci command ) running on a 5100-5674 acer system. But as I said I have kubuntu 64bit installed. How can I uninstall all the steps I did for ndiswrapper and try perhaps this ( if they would work with a 64bit driver, It was recognized in the initial kubuntu install but just not working as described here ).

Thanks in advance.

---

### Post by Hoov on 2007-08-19
kslagerman,

Thanks very much! I followed your instructions and it worked perfectly. The biggest thing that tripped me up is the 404 error with bcm43xx-fwcutter.

Thanks again.

---

### Post by Dragon5000 on 2008-05-11
Hello everyone!
Listen guys, I know this is an old thread but I'm having a weird problem...I've had to reinstall Gutsy because I screwed my video all up and couldn't find a way to fix it. Now, I can't get my wifi back. The steps posted here are what I used before to get it going, but now the wireless card is just not working. It is recognized in the "Hardware Information", but when I do a ifconfig -a, only the ethernet eth0 shows up. Please any help would be highly appreciated. Please let me know if any extra info is needed.

---

### Post by Dragon5000 on 2008-05-12
Maybe some spec's would help...
Acer Aspire 5100
AMD Turion 64 X2
1GB RAM
ATI Radeo Xpress 1100
Atheros AR5006EG wifi adapter
I think that is pretty much all the important stuff.
I've tried ndiswrapper but after loading the winxp driver, I couldn't even get it to see the wireless network.
Please I beg you all, I don't even want to dual boot with XP!!!

---

