---
title: "Problems DWL-122 Prism2 USB wlan adapter"
date: 2004-11-11
forum: Hardware &amp; Laptops
---

### Post by tidalwav1 on 2004-11-11
I love Ubuntu, but I simply cannot get my 802.11b prism2-based USB adapter working. The adapter is a D-link dwl-122.

After I plug the device into my USB hub, I try 'lsmod | grep prism' and the modules p80211 and prism2_usb are loaded, but I can't seem to be able to configure the adapter or enable it as a network device (such as wlan0).

I think I would need the linux-wlan-ng driver available at [ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/](ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/),  except I can't get the driver to compile without first compiling my own kernel, which I don't want to do.

Anyone know how I can get this thing working? I've seen a few threads in other forums about this adapter, and none of them have been helpful.

Thanks in advance for your help!

---

### Post by tidalwav1 on 2004-11-11
I just got it working using a precompiled debian package available at [http://ftp.us.debian.org/debian/pool/main/l/linux-wlan-ng/linux-wlan-ng_0.2.0+0.2.1pre21-1_i386.deb](http://ftp.us.debian.org/debian/pool/main/l/linux-wlan-ng/linux-wlan-ng_0.2.0+0.2.1pre21-1_i386.deb).

Just out of curiousity, though--how could I get this thing working without using the [older] precompiled packages?

---

### Post by mattyh on 2004-11-11
I believe I set one of these up previously on a different distro using ndiswrapper.  It was either the 122 or the 120, I can't remember off the top of my head.

---

### Post by az on 2004-11-11
I have the same device.  But I don't use it.  I tried to get it to work once with Ubuntu, but didn't try for very long.

The fact that the correct prism2_usb modules get loaded when plugged it means that the drivers are present in Ubuntu.  Compiling the drivers again will not be neccessary.

I was going to try the command line to get it going.  I remember using the device with sarge and I had to tell the device to reset and to turn on the radio (broadcast) manually before it would actually work.

Here is the quote from the readme:
FOR USB USERS:

A) Make sure your kernel usb support is running
B) Plug in the Prism2.x USB device
C) Run 'modprobe prism2_usb prism2_doreset=1' to load the driver into memory.
D) Run 'wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable' to initialize the
   driver+MAC functions.
E) Run 'wlanctl-ng wlan0 lnxreq_autojoin ssid=<your ssid> authtype=opensystem'
   to enable the MAC in Infrastructure Station mode.
F) Run 'ifconfig wlan0 <your IP address>'

Or, you can use the provided hotplug scripts, if your distribution has
hotplug support.  :) 

IMPORTANT: Due to an issue with some versions of the Prism USB firmware,
the driver usually needs to perform a port reset.  

Some combinations of usb low-level drivers, kernel releases, and
hardware don't like this, and usually end up generating a kernel OOPS.
newer kernels are much better in this regard.  In particular, Intel usb
controllers are the most trouble-prone.



I also think this is relevant:

Add an alias for wlan0 in /etc/modules.conf.  For example, a usb 
   interface on wlan0 would be set up as:

   alias wlan0 prism2_usb

   Substitute prism2_plx or prism2_pci as appropriate.

I will try this tonight...


Also (just to be a complete geek) I was too lazy to look up the README so I tried to use ndiswrapper.  I think that the version of ndiswrapper in Ubuntu is the one just before DWL-122 was added to their supported cards.  The new version (.11) does work.  I tried making those modules and updating ndiswrapper-utils (I remodes the old packages first...)  But I could not get it to work.  My baby started to cry and so I gave up at that point.

I had not bothered to unload the prism_2 modules which were loaded with hotplug.  That may have been why ndiswrapper did not work...   Something else I can try tonight.

---

### Post by az on 2004-11-12
You need to install the linux-wlan-ng package from universe.

That will take care of your /etc/modules.conf entry for you.

Again from the README:
/etc/wlan/wlan.conf:

	This file maps between wlan devices and network IDs, and contains
	the names of all devices that should be initialized by the hotplug
	and rc scripts.

/etc/wlan/wlancfg-*

	These files are per-network configurations.  This makes it easy to 
	switch between different SSIDs and the various settings they may
	require, like WEP keys and whatnot.

The bare minimum you need to do to configure your system after a fresh driver
install:

0)  Nothing whatsoever.  out-of-the-box, the driver will attempt to associate
    with any access point within range.

However, we highly recommend setting up a configuration specifically for
your network, using the following method:

0)  This example assumes your network name/SSID is "MyHomeNetwork"
1)  cp /etc/wlan/wlancfg-DEFAULT /etc/wlan/wlancfg-MyHomeNetwork
2)  edit /etc/wlan/wlan.conf and change the SSID_wlan0 line to:
	SSID_wlan0="MyHomeNetwork"
3)  edit /etc/wlan/wlancfg-MyHomeNetwork, and make any necessary changes 
    necessary to support your network, such as WEP and whatnot.



Hope that helps.

---

### Post by tidalwav1 on 2004-11-12
The problem was, I wasn't able to access Universe without an internet connection. I just installed a standard debian package for linux-wlan-ng that I found on another computer, so everything's fine now. :)

---

### Post by az on 2004-11-12
I blacklisted the prism2_usb and the p80211 modules (/etc/hotplug)
I compiled the most recent ndiswrapper modules and ndiswrapper-utils and installed them

cd to the driver's directory
sudo ndiswrapper -i  NETPRISM.inf

plug the sucker in.

Configure the interface with the networking tool.  This works because ndiswrapper uses wireless extentions.  The linux-wlan-ng uses it's own commands and the Gnome network tool interface does not yet support that.

It is ironic that it is easier to use Windows drivers in Gnome as opposed to the GPL driver for this device...

---

### Post by glmeece on 2004-12-12
OK, I give up. Maybe I've been in too much of a hurry trying to get this thing working.
   
 Long story short: my son's Redhat 9 laptop's PC Card cage is hosed, and as a result so is both wireless and wired connections (PC Cards). I've tured to USB wireless in hopes that I can get him on a network again. I'm supposed to give him the whole kit and kaboodle for his birtday today, but no joy yet.
   
   Anyhow, assuming I can get the linux-wlan-ng on his machine, what else can I do to get it installed?
  
 FWIW, I've been playing around with my wife's Ubuntu desktop but can't get it recognized as a wireless device. I do the Networking wizard, select wireless, and then NOTHING shows up under the drop-down menu. I've tried typing in various strings that I thought might help for the Device name, but still nothing. 
  
  Yes, my machine does recognize the device is there.
  
 I'm not a total Linux newbie, but I've only done one other wireless config, and that was the aformentioned machine for my son. However, it was a PCMCIA card as I indicated.
  
  TIA!

---

### Post by pdaliu on 2004-12-22
Hi:
  I've just made my DWL-122 work on Ubuntu (Hoary PowerPC) without any other outside package or driver input.  I hope it helps.

0) Make sure your linux-wlan-ng package is installed.

1) Try plug your DWL-122 and use lsmod to see if prism2_usb is appropriately loaded.  If no, your kernel has something wrong.  The module is even bundled in Warty.

2) Find the follwing line in /etc/network/if-pre-up.d/linux-wlan-ng-pre-up

result=`$WLANCTL $IFACE lnxreq_ifstate ifstate=enable`

    And let this line executed TWICE.  Yes, twice.  It seems successful initiation needs two visits.

3) My wireless network is simple, i.e. MAC filter without any WEP.  So I added the following to /etc/network/interfaces

auto wlan0
iface wlan0 inet dhcp
        wireless_essid  your_essid
        wireless_mode   infrastructure

4) ifup wlan0

Then it should work!

---

### Post by tidalwav1 on 2005-04-10
[QUOTE=pdaliu]Hi:
  I've just made my DWL-122 work on Ubuntu (Hoary PowerPC) without any other outside package or driver input.  I hope it helps.

0) Make sure your linux-wlan-ng package is installed.

1) Try plug your DWL-122 and use lsmod to see if prism2_usb is appropriately loaded.  If no, your kernel has something wrong.  The module is even bundled in Warty.

2) Find the follwing line in /etc/network/if-pre-up.d/linux-wlan-ng-pre-up

result=`$WLANCTL $IFACE lnxreq_ifstate ifstate=enable`

    And let this line executed TWICE.  Yes, twice.  It seems successful initiation needs two visits.

3) My wireless network is simple, i.e. MAC filter without any WEP.  So I added the following to /etc/network/interfaces

auto wlan0
iface wlan0 inet dhcp
        wireless_essid  your_essid
        wireless_mode   infrastructure

4) ifup wlan0

Then it should work![/QUOTE]

Didn't work over here. :p

My computer freezes trying to bring up the network during the bootup process.

---

### Post by swcc on 2005-12-24
[QUOTE=pdaliu]Hi:
  I've just made my DWL-122 work on Ubuntu (Hoary PowerPC) without any other outside package or driver input.  I hope it helps.

0) Make sure your linux-wlan-ng package is installed.

1) Try plug your DWL-122 and use lsmod to see if prism2_usb is appropriately loaded.  If no, your kernel has something wrong.  The module is even bundled in Warty.

2) Find the follwing line in /etc/network/if-pre-up.d/linux-wlan-ng-pre-up

result=`$WLANCTL $IFACE lnxreq_ifstate ifstate=enable`

    And let this line executed TWICE.  Yes, twice.  It seems successful initiation needs two visits.

3) My wireless network is simple, i.e. MAC filter without any WEP.  So I added the following to /etc/network/interfaces

auto wlan0
iface wlan0 inet dhcp
        wireless_essid  your_essid
        wireless_mode   infrastructure

4) ifup wlan0

Then it should work![/QUOTE]

Great post pdaliu! Here is just a couple of more steps for those who are still having trouble.

I got the DWL-122 up and working in Breezy by adding the following steps to pdaliu's instructions.

Skip step 4 (for now)

5) Modify /etc/modprobe.d/aliases and add the following:
    alias wlan0 prism2_usb

6) Then the ever important:
    sudo /etc/init.d/networking restart

Now do step 4 (ifup wlan0)

Enjoy your wireless!

---

### Post by KiAnKo on 2006-08-09
After installing UBUNTU 6.06 on my Mac Powerbook G4 last month I noticed some problems...

USB WLAN RECEIVER:
Since there is no (?) build-in WLAN-card, I have tried with a D-Link DWL-122, a USB receiver for WLAN. I have been reading:
<http://www.ubuntuforums.org/archive/index.php/t-4041.html>
and downloaded files from:
<http://ftp.us.debian.org/debian/pool/main/l/linux-wlan-ng/>
without any success...


According to "azz":
> Here is the quote from the readme:
FOR USB USERS:

A) Make sure your kernel usb support is running
B) Plug in the Prism2.x USB device
C) Run 'modprobe prism2_usb prism2_doreset=1' to load the driver into memory.
D) Run 'wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable' to initialize the
driver+MAC functions.
E) Run 'wlanctl-ng wlan0 lnxreq_autojoin ssid=<your ssid> authtype=opensystem'
to enable the MAC in Infrastructure Station mode.
F) Run 'ifconfig wlan0 <your IP address>'


When I enter the command: "wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable"
the answear is the command is not found!

Please help me!

---

### Post by Holmen on 2007-01-25
For long I've had problems with DWL-122, but after I've done this:
 sudo apt-get install linux-wlan-ng
It works perfekt! Thank you all, my sister will be very pleased.

---

