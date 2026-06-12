---
title: "TX1000 egalax final solution!"
date: 2008-06-16
forum: Hardware
---

### Post by edu90cb on 2008-06-16
Hello people, finally I found out the way to configure egalax just with a click and a pair of command lines.! here's the solution.

Go to egalax home page.

[www.eeti.com.tw](www.eeti.com.tw)

Enter to page, support/touchsolution/drivers; go to linux page, and download beta driver. once downloaded just extract it to any folder, i preffer to extrac it to home.

now open console and CD to the folder where you extracted the tar.gz.

now type sudo sh setup.sh... follow graphical instructions on installer, reboot, and that's it, you've your egalax installed. to callibrate just go to /usr/local/touchkit_x14/touchkit...!

Hope to help someone here!

---

### Post by Maceatron on 2008-08-31
Thanks edu90cb!!

I have a tx1001au and have been struggling to get the touch screen working!
The install was easy, though i did have to confirm that the touchscreen was USB and not RS232...

thanks mate!

---

### Post by ehellmer on 2008-10-12
I did the install and then rebooted, but I'm not able to calibrate it. I get cannot execute binary file.

---

### Post by cta16 on 2008-10-15
> **ehellmer said:**
> I did the install and then rebooted, but I'm not able to calibrate it. I get cannot execute binary file.

What do you mean you can't execute binary file? Does your touchscreen work? After I installed Touchkit, the screen gave me inverse Y values but the correct X values. To configure it, I had to go into the TouchKit folder but it was locked and I was not the owner. To change the owner:

```
sudo chown YOUR_USERNAME_HERE /usr/local/TouchKit_x14/
```

Then, all you need is to run the configuration tool:

```
sudo /usr/local/TouchKit_x14/TouchKit
```

Note: When you are configuring on the screen with the teal background, you have to tap and hold it until the crosshair goes away.

---

### Post by ehellmer on 2008-10-18
i tried to doing the chown, but it said i was missing the operand, i checked the help, but wasn't sure which one I needed to use.

---

### Post by cta16 on 2008-10-23
> **ehellmer said:**
> i tried to doing the chown, but it said i was missing the operand, i checked the help, but wasn't sure which one I needed to use.

That's where I got my code from. In the help section at the very bottom, there is three examples. I just followed the structure of the first one. sorry I'm pretty new to Ubuntu too so I'm not sure how I can help.

---

### Post by ehellmer on 2008-11-06
I got it working, thanks so much! :)

---

### Post by edu90cb on 2008-11-07
Sorry guys, i'd posted the thing and forgotten it, to find the usr/bin... the easyest way was to type in terminal: sudo konqueror that's how i do it, I just hate large commands. BTW, i'm not using ubuntu anymore, i liked but i hated it.! So I turn my tx1000 to Mandriva, it works better. Yes this is a forum for ubuntu but.. we've to be honest. Mandriva is better for our tx1000.

---

### Post by gameboymg on 2008-11-08
Hi,

I am just not able to calibrate the Touch Screen on my TX1220us.

I have a screen resolution of 1280x800
I am using Ubuntu 8.10

I have attached the results of a 25 point calibration.

I'd be very grateful if someone could help me out.

Also - I am able to calibrate a 200x200 pixels perfectly however when I increase the scope it goes berserk.

Thanks.
Kobe

---

### Post by romerotek on 2008-11-09
at first thanks for this col stuf.. i installed the usb driver successfully n is nw working... m using tx1218au.. with ubuntu 8.04... i also calibrated it.. 
  the system worked wel aftr the installaton, i can also use the touchscreen, but when ever i uses mouse aftr using the touchscreen everything except the mousepointer hangsup... i mean i can move the pointer but cannot select any thing on the screen.. same vth the case of touchscreen..
   also my usb doesnot recognises pendrives.. usb mouse connected is working... but pendrive or external harddisks are not working...:(

---

### Post by ccw127 on 2008-12-10
Okay, so my touchscreen was working great with 8.04. Upgraded to 8.10 and I lost it. I tried to fix it on my own, no success. Tried the official egalax driver from their site, now when I touch anywhere on the screen, my mouse jumps to a point an inch off the bottom of the lower left corner of the screen. Doesn't matter where I touch or move.

Ideas???

Chris

---

### Post by Alejandro Nova on 2008-12-16
$ sudo apt-get install xserver-xorg-input-evtouch

...and forget about eGalax ;)

---

### Post by ccw127 on 2008-12-16
Just one problem... evtouch is installed already... when i use the System-> Administration-> calibrate touchscreen.... it tells me i dont have a evtouch compatible touchscreen. When I use the egalax program it sees the touchscreen device but will not calibrate correctly.

Chris

---

### Post by Alejandro Nova on 2008-12-17
Interesting.

```
root@faeris:/dev/input/by-id# ls -l
total 0
lrwxrwxrwx 1 root root 9 2008-12-17 07:04 usb-eGalax_INC._USB_TouchController-event-mouse -> ../event3
lrwxrwxrwx 1 root root 9 2008-12-17 07:04 usb-eGalax_INC._USB_TouchController-mouse -> ../mouse2
lrwxrwxrwx 1 root root 9 2008-12-17 10:19 usb-Kensington_Kensington_USB_Wheel_Mouse-event-mouse -> ../event2
lrwxrwxrwx 1 root root 9 2008-12-17 10:19 usb-Kensington_Kensington_USB_Wheel_Mouse-mouse -> ../mouse1

```

This is where I'm looking at: the event interface. As you can see, the TouchController is /dev/input/event3 and is symlinking to /dev/input/mouse2.

All my evtouch experiments are being conducted with a mutilated xorg.conf, that I'm going to transcribe for you. Perhaps you followed the HOWTOs and have a fully configured xorg.conf for eGalax. That's not the way to go for the Ibex: the Ibex changed it all.

Check this against your xorg.conf, and come back if you keep having trouble.

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x3333"
	Option  "UseEvents"			"True"
	Option	"NoLogo"			"True"
	Option	"RandRRotation" 		"True"
	Option	"PixmapCacheSize"		"3000000"
	Option	"OnDemandVBlankInterrupts"	"True"
EndSection


```

---

### Post by ar-grig on 2008-12-26
thanks for the advice !
my touchscreen finally working !

BUT ...

I have calibration issues : after several times calibration mouse jumps on wrong place (about 7 mm offset radius) when I am tap near the screen edges ......

What can I do ?
thanks

---

### Post by Alejandro Nova on 2008-12-28
Select the Calibrate Touchscreen option in your System GNOME menu, and follow carefully the instructions. You'll see nine black crosses, and first, carry your stylus from the center to the border. You must touch all of them. Later, you press Enter and let the computer compute your pen movements. When it's finished, you'll see that one of the nine crosses will turn red. Press the crosses with your pen as they turn red.

I'm crossing my fingers because I'm waiting for Ubuntu developers to catch with evtouch 0.8.8. 0.8.7 works good enough, but 0.8.8 works a lot better. I'm getting perfect calibrations with both. You can get evtouch 0.8.8 from:

[http://www.conan.de/touchscreen/evtouch.html](http://www.conan.de/touchscreen/evtouch.html)

(Everyone knows about this address, except Debian Sid maintainers... :()

---

### Post by ar-grig on 2008-12-28
Thanks for you answer !

I have done exactly what you write, before posting previous message.
Callibration was ok and pointer was moving just where i tap in area near the center.
But when i am tapping near the edges the pointer moves a wrong place with about 7mm error. Error increases from 0 to 7 when i am moving from center to corner.

Evtouch 0.0.8 is not working for me -- i have copied appropriate file evtouch_drv.so to the xorg directory and X server can't load this driver. after installing old version all works just like it was before.

What else can i do ?
Thanks

---

### Post by ar-grig on 2008-12-28
thanks for you answer !

before writing my first message i have done exactly what you say, but i have got the touchscreen working good in center but not so good near the eges -- i have increasing tap/point difference 0-7 mm when moving from center to edges.

evtouch.0.0.8 isn't working for me -- X server can't load the driver. I have just copy/paste the driver to appropriate directory, but it couldn't be loaded according to logfile

what else can i do ?
thanks

---

### Post by Alejandro Nova on 2009-01-01
Use evtouch 0.8.7 for the time being. I also had some troubles with evtouch 0.8.8. I've filed a bug against xserver-xorg-driver-evtouch in the Debian bug tracking system. I hope they catch the update and make a Debian Sid (and Ubuntu Jaunty) package soon, so, when they have the package ready, we will be able to use it.

About your error: calibrate again. I had to do it 3 or 4 times before I had an acceptable calibration for my touchscreen :(

---

### Post by momerat99 on 2011-08-12
> **edu90cb said:**
> Hello people, finally I found out the way to configure egalax just with a click and a pair of command lines.! here's the solution.

Go to egalax home page.

[www.eeti.com.tw](www.eeti.com.tw)

Enter to page, support/touchsolution/drivers; go to linux page, and download beta driver. once downloaded just extract it to any folder, i preffer to extrac it to home.

now open console and CD to the folder where you extracted the tar.gz.

now type sudo sh setup.sh... follow graphical instructions on installer, reboot, and that's it, you've your egalax installed. to callibrate just go to /usr/local/touchkit_x14/touchkit...!

Hope to help someone here!
using ubuntu 10.10 32bit on eeepc 1000he 4-wire resistive touch and this worked like a charm THANK YOU THANK YOU THANK YOU didnt wanna have to go back to windows

---

