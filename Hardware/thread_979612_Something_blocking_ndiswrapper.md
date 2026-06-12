---
title: "Something blocking ndiswrapper?"
date: 2008-11-12
forum: Hardware
---

### Post by LastChildren on 2008-11-12
So I'm fed up with dealing with the whole b43 fiasco, reverted back to 8.04 and decided to try using ndiswrapper to get my bcm4318 card working on my laptop (which worked FLAWLESSLY back in the bcm43xx days btw) and i've followed all the instructions on this wiki [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

Before I blacklisted all the native drivers (b43, ssb, etc..) iwconfig showed my device under wlan0, but I couldn't connect to anything nor could I detect any networks. 

But after blacklisting everything, installing ndiswrapper and the bcmwl5.inf driver (and yes, i have the .sys file in the same folder), verifying that the driver was loaded via ```
sudo ndiswrapper -l
``` loading the module via ```
sudo modprobe ndiswrapper
``` adding ndiswrapper in /etc/modules and restarting a couple of times, I get NOTHING.  In Konsole, iwconfig now no longer shows my device (no wlan0).

Could there be something else interfering with ndiswrapper?

---

### Post by rondackcpu on 2008-11-12
Here is the method I have been using to get the 4318 working.  Courtesy Mazza558, long, long ago.  Search back thru Mazza558's posting if you want to find the original.

1.) Remove the b43-fwcutter package if you have it installed

Code:

sudo aptitude remove b43-fwcutter


2.) Follow the method you have used to get ndiswrapper working with bcmwl5.inf, or use this

Code:

sudo ndiswrapper -i bcmwl5.inf

3.) Here's a workaround to getting ndiswrapper working.

run this:

Code:

sudo gedit /etc/init.d/wirelessfix.sh

and paste this:

Quote:
#!/bin/bash

modprobe -r b44
modprobe -r b43
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44
into the file. Save and close it.

Next, run this:

Code:

cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh

and finally, this:

Code:

sudo update-rc.d wirelessfix.sh defaults

Restart and enjoy your wireless!  Works with 8.04 and 8.10 both Ubuntu and Kubuntu.

CRS

---

### Post by LastChildren on 2008-11-12
alas, no luck.  i finally have my device back (wla0) but no networks detected.  i even installed wicd to see if that helped, but still detecting nothing.  is this a problem with the new linux-kernel perhaps?  even on my pc desktop which is running Kubuntu 8.10 and using a Netgear wireless card w/ndiswrapper, when I click on Knetworkmanager, only one wireless network shows up, my home network, whereas when I was running 8.04 knetworkmanager and gnome-network manager (i was running Ubuntu 8.04 on my laptop) they would both pick up 4 or 5 networks from around my neighborhood.

---

