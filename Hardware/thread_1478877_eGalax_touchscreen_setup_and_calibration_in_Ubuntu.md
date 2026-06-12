---
title: "eGalax touchscreen setup and calibration in Ubuntu Lucid (with calibration tool)"
date: 2010-05-10
forum: Hardware
---

### Post by naugtur on 2010-05-10
[not sure, but it might work with earlier versions.]

Without installing the eGalaxTouch support I got everything working  great with default evdev setup in ubuntu 10.04 adding these two commands  to fix the old problems with rotation / swapped axes. Correct tap  behaviour was present out-of-the-box.

```
xinput set-prop --type=int --format=8 "eGalax Inc. USB  TouchController" "Evdev Axes Swap" 1
```fixed the swap
If Y is inverted:
```
xinput set-int-prop "eGalax Inc. USB TouchController" "Evdev Axis Inversion" 8 0 1
```
and then calibration:
```
xinput set-prop --type=int --format=32 "eGalax Inc. USB  TouchController" "Evdev Axis Calibration" 57 1938 162 1979
```to get Your own calibration numbers You need this:
[http://www.freedesktop.org/wiki/Software/xinput_calibrator](http://www.freedesktop.org/wiki/Software/xinput_calibrator)

building from source:

#for fresh desktop install You'll need some packages:
```
sudo apt-get install g++ autoconf libtool xorg-dev
```unpack the calibrator, cd to the folder and run 
```

./autogen.sh
make

```cd to the src folder and run
```
 ./xinput_calibrator_x11 
```do the clicks and it will write Your config to console.

binary built on ubuntu 10.04 32bit 
[ATTACH]156303[/ATTACH]

---

### Post by cywhale on 2010-05-15
Does not work for me on Lucid Lynx, full updated and a eGalax Touchscreen (xinput name "eGalax Inc. Touch") in my Samsung NC10 :(

Tried every hint I found via searchengine (bug reports on this, threads, even a newly developed driver) to get the touchscreen working with evdev (read somwhere this should be more responsive and with much less wakeups than original eGalax driver), nothing works:

The cursor moves to upper left corner (or somwhere else after trying to calibrate via xinput), calibrate_x11 recognizes only click #1 :(

Only way to get the touchscreen work with Lucid for me is to use the original 32Bit beta-driver -> "xinput --list" shows 2 eGalax-devices -> deactivate the device managed by evdev (device 13 here)-> calibrate with eGalax tool -> done.

Do you use any other hints/quirks to get this working with evdev only and Lucid???? Do you use a xorg.conf ? 

I'd love to uninstall the original eGalax driver... :(

---

### Post by merajchhaya on 2010-05-16
I'm facing the same problem as the person above.

I have a Lilliput EBY701, using eGalax drivers, on a desktop computer.

I can only calibrate to one point, and even before doing this, regardless where I touched, the pointer would remain in the upper-left position of the screen.

Could you please mark this thread as unsolved? Thanks

---

### Post by aeqel on 2010-05-16
> **merajchhaya said:**
> I'm facing the same problem as the person above.

I have a Lilliput EBY701, using eGalax drivers, on a desktop computer.

I can only calibrate to one point, and even before doing this, regardless where I touched, the pointer would remain in the upper-left position of the screen.

**Could you please mark this thread as unsolved? Thanks**

+1

I got a Gigabyte T1028x (eGalax touch screen) and get this "jump to top left" behaviour since upgrading to 10.04.

In 9.10 UNR I got the touch screen working fine using these instructions:
[http://samiux.blogspot.com/2009/12/howto-ubuntu-910-on-gigabyte-t1028x.html](http://samiux.blogspot.com/2009/12/howto-ubuntu-910-on-gigabyte-t1028x.html)

I attempted to use those again to no avail in 10.04.

I notice that I don't get the "Calibrate Touchscreen" option under administration anymore either even after following the instructions in the link.

---

### Post by reckik on 2010-05-21
Im having some issues after updating too. 

> xinput set-prop --type=int --format=32 "eGalax Inc. USB  TouchController" "Evdev Axis Calibration" 57 1938 162 1979

unable to find device eGalax Inc. USB  TouchController

I tried it through the /dev/input/by-id/usb...etc got the same result

using the attatchment calibrator of Naugter recognized the points very good, but didnt seem to write.

In 9.10 i ended up manually editing my numbers in the evtouch configuration file. Is that still being used in 10.04? 

> Only way to get the touchscreen work with Lucid for me is to use the original 32Bit beta-driver -> "xinput --list" shows 2 eGalax-devices -> deactivate the device managed by evdev (device 13 here)-> calibrate with eGalax tool -> done.

How did u do that? cause i cant use it at all now.....

---

### Post by cywhale on 2010-05-22
First of all: using the original egalax driver is suboptimal for me as the touchscreen stops working after a while, using it with easystroke somehow causes the touchscreen to quit working, too. That's the reason I'm trying to get the touchscreen to work with evdev/evtouch...

[B]Original egalax driver:
[/B]
1) Download and extract the driver
2) Create xorg.conf if does not exist
3) Install original driver via setup.sh

3.1) Edit xorg.conf, section for mouse changed to use numbered input device instead of "dev/input/mice", egalax driver to use "/dev/usb/hiddev0":

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
        InputDevice "EETI" "CorePointer"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "ServerFlags" 
	Option "BlankTime" "5" 
	Option "StandbyTime" "0" 
	Option "SuspendTime" "0" 
	Option "OffTime" "0" 
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri"
	Load  "dbe"
	Load  "glx"
	Load  "dri2"
	Load  "extmod"
	Load  "record"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/event8"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 945GME Express Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

### Touch Configuration Beginning ###
Section "InputDevice"
        Identifier "EETI"
        Driver "egalax"
	Option "Device" "usbauto"
        Option "Device" "/dev/usb/hiddev0"
        Option "Parameters" "/var/lib/eeti.param"
        Option "ScreenNo" "0"
        Option "SkipClick" "0"
EndSection
### Touch Configuration End ###

```
4) Reboot
5) Run "xinput --list" in (gnome-)terminal, there should be some touchscreen devices, found "egalax" and 2 times "eGalax Inc. Touch" in the list. "egalax" is the new xorg.conf defined original driver and I had to deactivate the other devices via
6) "xinput -set-prop 11 "Device Enabled" 0", 11 is the device id provided by the "xinput --list" command, instead of the number the id string could be used, too.
7) "sudo eGalaxTouch" to do the calibrating stuff.

After this the touchscreen works for a while, then stops working, after a reboot the calibration is ok, after deacticating the other devices the touchscreen works for a while,...

Alternative method to stop xorg from loading evdev for the two unneccessary devices ist to edit "/usr/lib/X11/xorg.conf.d/05-evdev.conf" and change the two touchscreen relevant sections at the end of the file (commented them out so only device created is the one defined in xorg.conf -> "egalax").

[B]Did anybody get this to work with evdev driver only??
[/B]

---

### Post by cywhale on 2010-05-22
Ok then...

**made my "Egalax Inc. Touch" (-screen) work with module "usbtouchscreen":**

Preferences: Fully updated Ubuntu Lucid Lynx, Samsung NC10, Touchscreen \w Xinput-ID "Egalax Inc. Touch"

1) Edited /etc/default/grub adding "usbhid.quirks=0xeef:0x1:0x40" to the boot parameters line so it looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbhid.quirks=0xeef:0x1:0x40"
```
Then "sudo update-grub" in (gnome-)terminal.

2) Edited /etc/modules, inserting
```
usbtouchscreen
usbhid
```
right after the line containing "lp". Important: "usbtouchscreen" MUST be loaded before "usbhid"

3) Reboot

4) Calibration using xinput_calibrator_x11 from first post in this thread

That's it. The touchscreen seems to work as intended, left-click, moving windows, using easystroke, drawing with xournal - all simple tests are looking good.

[B]Does anybody know how to get right-click functionality by touching > 3sec. with module usbtouchscreen ?
[/B]
All the used hints above were gathered in many searches about the egalax touchscreen, it seems i never tried the right/working combination...

---

### Post by cywhale on 2010-05-31
Hmmm...
after some days I must correct my last post - the touchscreen seems to work randomly - sometimes from first login after boot, sometimes not, sometimes it stops working after some time again... :(

With the kernel option mentioned above this also occurs using evdev only (no usbtouchscreen module needed)... :(

---

### Post by border on 2010-06-03
> **aeqel said:**
> 
In 9.10 UNR I got the touch screen working fine using these instructions:
[http://samiux.blogspot.com/2009/12/howto-ubuntu-910-on-gigabyte-t1028x.html](http://samiux.blogspot.com/2009/12/howto-ubuntu-910-on-gigabyte-t1028x.html)

I attempted to use those again to no avail in 10.04.

I looked at that link, and it's obvious that it does not work in 10.04 since hal is not used anymore (deprecated) and since they use hal rules inthere...

But I adapted it to 10.04 (with xorg.conf.d) and it works for my touchscreen!!!
I have a Samsung Q1 ultra. My touchscreen is a
ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
as reported by lsusb
and udev reports it as Touchkit Touch (that's how I found it in Xorg.0.log)

So here's the configuration I added to /usr/lib/X11/xorg,conf.d:
file name 11-touchkit.conf

```
Section "InputClass"
	Identifier "Touchkit Touch"
	MatchIsTablet	"on"
	MatchDevicePath "/dev/input/event*"
	Driver 	"evtouch"
	Option	"ReportingMode"	"Raw"
	Option	"Emulate3Buttons"
	Option	"Emultate3Timeout"	"50"
	Option	"SendCoreEvents"	"On"
	Option	"TapTimer"		"200"
	Option	"LongTouchTimer"	"400"
	Option	"MinX"			"145"
	Option	"MinY"			"193"
	Option	"MaxX"			"3973"
	Option	"MaxY"			"3898"
EndSection
```

I got those evtouch options out of an old xorg.conf file from a configuration package specially made for a q1ultra which existed in the ubuntu 8.04 time.
And now it runs perfectly!!!
I also calibrated it using the utility in the first post, but I don't think that was necessary.

Thanks everybody for your contributions
I'm glad I got everything together finally
And I hope that it can be of use to anyone

Edit: To be clear to anyone, I also was troubled by the cursor stuck in upper left corner 'bug' after clicking once. So I can advice everyone with that problem to install xserver-xorg-input-evtouch and add a file like mine to the directory xorg.conf.d

---

### Post by Wandering Methodist on 2010-06-04
Worked a treat :D on my eeePC 701 and I had almost given up and was getting ready to get rid of the touchscreen

Just one comment, if just copy and pasting from the original post there is an additional space between USB and TouchController which I needed to remove

---

### Post by Cka3o4nik on 2010-06-05
Hi!
Works for me too :-) Many thanks, border!

Off: by the way, does anybody know correct keyboard mapping name for Q1U (or how to tune default)?

---

### Post by liviococcia on 2010-06-08
Hello Cka3o4nik, thanks for all the help from this thread, and the other post you sent on my thread, i've just a request for some more info please.

Is there a working Graphic calibration tool specifically for the Samsung Q1 ultra under Ubuntu netwbook Edition 10.04 as you mention the use of one that you had used, or, were the settings in the '11-touchkit.conf' file worked out through personal diagnosis while testing the Q1 Ultra's touch-screen, the reason i ask is, i can't seem to follow or work out what's the Samsung Q1 Ultra's calibration tool that's being refered to in this thread, or it's instructions on how to install it.

I just wanted to see if i could get the touch-screen to be a little more precise.

Kind regards
Livio

---

### Post by Cka3o4nik on 2010-06-08
Hello
> **liviococcia said:**
>  Is there a working Graphic calibration tool specifically for the Samsung Q1 ultra under Ubuntu netwbook Edition 10.04 as you mention the use of one that you had used

Oh, there's some misunderstanding. I only referenced border's method to solve the problem. On my Q1 I just made that config and it helped. I didn't use any calibration tools. Only tried several configs before.

But I seriously doubt someone would develop calibration tool specially for Q1 under Ubuntu. There might be some common tools.

> , or, were the settings in the '11-touchkit.conf' file worked out through personal diagnosis while testing the Q1 Ultra's touch-screen,

You should ask the author of config, I suppose :-)

> the reason i ask is, i can't seem to follow or work out what's the Samsung Q1 Ultra's calibration tool that's being refered to in this thread, or it's instructions on how to install it.

I just wanted to see if i could get the touch-screen to be a little more precise.

I also plan to do precise calibration, but later. I need to get WiFi working stable first. Does your's work properly? Mine looses connection in a minute it connected to network. Getting fresh MadWifi drivers didn't help.

---

### Post by liviococcia on 2010-06-09
cheers for that Cka3o4nik, i use a UK 'T-Mobile' mobile broadband dongle connection, i just followed the network manager/tools setup process and it setup without a hitch, i've had no issues using this connection, i have had the unit connected by 'Ethernet' and not had problems either, but have not tried a 'Wireless' connection through any network's routers as yet, i will give this a go, i'll try either later tonight or tommorow (Thursday) using a friends router he's on a 'Plusnet' connection, and his router's made by 'Huawei' i think.

I'll post back the results.
regards

---

### Post by Cka3o4nik on 2010-06-09
Thanks, liviococcia. I'm looking forward for your results

---

### Post by border on 2010-06-09
I got these calibration values from a config file which was included in hardy [http://packages.ubuntu.com/hardy/ume-config-samsung-q1-ultra](http://packages.ubuntu.com/hardy/ume-config-samsung-q1-ultra)
If my information is correct the q1 ultra was the main development platform for the ubuntu mobile edition version of hardy heron.

The calibrations options are ok, but not quite that, they seem a little bit of at the right side of the screen, which makes it difficult to scroll windows. I have had a little bit of succes adjusting the max X value a little. More details on that later on.

There seems to exist a calibration tool for the evtouch driver (the driver used in the config I posted). 
/usr/lib/xf86-input-evtouch/calibrate.sh
But that doesn't work. That could be because it uses hal, and hal is not used anymore in lucid. And the last update the package had was in 2008.
So I guess there is not much hope in it getting an update so the calibration method works.

The calibration program explained in the OP of this thread does work, but it's values are not usable as far as I know.

Maybe it is time to create a new thread with all this information about the q1 ultra, since we are hijacking this thread more or less (MODS?)
Maybe I'll create a new one tomorrow.

cheers

---

### Post by Cka3o4nik on 2010-06-09
+1 about creating new thread for Q1.

Is WiFi connection on your's Q1U working stable?

---

### Post by liviococcia on 2010-06-10
Hello Cka3o4nik, I've just check my wireless connection, the ISP was Plusnet, and i know this to be a recent broadband account of a friends, i'm guessing it's was there latest 'Wireless' router that i was using, i didn't make a note of the model though.

I can only describe the router, it's Apple mac glossy white finish with rounded corners, and a single ariel, all the lights are very small and green when fully syncronised, there located on the top, and to the corner of the router, diagonally oposite to the ariel.

It was sited in his basement area, and i was using the Q1 Ultra in the loft of the house when i first chose the plusnet connection and put in the wireless security 'key', it connected with no problems.

I did some browsing for around 2 hours, and then went to the 'Update manager' for any new updates, there were 34 and they were mainly 'OpenOffice', Chromium browser and 'Rythembox' plugins, from the distance of the router and my location the download rate did fluctuate, jumping around '5000 B/s' going upto '35 Kb/s', but i notice the signal bar's of the 'Network connection' icon kept increasing, then decreasing constantly.

As the updates were being downloaded. i decided to move the Q1 Ultra closer to the router, so i went into the basement, i notice that although the download rate had increased, going between 40 Kb/s and 198 Kb/s, the 'Network connection' signal strength idicator bars at this location were now full, and stable though, and 'Update Manager' completing all it's downloading, and installing took around 1 hour to do, i then did a little more web browsing, about an hour, and then disconnected the Plusnet connection.

What i would mention is, that while i was using the Q1 Ultra via it Wireless connection, i found it was slightly slower, as if running the Wireless adapter with a connection running through it was using more memory, even though i always have the wireless adapter turned on, though i don't have a router to use on it.

I would also mention that my Q1 Ultra has been fitted with the maximum memory modules allowed in it, and that i did have BIO's updates installed via the Samsung Update Plus software when it was running Windows XP, i ran the Samsung Update check on a regular basis, i've only been running Ubuntu Netbook Edition 10.04 for around month, or just over.

After checking if you have latest BIO's version, and installing it if you don't, i would then go back into the BIO's again and make sure to 'Load Default settings', and 'Save and Exit', just incase something has changed, or was never quite right with the Wireless adapter in the settings for running Ubuntu.

I then delete any current network connections you have, and, any old Wireless or Mobile connections you previously had used, through the 'Network Connections' software, then restart the Q1 ultra, i wouldn't setup a Wireless connection again on the router your having these issues with, but would try someone elses router first, this may show the problems with your router.

If doing the above did point to the router, i'd first get another Microfilter, and would unplug any phones and turn any 'cordless' phones and there 'handsets' off completely, leave them unplugged for now, check all the connections between the BT socket a 'new' Microfilter and the router, then ask a friend to 'Wirelessly' connect to your router (someone with a dual 'OS' (Win/ubuntu) computer would be best, or using a 'Live' Ubuntu version), if they experiance wireless issues, i do a 'full reset' of the router to make sure it's set to it's defaults (make sure you have the 'Default' WAP/WEP security access keys, your router manufacturer 'defualt' one for your model, your ISP's original one, and the one you might have created yourself before resetting the router).

If they didn't experiance any problems connecting, after using there computer for a bit, and while they are still connected to your router, setup your connection on the Q1 Ultra, if you are still suffering the same problems then you know it could really only be corruption somewhere in the Ubuntu networking part of the software, or it's hardware drivers settings, but give it another check using a Ubuntu Netbook Edition or Ubuntu in a 'Live' CD run, and see if it runs Ok this way, if it does, then it has to almost certainly be the Wireless driver settings or the Wireless Hardware driver's it's using.

If you find that you are both connecting ok, i know this may sound crazy but just try a few household electrical items while you are still connected, like microwaves, coffee machines, turn off and on Fridges and Freezers, and game consols. My sister had a strange problem with both here Wireless router from Sky, an XBox 360 and an electric expresso coffee machine, even though the household wiring was all new and to spec, if she turned any of these items on her wireless connection would drop for some strange reason.

Hope something here might be of help

regards

---

### Post by border on 2010-06-12
Hello,

Information for the Samsung Q1 Ultra now goes here:
[http://ubuntuforums.org/showthread.php?t=1506246](http://ubuntuforums.org/showthread.php?t=1506246)

to make it clear that it is a different subject than the one of the OP.
Maybe it's handy to repeat the interesting stuff there so it's bundled at 1 place.

cheers

---

### Post by Cka3o4nik on 2010-06-12
Hello liviococcia, I answered your message at a new thread ([http://ubuntuforums.org/showthread.php?t=1506246](http://ubuntuforums.org/showthread.php?t=1506246)).

---

### Post by reckik on 2010-06-15
After much installing and trying other drivers my Lucid sytem kept freezing up, so i am using crunchbang now, which i used before installing my touchscreen. 

The touchscreen is working good sofar, at least no freezing which my Ubuntu Lucid just kept doing. The only thing is the calibration numbers wont stick. The commands of the first post worked great, but i after each reboot i have to give the command seperatly.
Anyone know how to keep these after reboot?

---

### Post by enoch.brown on 2010-06-19
Hi all,
I have a Gigabyte T1028X with the eGalax touchscreen. I just installed a fresh install of Lucid on it. I have tried everything in this post to set it up, however whenever I touch the screen the cursor flits around in seeming random patterns. 

Thanks in advance,
Enoch

---

### Post by cywhale on 2010-06-19
@border: Thank you very much, solved the problem with my samsung nc10 + eGalax touchscreen with
Once again I installed evtouch:
```
~$ sudo apt-get install xserver-xorg-input-evtouch
```

Then created the Xorg config file:
```
~$ sudo gedit /usr/lib/X11/xorg.conf.d/11-touchscreen.conf

```

```
Section "InputClass"
	Identifier "Touchkit Touch"
	MatchIsTablet	"on"
	MatchDevicePath "/dev/input/event*"
	Driver 	"evtouch"
	Option	"ReportingMode"	   "Raw"
	Option	"Emulate3Buttons"
	Option	"Emultate3Timeout"  "50"
	Option	"SendCoreEvents"    "On"
	Option	"TapTimer"	    "90"
	Option	"LongTouchTimer"    "150"
        Option  "MinX"              "108"
        Option  "MinY"              "124"
        Option  "MaxX"              "1835"
        Option  "MaxY"              "1970"
#	Option  "Calibrate"         "1"
	Option  "SwapX"	            "1"
	Option	"SwapY"		    "1"
	Option	"Rotate"	    "ccw"
EndSection
```

I had to rotate the screen orientation using the "Rotate" option  and to calibrate one time with the calibration tool included in the latest evtouch-package ([http://www.conan.de/touchscreen/evtouch.html]("http://www.conan.de/touchscreen/evtouch.html")) as my old values did not work anymore.

Now the screen works fine for 4 days, surviving suspend/resume/reboot - no problems until now.

Easystroke works great, now I have to figure out some good values for tap timing, I'd prefer the touchscreen to recognize a touch immediately AND beeing able to initiate a right-mouse-click - with TapTimer 90 this is nearly impossible...

After this I'll finally think about my planned NC10/Tablet mod again... :)

Thank you very much

---

### Post by Cka3o4nik on 2010-06-19
> **border said:**
> 
So here's the configuration I added to /usr/lib/X11/xorg,conf.d:
file name 11-touchkit.conf

```
Section "InputClass"
...
	Option	"MaxX"			"3973"
...
EndSection
```

I've tried some values for more precize X axis positioning and discovered **MaxX** value **3950** (for Q1 Ultra). Now cursor is exactly at stylus position at the right side of the screen.

---

### Post by cywhale on 2010-06-19
Must correct myself again - TOuchscreen DID work for some days, right after my last post I tried to finetune the calibration and now the screen does not do anything anymore :(
I think I give up on this...

---

### Post by aeqel on 2010-06-22
> **border said:**
> I looked at that link, and it's obvious that it does not work in 10.04 since hal is not used anymore (deprecated) and since they use hal rules inthere...

But I adapted it to 10.04 (with xorg.conf.d) and it works for my touchscreen!!!
I have a Samsung Q1 ultra. My touchscreen is a
ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
as reported by lsusb
and udev reports it as Touchkit Touch (that's how I found it in Xorg.0.log)

So here's the configuration I added to /usr/lib/X11/xorg,conf.d:
file name 11-touchkit.conf

```
Section "InputClass"
	Identifier "Touchkit Touch"
	MatchIsTablet	"on"
	MatchDevicePath "/dev/input/event*"
	Driver 	"evtouch"
	Option	"ReportingMode"	"Raw"
	Option	"Emulate3Buttons"
	Option	"Emultate3Timeout"	"50"
	Option	"SendCoreEvents"	"On"
	Option	"TapTimer"		"200"
	Option	"LongTouchTimer"	"400"
	Option	"MinX"			"145"
	Option	"MinY"			"193"
	Option	"MaxX"			"3973"
	Option	"MaxY"			"3898"
EndSection
```

I got those evtouch options out of an old xorg.conf file from a configuration package specially made for a q1ultra which existed in the ubuntu 8.04 time.
And now it runs perfectly!!!
I also calibrated it using the utility in the first post, but I don't think that was necessary.

Thanks everybody for your contributions
I'm glad I got everything together finally
And I hope that it can be of use to anyone

Edit: To be clear to anyone, I also was troubled by the cursor stuck in upper left corner 'bug' after clicking once. So I can advice everyone with that problem to install xserver-xorg-input-evtouch and add a file like mine to the directory xorg.conf.d

Thanks Border! This has now fixed my jump to corner behaviour on my T1028x. Now I have a reasonably working touchscreen.

However! Using my stylus the touch screen is accurate in the centre of the screen then it slowly tends to accelerate faster than I move the stylus in any direction from there.

i.e. Going right from the centre with the stylus the pointer slowly gets further and further to the right of the stylus itself.

EDIT: I tried the calibration tool at the start of this thread and created a udev rule, it changed nothing.
I also remember the 9.10 UNR had a touch screen calibration option under the Administration menu which had 9 point calibration. 

I'm pretty sure the only issue now is calibration now.

---

### Post by GroovingClockwork on 2010-07-18
For me and my Q1 naugtur's original solution (see first post) worked perfectly :)

To call xinput every time the system initialises, I added the "xinput ..." line to the graphical Startup Programs manager (in Mint; I bet there's a similar thing in Ubuntu).

Works good, but would there be a way to run this straight when X initialises, some setting or script? As I have it now, the correct calibration does not get set until after login.

---

### Post by WillardPotter on 2010-08-12
Has anyone managed to get the eGalax screens working properly? I just recently put one in my Asus Eee 1005HAB. I was able to install the eGalax driver without any problem. I was even able to calibrate with their tool. It took running the eGalaxTouch tool as root for it to work correctly. When I wasn't running it as root, it would let me get through a few points and then just completely crash, leaving an error in the terminal.

The calibration seems to have worked fine, but I still have one remaining issue. The whole thing where everyone says the cursor jumps to the top-left of the screen. I got that before the calibration and, although I can touch and move the cursor where I want, it jumps at that top left with every tap, causing it to think i'm doing a drag and highlighting text, icons, etc...

I'm assuming this is just left over from what was originally there on a clean install. Is there any way to remove that? I'm not a noob, but i'm no pro either. Hopefully I can be of some use if anyone needs to know specifics on how I got this far at least.

---

### Post by Cka3o4nik on 2010-08-13
Read the thread above. [http://ubuntuforums.org/showpost.php?p=9406477&postcount=9](http://ubuntuforums.org/showpost.php?p=9406477&postcount=9) solves this problem for Samsung Q1 Ultra, it might suite you too.

---

### Post by ka1axy on 2010-10-20
I've just been through the whole eGalax journey with a Xenarc 700TSV display.  This thread (and some others) was a major part of my finally getting it working (after an entire day of trying things). I'm writing this to summarize what worked for me on an Asus EB1501, running Lucid 10.4 with the Xenarc display. My system also has a USB/Bluetooth mouse and keyboard. The mouse is extra helpful while trying to get things working, and seems to coexist well with the touchscreen.

The key steps were:
- downloading the beta Linux driver (3.03.4510 at this time) from the EETI website:
  [http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm)
- running the unmodified setup.sh script with sudo
- rebooting 
- running the eGalaxTouch command after rebooting and selecting USB and disabling right click
- running the TKCal command and doing a 4-point calibration
- running [FONT="Courier New"]xinput -list[/FONT] and note that there were two eGalax input sources
- adding a startup program: [FONT="Courier New"]xinput -set-prop "eGalax Inc. Touch" "Device Enabled" 0[/FONT]

Disabling the second eGalax input device was the key to eliminating the upper-left pointer issue.  I'm still working to determine exactly where to run this command during startup, as it sometimes seems to lose its effect, but rerunning it *always* removes the upper-left pointer problem.

---

### Post by imato on 2010-12-20
> **enoch.brown said:**
> Hi all,
I have a Gigabyte T1028X with the eGalax touchscreen. I just installed a fresh install of Lucid on it. I have tried everything in this post to set it up, however whenever I touch the screen the cursor flits around in seeming random patterns. 

Thanks in advance,
Enoch

Hi enoch.brown,

I got exact same problem with yours. the mouse cursor is flying around. have you solve your problem yet?

PS. I am not sure which brand of my touch screen. it seems like a oem 8" touch screen.

---

### Post by imato on 2010-12-21
Hi, I have done a lot of search on internet. Finally, I sort it out haha :).

Here is my installation note :

[http://oestudyard.blogspot.co.nz/2009/11/install-egalax-touch-screen-in-linux.html](http://oestudyard.blogspot.co.nz/2009/11/install-egalax-touch-screen-in-linux.html)

---

### Post by Dsky on 2011-03-26
i have a eeepc 901 asus and ubuntu 10.10 netbook with touchscreen

i did this

[http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html)

and then

> Linux driver installer for TouchKitTouch controller 

(I) Check user permission: root, you are the supervisor.
(I) Begin to setup the TouchKitTouch driver.
(I) Found and removed previous TouchKitTouch driver.
(I) Extract TouchKitTouch driver archive to /usr/local/TouchKit32.
(I) Create TouchKit utility shortcut in /usr/bin.
(I) Create TKCal tool shortcut in /usr/bin.
(I) Check X window version: 6.9.0 ~ 7.2.0
(I) Copy X module: x69/egalax_drv.so to /usr/lib/xorg/modules/input.

(Q) Which interface controller do you use?
(I) [1] RS232 [2] PS/2 [3] USB : 3
(I) Using interface: USB
(I) Found a HID compliant touch controller.
(I) Found inbuilt kernel module: usbtouchscreen.
(I) It is highly recommended that add it into blacklist.
(Q) Do you want to add it into blacklist? (y/n) y

(I) Found X configuration file: /etc/X11/xorg.conf.
(I) Removed touch configuration from /etc/X11/xorg.conf.
(I) Add touch configuration into /etc/X11/xorg.conf.

(I) Please reboot the system for some changes to take effect.
(I) After booting, type "TouchKit" to do calibration.


but still "no touch controller found"

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dbe"
    Load  "glx"
    Load  "record"
    Load  "dri"
    Load  "dri2"
    Load  "extmod"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

---

### Post by aanno on 2011-04-14
Hello,

with Ubuntu 10.10 (Maverick) I also was able to use my eGalax touchscreen. This is my /usr/share/X11/xorg.conf.d/40-touch.conf file:

[PHP]
Section "InputClass"
        Identifier "eGalax touch class"
        MatchProduct "eGalax"
        MatchDevicePath "/dev/input/event*"
        Driver "evtouch"
        Option "MinX" "150"
        Option "MinY" "100"
        Option "MaxX" "1900"
        Option "MaxY" "1950"
        Option "ReportingMode" "Raw"
        Option "Emulate3Buttons"
        Option "Emulate3Timeout" "50"
        Option "SendCoreEvents" "On"
        Option "Rotate" "CCW"
        Option "SwapY" "1"
EndSection
[/PHP]

But with 11.04 the 'evtouch' isn't available any more :(
The news is:
[LIST]
[*] The eGalax input device gets detected automatically using the general evdev driver. 
[*] With help of 'xinput' it is possible to configure it (swap, calibration, invert, ...).
[*] BUT there is a nasty hassle with the touchscreen 'button' emulation (see below).
[/LIST]

In 10.10 'evtouch' was kind of clever: if you ticked short onto the screen, it was detected as 'left mouse button'; if you ticked short and then a little longer immediate after that, it was detected as 'right mouse button'. If you touched the screen for longer (and moving the finger/mouse around), **no** mouse event was recorded (as it should be!).

In 11.04, if you touch the screen this will *always* trigger a mouse button event. And because of this, the new state of affairs renders the touchscreen **unusable**.

Anyone with a suggestion?

Kind regards,

aanno

---

### Post by Thomaseov on 2011-04-19
Hi aanno,
I am in exactly the same boat with my egalax touchscreen.  Tell me if you stumble upon a cure for this.
Thomas

---

### Post by Dave911 on 2011-10-06
I bought a little car computer type 7" LCD touch screen that uses the eGalax USB driver and I am using it with Ubuntu 10.04.   I read many lists and forums regarding how to get a touchscreen to function with Ubuntu, and much of the information was wrong or misleading.

So I would like to clear up what has and has not worked for me after spending 18 hours to get this screen to work properly.

The eGalax drivers that came with the screen were old and obsolete.  3.02 was the latest on the little mini cd.  I found a 3.06 version on the web from the company that writes the drivers and although it looked good and it had concise instructions on how to use it, it did not work with Ubuntu 10.04 on a MW525 intel mb.    The software could never find the touch controller, even though it was showing up in the USB device list!  After doing a lot of reading on the web about this driver, I came to the conclusion that the driver is junk and should be avoided.  I lost some hair working with that driver.  Do yourself a favor and don't bother trying to use these old drivers.

With no additional drivers loaded into Ubuntu 10.04, the system cannot identify the eGalax touch screen device.   A driver called evtouch must be loaded.   You can find it via the Synaptic package manager.  Install that and reboot.

Not comes the really weird part.  The newest USB driver is called the evdev driver and the evtouch driver is apparently being phased out (I have read that it does not work with version 11 or later ??)  

After you load the evtouch driver, Ubuntu will find the touch device using the evtouch driver but then the evdev driver apparently wrestles control of the touchscreen away from the evtouch driver. 

So two files need to be modified to allow this screen to work:   

The configuration file for the evdev and evtouch driver is in /usr/lib/X11/xorg.conf.d   and the files I edited were called 05-evdev.conf and 10-evtouch.conf.     Do not be tempted to try and make and edit a file called xorg.conf as mentioned in older docs.    That is a no no in Ubuntu 10.04 and later.   Only edit the config files in xorg.conf.d.


This is how I modified the last InputClass section of the evdev config file (at the very bottom):

[FONT=&quot]Section "InputClass"[/FONT]
  [FONT=&quot]      Identifier "evdev touchscreen catchall"[/FONT]
  [FONT=&quot]      MatchIsTouchscreen "on"[/FONT]
  [FONT=&quot]      MatchDevicePath "/dev/input/event*"[/FONT]
  [FONT=&quot]      Driver "evdev"[/FONT]
  [FONT=&quot]      Option "InvertX" "true"[/FONT]
  [FONT=&quot]      Option "InvertY" "true"[/FONT]
  [FONT=&quot]        Option "Calibration" "38 2003 30 1825"[/FONT]
  [FONT=&quot]EndSection[/FONT]


[FONT=&quot]The calibration section is minX maxX minY maxY for settings.[/FONT]

This is how I modified the config file for the evtouch driver:

Section "InputClass"
    Identifier "eGalax TouchScreen"
    MatchProduct "eGalax TouchScreen"
    MatchDevicePath "/dev/input/event*"
    Driver "evtouch"
EndSection

The descriptor (in this case "eGalax TouchScreen" ) must match up with what the computer identifies in the description you can see via "lsusb" at a terminal window.
  
Other things:

If you look in the boot up log for X you can see how your computer is trying to handle the touch screen.  /var/log/xorg.0.log   You can access it via gedit like this:  sudo gedit /var/log/xorg.0.log.  

If you run evtest (may need to install the evtest software)   via
   sudo evtest /dev/input/eventx”    and try different x events, then you can find the touch screen and see how it is interacting with linux – live.  This is a real eye opener if you haven't seen the evtest program run.

   Of course you can get some info from boot up via "dmesg" at a terminal screen also.

If you get a lockout of the screen and end up not seeing Gnome desktop on the reboot, then hit Control-Alt-F2 and log in as root (make sure you have a root login setup or else you could lock yourself out of your computer on an error) , go and edit the .conf file via nan..  ie nano 05-evdev.conf.

Reboot and try it again.    A typo in that file can cause a lockout of the Gnome desktop.

There is a calibration program called xinput-calibrator, but I have found it of limited use and it also has directions on how to update an fdi hal entry which is not required when using the evdev driver.   (The hal entry is stuff from version 9.10 I believe) However finding the screen calibration coordinates might be useful for some.  I ended up tweaking them manually in the .conf file, reboot, try, repeat.  

On my eGalax equipped screen  ( I don't know the brand as it was made in China and really don't have a brand name!) if I input a MaxY value that was too large the touchscreen simply stopped responding via the evdev driver.  So if in doubt start with smaller values for the maxX and maxY and work up until things look right.

I really like Linux but the development of the software moves so fast from version to version and the changes between major version are substantial that trying to stay on top of what is required is a major task.   The good thing is that the software is progressing (unlike windows) and making technical jumps.

---

### Post by thctlo on 2011-12-02
> **WillardPotter said:**
> Has anyone managed to get the eGalax screens working properly?
 
Yes, me. 
took about 2 hours of reading and then in 5 min it was working.. 
Its realy simpel. 

1) go here, and get the drivers. 
[http://home.eeti.com.tw/web20/eGalax...inuxDriver.htm]("http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm") 

2) backup you config of xorg.conf remove it. 
( make sure its al back to basic, like new install )
cd /etc/X11 
X -configure

3) unpack downloaded drivers, and run setup.sh. 

reboot the server. 

4) touch wil work now, but things are not right. ( for me x-y mouse was incorrect ) 
to fix this. 
login in X, In Aplications-Accessories, you find : eGalaxTouch Utiliy 
Start it and go to tab Tool. 
First do a 4 Pts Calibration, then do 25 points linearization. 

After this every thing was working correct for me. 

hope this helps someone

---

### Post by GeoMX on 2011-12-19
> **ka1axy said:**
> I've just been through the whole eGalax journey with a Xenarc 700TSV display.  This thread (and some others) was a major part of my finally getting it working (after an entire day of trying things). I'm writing this to summarize what worked for me on an Asus EB1501, running Lucid 10.4 with the Xenarc display. My system also has a USB/Bluetooth mouse and keyboard. The mouse is extra helpful while trying to get things working, and seems to coexist well with the touchscreen.

The key steps were:
- downloading the beta Linux driver (3.03.4510 at this time) from the EETI website:
  [http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm)
- running the unmodified setup.sh script with sudo
- rebooting 
- running the eGalaxTouch command after rebooting and selecting USB and disabling right click
- running the TKCal command and doing a 4-point calibration
- running [FONT="Courier New"]xinput -list[/FONT] and note that there were two eGalax input sources
- adding a startup program: [FONT="Courier New"]xinput -set-prop "eGalax Inc. Touch" "Device Enabled" 0[/FONT]

Disabling the second eGalax input device was the key to eliminating the upper-left pointer issue.  I'm still working to determine exactly where to run this command during startup, as it sometimes seems to lose its effect, but rerunning it *always* removes the upper-left pointer problem.

Thanks a lot for the tip on disabling the eGalax device using xinput, it solved my problem with the upper-left pointer. Before this I was planning to discard any mouse event with 0,0 coordinates in my software (I'm developing a custom system).
In my system, *xinput list* shows two eGalax devices, one named "egalax" and the second "eGalax Inc. TouchController", disabling the second one fixes the problem. I have placed the xinput calls in my **xinitrc** file, hope it helps you.

---

