---
title: "Problem setting up internet on 8.04"
date: 2008-05-10
forum: Hardware
---

### Post by haran_hockey on 2008-05-10
I really need to setup internet on ubuntu 8.04 as my screen resolution is still on 640x480 and i can't donwload the nvidia driver without internet. Also, I can't install stuff like advanced desktop effects because I don;t have the ubuntu cd as I used wubi to isntall ubuntu.

I'm on a wireless connection(so I have the stick thingy in my room shown [http://www.cheapstingybargains.com/wordpress/wp-content/images/prod32568.gif]("http://www.cheapstingybargains.com/wordpress/wp-content/images/prod32568.gif") and my brother has 2 modems(1 from rogers and 1 shown [http://i167.photobucket.com/albums/u131/karthiik/ShanKri-la/trendnet.png]("http://i167.photobucket.com/albums/u131/karthiik/ShanKri-la/trendnet.png")     )

The model is Trendnet Wireless G Broadband Router TEW-432BRP

Note: This is my first version, I've never used linux before so I'm really new to things. Please give detailed instructions if you can.

I am also using windows 2000 professional SP4 with 2.00 GHz and 256 mg of ram

For my 640x480 problem, my display adapter is Intel(R)82845G/GL/GE/PE/GV Graphics Controller

---

### Post by jordey24 on 2008-05-10
hmm...you already try to change the resolution?
about the internet problem,it's a bit strange because it works fine for me (i also use wireless)
Sorry i'm using ubuntu not very long but when i know of something,i tell.

---

### Post by haran_hockey on 2008-05-10
I've already tried changing resolution- only 640x480 is available and I need cd to change that and I don't know how and where to install my trendnet driver for linux.

---

### Post by hermes0710 on 2008-05-12
Go here :

[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu]("http://madwifi.org/wiki/UserDocs/Distro/Ubuntu")

---

### Post by wadelewis4 on 2008-05-12
The model of your wireless router doesn't matter, it's the model of your USB wireless adapter (What you called a "stick thingy"). That's what Ubuntu isn't loading drivers for. Your options are as follows: 1) Install a supported wireless adapter (which may cost you 30.00 bucks or more). 2) Buy an ethernet patch cable (the length you need from your computer to your wireless router) and plug one end into one of the ports on the router and the other into your computer's ethernet port. This will give you a wired connection that you can use to download the files you need (The nvidia drivers, plugins, other drivers, etc). 

I would have to say try #2 first. You really need to also let us know what the model of that usb wireless adapter is, so we can see if there is a workaround for it. Ndiswrapper may be an option in this case, but you'll need the windows version of the driver - not to mention an internet connection for downloading everything.

Once your internet connection is up, you can go to Hardware Drivers and install your proprietary video drivers without hiccup. From there you'll be worry free.

---

### Post by holynik on 2008-05-12
I am have trouble thish hardy
Specified hardware USB ADSL Globespan virata is not detected.
Is old problem USB device indentification.
Driver eciadsl is installed (debian pakage) i am reading more instruction, can not  device working. Other more errors is not visible. driver eciadsl-usermode version 1.12.1
GUI is tk interface not found, text mode is normal.
PC mashine is old - USB v 1.1 
I am haved more problem on printer USB HP LJ 1000.
It is resolved  manual editing printers.conf 
changed device URI hp:/usb/hp_laserjet_1000 -> file:///dev/usb/lp0
/dev/usb/lp0 do resume start test page print is removed /dev/usb folder on default. It work only used simvolic link /dev/usblp0 dont print test page (after page print always port removed to reject usb cable)

---

### Post by haran_hockey on 2008-05-12
Ok. My usb wireless adapter model is TEW-424UB. I've downloaded ndiswrapper 1.52 but I'm not really sure what to do with it. Hope it helps now you know what the model of my adapter is.

EDIT: I went to this site: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/") and my adapter model was there so now what do I do.

---

### Post by jordey24 on 2009-04-29
Did you upgrade to the 9.04 version of Ubuntu?The problem might be solved in the newer version.

---

