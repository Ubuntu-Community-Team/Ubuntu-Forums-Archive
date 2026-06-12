---
title: "Touchscreen &amp; Dell E6400 ATG"
date: 2009-05-31
forum: Hardware
---

### Post by kent_e6400 on 2009-05-31
Hi all!

I have installed ubuntu on a Dell E6400 ATG with touchscreen, but the touchscreen isnt working at all. Does anyone know where to find drivers, or how to configure it..?

Ubuntu rocks! :)


Thanks


Kent

---

### Post by aikiwolfie on 2009-05-31
I don't know who Dells supplier is for the ATG. But for the Latitude XT they use N-trig. Who so far as I know do not support Linux in anyway shape or form. Note the [Emperor Linux]("http://www.emperorlinux.com/mfgr/dell/caiman/?tab=overview") version is non-touch only.

My guess is Dell are using an N-trig touch sensor for the ATG as well which means it likely won't work with Linux anytime in the near future.

---

### Post by kent_e6400 on 2009-05-31
Oki, thats bad news...

but.. in windows, it is Digitech that deliver software to the touchscreen, and i found a linux serial driver at their site.

In windows it uses the COM2 port, so i belive it is connected the same way in Linux... Port2..

[http://www.digitechsys.co.kr/board/support_en/s_10.html]("http://www.digitechsys.co.kr/board/support_en/s_10.html")


Now i have to figure out how to install the new driver. Still learning :)

---

### Post by kent_e6400 on 2009-05-31
Hi all! Ive tried to edit xorg.conf, but X crashes, and i have to edit, and remove the last added config to get it work again...



This is my xorg.conf file, after the new settings...
> Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


#
# New section for Digitech touchscreen
#

Section "Files"
	ModulePath 	"/usr/X11R6/lib/modules/Digitouch.so"
EndSection

Section "Module"
	Load "Digitouch"
Endsection

Section "ServerLayout"
	Identifier	"Digitech"
	InputDevice "Digitech" "SendCoreEvents"
EndSection

Section "Input Device"
	Identifier "Digitech"
	Driver "Digitouch"
	Option "Device" "/dev/ttyS1"
	Option "Mode" "absolute"
EndSection


And this is the errorlogfile, 

> 
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux kent-laptop 2.6.28-12-generic #43-Ubuntu SMP Fri May 1 19:27:06 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jun  1 04:09:16 2009
(==) Using config file: "/etc/X11/xorg.conf"
(EE) Failed to load module "digitouch" (module does not exist, 0)
(EE) Failed to load module "extmod" (module does not exist, 0)
(EE) Failed to load module "dbe" (module does not exist, 0)
(EE) Failed to load module "glx" (module does not exist, 0)
(EE) Failed to load module "record" (module does not exist, 0)
(EE) Failed to load module "dri" (module does not exist, 0)
(EE) Failed to load module "dri2" (module does not exist, 0)
(EE) Failed to load module "intel" (module does not exist, 0)
(EE) Failed to load module "digitouch" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log


Anyone?

---

### Post by aikiwolfie on 2009-06-01
Well you might be in luck then and find away to make it work.

I found the following [here]("http://groundstate.ca/TC1100"). Not sure how much use it will be seeing as it's for a wacom device.

> Pen

I've had all of the drivers for the pen added to the default kernel, but you will have to activate by adding those lines to the end of /etc/rc.local .

```
modprobe wacom_acpi
modprobe wacom
sleep 1
echo 1 > /dev/ttyS4
```

You will then have to add some lines to your X config file. You can find information on this from the Linux Wacom project, or you can just add these lines to /etc/X11/xorg.conf .

```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS4"
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"
  Option	"Mode"		"Absolute"
  Option	"Button2"	"3"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS4"
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"
  Option	"Mode"		"Absolute"
  Option	"Button2"	"3"
EndSection
```

And add the following lines to the Server Layout section.

```
InputDevice    "cursor"    "SendCoreEvents"
InputDevice    "stylus"    "SendCoreEvents"
```

---

### Post by aikiwolfie on 2009-06-01
I've also noticed xserver-xorg-input-wacom is installed on my system by default. Even though I don't have any wacom devices. Perhaps there's a conflict.

This might be a stupid question. But you did install all of these modules right?
```
(EE) Failed to load module "digitouch" (module does not exist, 0)
(EE) Failed to load module "extmod" (module does not exist, 0)
(EE) Failed to load module "dbe" (module does not exist, 0)
(EE) Failed to load module "glx" (module does not exist, 0)
(EE) Failed to load module "record" (module does not exist, 0)
(EE) Failed to load module "dri" (module does not exist, 0)
(EE) Failed to load module "dri2" (module does not exist, 0)
(EE) Failed to load module "intel" (module does not exist, 0)
(EE) Failed to load module "digitouch" (module does not exist, 0)
```

---

### Post by kent_e6400 on 2009-06-03
Huum, nope, i havent installed these modules, but i have copied files to the locations described in the Digitouch dokumentation....

Maybe i missed something :)

---

### Post by Favux on 2009-06-04
Hi kent_e6400,

Just to kibitz a little.  Usually touchscreens use the evtouch driver, but since Digitouch has a driver.  And I think your "ServerLayout" needs to look more like:
```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Digitech"	"SendCoreEvents"
EndSection
```
By the way are you in Intrepid or Jaunty?  And just how old are the instructions because "Module" and "Files" were sort of deprecated starting with Hardy I think.  But I don't think they'll hurt anything.

---

### Post by kent_e6400 on 2009-06-05
@Favux:
I changed my config, as you described, but no luck. X says failed to load module.

So, how the heck do i load modules? 
I will try the evtouch driver next...

Im in Jaunty. Ubuntu 9.04...

Thank you!

---

### Post by Favux on 2009-06-06
Hi kent_e6400,

Kernel modules/drivers can be loaded through "/etc/modules".

---

### Post by batch_mode on 2009-07-02
Hello,

Sorry for this late answer. The modules that "do not exist" are Xorg modules not Linux kernel modules. They are found in /usr/lib/xorg/modules/drivers for the display (e;g intel_drv.so is the intel module), and in the /usr/lib/xorg/modules/input for the input modules (e.g. mouse, keyboard, touchscreen, ...). The digitouch_drv.so file should be located here.

But as you may have seen on the Digitech site, there are no drivers for Linux 2.6 available online and no mention of the Digitouch module. And I found it nowhere else on the web. So, the only possibility is to contact them to get it.

Cross fingers !

---

