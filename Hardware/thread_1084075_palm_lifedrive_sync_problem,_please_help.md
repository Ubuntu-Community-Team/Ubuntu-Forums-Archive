---
title: "palm lifedrive sync problem, please help"
date: 2009-03-01
forum: Hardware
---

### Post by pumatheman on 2009-03-01
I'm an absolute  beginner on linux and I've installed the 8.10 wonderfull ubuntu! with gnome-pilot, it founds the LD when I plug it, I can't configure it becouse as I press the hot sync button an error message came out  sayng:

[I](traslated from italian) 
connection failed on /dev/ttyUSB1 check the configuration becouse the syncronization has been request with "old style" usb serial but the usbserial kernel wasn't been loaded[/I]


what this means? 
I've also followed the suggestions of 
[https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)
 but I always have had the same problems

---

### Post by sgosnell on 2009-03-01
I never use a USB sync, I sync via wifi.  On the Lifedrive, set the hotsync to Network, then open Primary PC Setup and put in the local network IP address of the computer you want to sync with.  THe rest of the entries don't matter.  Turn on wifi and start the hotsync, assuming everything is running on the PC.  The Lifedrive should sync easily.  I haven't tried a USB sync in so long I don't even remember how to set it up.

Some investigation shows that when you set up the Palm, you can click on the Device tab and you can select one of several radio buttons.  For the Lifedrive, you need to select either USB or Network, not Serial.  That's for older devices that used an RS-232 serial connection.  It sounds like that's what is happening to you.  Check and make sure the correct choice has been highlighted on the Device tab.

---

### Post by pumatheman on 2009-03-02
thanks for you reply, but I don't have wifi :(

---

### Post by pumatheman on 2009-03-02
"How I did it" on 8.10
 di Victor Von Pumatheman :lolflag:

disinstalled evolution
disinstalled kpilot
disinstalled jpilot
followed the precious lines of  [https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)

in this steps:

Open a terminal window  Type the following line:    gksudo gedit /etc/udev/rules.d/10-custom.rules

Insert the following line into the empty file:

BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="666"

Open a terminal window  Type the following line:    gksudo gedit /etc/modules

Add after last line:            visor

and save the file.

Open a terminal window  Type the following line:    sudo modprobe visor

after I have reisntalled evolutio e jpilot

it's wonderlully working :guitar:

---

