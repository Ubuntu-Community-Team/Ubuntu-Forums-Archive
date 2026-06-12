---
title: "touch panel configuration on a ubuntu 10.04 tablet"
date: 2011-01-26
forum: Hardware
---

### Post by openick on 2011-01-26
Hello

I tried to configure the touch screen, started by installing microtouch, didn't work, removed the package and installed evtouch followed instructions at page [http://www.conan.de/touchscreen/evtouch.html](http://www.conan.de/touchscreen/evtouch.html), one of the steps was to modify xorg.conf, there was no xorg.conf by default, so created a file at /etc/X11 and copied the following:
(also copied some code from page [http://www.conan.de/touchscreen/libtouch.html](http://www.conan.de/touchscreen/libtouch.html)

Section "InputDevice"
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/event1"
    Option "DeviceName" "touchscreen"
    Option "MinX" "98"
    Option "MinY" "43"
    Option "MaxX" "940"
    Option "MaxY" "925"
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "On"
Option "longtouch_action" "down"
    Option "longtouch_button" 3
 Option "maybetapped_action" "click"
    Option "maybetapped_button" 2
    Identifier "dummy"
    Driver "void"
    Option "Device" "/dev/input/mice"
EndSection

Section "ServerLayout"
InputDevice "touchscreen" "CorePointer"
InputDevice "dummy"

After this I restarted the computer, there was a display problem, after a few attempts, it started in lowgraphics mode with the folowing errors:

EE problem parsing the config file
EE error parsing the config file

parse error on line 15 of section InputDevice in the file xorg.conf "3" is not a valid keyword in this section

..

fatal server error
no screens found

check var/log/xorg.0.log

KDSETMODE failed
VT_GETMODE failed
VT_GETSTATE failed

ddxSigGiveUp


This is a new 10.04 installation with all updates.


How do I reset xorg ?

How will I make the touch screen work?

Thank you.

---

### Post by pi/roman on 2011-01-26
You only need one identifier and driver for each input device, you need to place your values in quotes, and you need to place an end for your server layout section so it would look more like this.

Section "InputDevice"
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/event1"
    Option "DeviceName" "touchscreen"
    Option "MinX" "98"
    Option "MinY" "43"
    Option "MaxX" "940"
    Option "MaxY" "925"
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "On"
Option "longtouch_action" "down"
    Option "longtouch_button" "3"
 Option "maybetapped_action" "click"
    Option "maybetapped_button" "2"
EndSection

Section "ServerLayout"
    Identifier "X.org Configured"
InputDevice "touchscreen" "CorePointer"
EndSection


If you want to define your mouse then you have to create a new section for that.

It looks like you may have other problems though so you would be better off to creat a new xorg.conf and add these sections to it.
```
sudo X :1 -configure
``````
gksudo gedit ~/xorg.conf.new
###or from run app prompt
gksudo gedit xorg.conf.new
```then save it as xorg.conf in /etc/X11

---

### Post by Favux on 2011-01-26
Hi openick,

As pi/roman says your xorg.conf needs a little work.  I believe you want something like this:
```
Section "InputDevice"
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/event1"
    Option "DeviceName" "touchscreen"
    Option "MinX" "98"
    Option "MinY" "43"
    Option "MaxX" "940"
    Option "MaxY" "925"
    Option "ReportingMode" "Raw"
#    Option "Emulate3Buttons" ??
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "On"
EndSection

Section "InputDevice"
    Identifier "dummy"
    Driver "void"
    Option "Device" "/dev/input/mice"
    Option "longtouch_action" "down"
    Option "longtouch_button" "3"
    Option "maybetapped_action" "click"
    Option "maybetapped_button" "2"
EndSection

Section "ServerLayout"
    Identifier "X.org Configured"
    InputDevice "touchscreen"
    InputDevice "dummy"
EndSection
```
Since you didn't have an xorg.conf to begin with you could just remove it:
```
sudo rm /etc/X11/xorg.conf
```
and start over.  Or edit it from the command line with nano:
```
sudo nano /etc/X11/xorg.conf
```
And now you know to always have a backup of your current working xorg.conf and be prepared to restore it from the command line if you break X.  And the same applies to a .conf file in xorg.conf.d if you wanted to go that route.

---

### Post by openick on 2011-01-27
Hello roman

While in low graphics mode, I tried to make it work, chose 'reconfigure graphics' and the xorg settings were altered, so I thought it was necessary to remove xorg.conf file first, by following favux

> **Favux said:**
> [/CODE]
Since you didn't have an xorg.conf to begin with you could just remove it:
```
sudo rm /etc/X11/xorg.conf
```
and start over. 

~$ sudo rm /etc/X11/xorg.conf 
rm: cannot remove `/etc/X11/xorg.conf': No such file or directory


> **pi/roman said:**
> 
It looks like you may have other problems though so you would be better off to creat a new xorg.conf and add these sections to it.
```
sudo X :1 -configure
``````
gksudo gedit ~/xorg.conf.new
###or from run app prompt
gksudo gedit xorg.conf.new
```then save it as xorg.conf in /etc/X11

me@myumpc:~$ sudo X :1 -configure 

X.Org X Server 1.7.6 
Release Date: 2010-03-17 
X Protocol Version 11, Revision 0 
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu 
Current Operating System: Linux myumpc 2.6.32-27-generic #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 i686 
Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.32-27-generic root=UUID=e670ea3c-d7ae-4712-b26e-635e92b12ec0 ro quiet splash 
Build Date: 23 April 2010  05:11:50PM 
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org) 
	to make sure that you have the latest version. 
Markers: (--) probed, (**) from config file, (==) default setting, 
	(++) from command line, (!!) notice, (II) informational, 
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown. 
(==) Log file: "/var/log/Xorg.1.log", Time: Thu Jan 27 17:27:37 2011 
List of video drivers: 
	s3virge 
	sisusb 
	intel 
	nv 
	mga 
	trident 
	voodoo 
	tdfx 
	ark 
	neomagic 
	r128 
	chips 
	nouveau 
	tseng 
	vmware 
	v4l 
	geode 
	apm 
	openchrome 
	siliconmotion 
	cirrus 
	savage 
	mach64 
	i128 
	ztv 
	ati 
	i740 
	radeon 
	s3 
	sis 
	rendition 
	fbdev 
	vesa 
(++) Using config file: "/home/myumpc/xorg.conf.new" 
(==) Using config directory: "/usr/lib/X11/xorg.conf.d" 


Xorg detected your mouse at device /dev/input/mice. 
Please check your config if the mouse is still not 
operational, as by default Xorg tries to autodetect 
the protocol. 

Your xorg.conf file is /home/myumpc/xorg.conf.new 

To test the server, run 'X -config /home/myumpc/xorg.conf.new' 

 ddxSigGiveUp: Closing log 

I am still going ahead with the rest of the instructions.

---

### Post by openick on 2011-01-27
Hello

In addition to the steps that I mentioned as followed in my reply to roman and Favux above, I proceeded to edit xorg.conf.new in directory /home/myumpc and also copied the xorg.conf.new file as /etc/X11/xorg.conf

I tried this with the code from roman first and then again tried the slightly modified code by Favux.

Touch does not work.

In the conan.de/touchscreen/evtouch.html page there are some steps outline as button events and advanced configuration which I did not follow. Also skipped are instructions at the libtouch.html page

Could this be the reason why touch does not work?

Thank you.

---

### Post by openick on 2011-01-29
10.10 has a better environment for touch, so I erased 10.04 and installed 10.10, but there are more fundamental problems, grub requires a choice prompted (this tablet does not have a keyboard), with an external keyboard, several prompts are required (F1 / Enter) on various stages of the booting process, and after booting touch does not work.

(Touchscreen worked at the final stages of the 0/S installation, i.e, there is an introduction of what is new in 10.10 which displays as a slide show during installation, it was responsive to touch)

---

