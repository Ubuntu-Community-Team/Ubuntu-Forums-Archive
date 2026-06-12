---
title: "NETGEAR WNA1100 to work on 3 different laptops everytime with multiple variants"
date: 2010-07-06
forum: Hardware
---

### Post by ironhoof on 2010-07-06
I can say for sure that NDISWrapper will handle the NETGEAR WNA1100
I wrote this for anyone looking to get it working. There are variations in how it runs on each computer but I have gotten it to run quite nicely on all three plus my desktop! I know some people can't get it to work I can't promis this will work for everyone but it never hurts to try.

This is pretty standard stuff but I wrote it anyway in case
someone new to this stumbles across it.

Here is exactly what you need:
You need to get WNA1100_v1.1.3.21_Setup.exe driver

You need to extract this using windows XP/Vista 32 if you have it.
You can also use a virtual boxed windows XP/Vista, this is what did.

It will place its files in c:/program files/NETGEAR
You need the DRIVER directory which is in the sub folder of
/NETGEAR  

like so c:/program files/NETGEAR/WNA1100/Driver

copy this to a pen drive if your using Virtualbox. You can otherwise burn or whatever you like.

You will need these files:

netathuw.inf
athuw.sys
netathuw.cat  <- ( you may or may not need this just leave it )

Now make sure you get the latest NDISWRAPPER from sourceforge or where ever. I used 1.56 if you have it get it anyway... be sure.

You will need to make sure your system is up to date update your system if you been putting it off. Double click this extract to documents or where ever (you can delete it later) in the extracted folder type in terminal:

# make install

You should do the following as root

now to extract the drivers go to your driver folder and the sub folder WinXP2000 
/NETGEAR/WNA1100/Driver/WinXP2000
where the actual files are located and open a terminal.

use ndiswrapper to extract them

# ndiswrapper -i netathuw.inf

It will list quite a few extractions which I don't have with me.

Plug in your NETGEAR WNA1100 USB DEVICE and type 

# lsusb

Make sure it is in USB device list.

You should see NETGEAR in the list.

0846:9030 is what mine was listed as.

Next using sudo

# ndiswrapper -m

To give the device files an alias of wlan0 or so depending if you have more than one. Now type

# ifconfig

You should see wlan0 in the list with the device next to it.
Next type

# ifconfig wlan0 up
(You may have to type sudo ifconfig wlan0 up I did on one machine odd...)

It will load your driver and start it up.

LEFT click your network connection after a few seconds and you should see your Wifi hotspot name or whatever in the list.

Click it and fill out password information so forth.

This will be your auto connect for this device. However you
will have to do a ifconfig wlan0 up every time you reboot/shutdown.

There is a method to get this to start automatically but I don't
use it but you can find the information quite easily.

# modprobe ndiswrapper

Hope it works for you

---

