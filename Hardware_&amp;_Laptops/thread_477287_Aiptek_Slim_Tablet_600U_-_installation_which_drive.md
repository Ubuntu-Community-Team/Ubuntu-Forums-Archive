---
title: "Aiptek Slim Tablet 600U - installation: which driver?"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by mr.garfield on 2007-06-18
Hi everybody,

I recently bought a Aiptek Slim Tablet 600U. It's a graphic tablet for pen driven applications.

It works like a charm under VISTA but I can't get it to work correctly under Ubuntu (Feisty - UbuntuStudio actually). I tried downloading and installing the aiptek driver package (kernel and X-Server). I configured the xorg.conf to use the driver and also managed to install a /dev/input/aiptek entry in the devices. However the kernel module does not pick up the tablet.

I know this tablet is not listed in the supported tablet of the aiptek driver. Does anybody know which driver I can use to get the tablet to work?

My main concern is to get absolute coordinates from the tablet rather then the relative ones I get now. This would make using the tablet much more natural. Maybe I can configure this in the xorg.conf by specifying a different driver (I believe Ubuntu installs the tablet using the xpad driver as a mouse input device)? Any help would be appreciated.

TIA.

Cheers,
Marcel

---

### Post by JanvL on 2007-06-18
Hi

I have not yet tried it but this is the only possible solution I have found sofar.

[http://sourceforge.net/projects/xf86digitaledge/](http://sourceforge.net/projects/xf86digitaledge/)

I will try ot soon and report then.


I would say do the same . . . 

Jan

---

### Post by JanvL on 2007-06-18
another link

[http://www.linuxforen.de/forums/archive/index.php/t-37573.html](http://www.linuxforen.de/forums/archive/index.php/t-37573.html)

---

### Post by JanvL on 2007-06-18
next link

[http://sourceforge.net/project/downloading.php?group_id=75377&use_mirror=ovh&filename=xorg-x11-drv-aiptek-1.0.1-2RvP.src.rpm&53376324](http://sourceforge.net/project/downloading.php?group_id=75377&use_mirror=ovh&filename=xorg-x11-drv-aiptek-1.0.1-2RvP.src.rpm&53376324)

---

### Post by mr.garfield on 2007-06-19
Hi Jan,

I already tried the aiptek kernel and xorg drivers. My problem is that apparently the driver gets not loaded with this tablet. The vendor id of this thing is some

Waltop International Corp. 

which is not listed in the aiptek module code.

Any other ideas how to get this tablet to work? Are there generic tablet drivers?

Cheers,
Marcel

---

### Post by bmcage on 2007-06-21
Please do exactly as given in the thread:

[http://ubuntuforums.org/showthread.php?t=122735](http://ubuntuforums.org/showthread.php?t=122735)

but change input/aiptektablet by input/aiptek (there is a bug in X server with long input names)

That should work, if that does not work, nothing will. Note that the thread explains how the vendor id must be used to eg setup a udev rule.

Benny

---

### Post by mr.garfield on 2007-06-23
Thanks everybody for your help. I actually got my tablet working now as I wanted it (absolute coordinates are sent).

The trick was to use the wacom driver instead of the aiptek driver.

Cheers,
Marcel

---

### Post by toshub on 2007-09-16
> **mr.garfield said:**
> The trick was to use the wacom driver instead of the aiptek driver.
Hi,

I've a brand new Aiptek 14000U tablet which reveals being a Waltop Media Tablet as your Slim Tablet 600U. I did as you did (explanation [HERE]("http://ubuntuforums.org/showthread.php?p=3368608#post3368608")) an it works. Not the stylus button which reacts differently as I wrote in the post.

Did you get the stylus button work as you want ?

Thanks

---

### Post by jarvist on 2008-05-12
To get the Aiptek Slim Tablet 600u working with Ubuntu 8.04 (by default it works in relative mode along with the mouse):

Added a new udev rule:
```
root@team-jj:/home/jj# cat /etc/udev/rules.d/66-aiptek.rules 
BUS=="usb", KERNEL=="event[0-9]*", SYSFS{idVendor}=="172f", \
        SYMLINK+="input/aiptek", OWNER="root", MODE="0666"
```

/etc/init.d/udev restart

Check /dev/input for the new aiptek symlink. You can 'cat' this, and then fiddle with the tablet to check that you make lots of binary data.

(the necessary magic vendor number was groked from cat /proc/bus/input/devices), you could probably also put the "idProduct=0031" in there as well. You almost certainly should if you might get another Aiptek/Waltop device. It identifies itself in dmesg as WALTOP type.

Installed the wacom-tools.

Modified my /etc/X11/xorg.conf :
(all irrelevant sections emitted, be careful with this - if you mistype, you won't have a GUI anymore, and will have to fix from console)
```
Section "InputDevice"
         Identifier "aiptek"
         Driver "wacom"
         Option "Device" "/dev/input/aiptek"
         Option "Type"   "stylus"
         Option "USB"    "on"
         Option  "TopX"          "0"
         Option  "TopY"          "0"
         Option  "BottomX"       "10000"
         Option  "BottomY"       "6250"
         Option  "MaxX"          "10000"
         Option  "MaxY"          "6250"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"aiptek"	"SendCoreEvents"
#	Inputdevice	"stylus"	"SendCoreEvents"
#	Inputdevice	"cursor"	"SendCoreEvents"
#	Inputdevice	"eraser"	"SendCoreEvents"
EndSection
```

Err... and I think that was it!
Restart X-server with Ctrl-Alt Backspace..

Just as a note, the aiptek goes to sleep if left alone for a minute or two, to wake up just depress the pen nib and wait a few seconds.

This thread was the first google search for 'ubuntu aiptek 600u', so I thought I'd come here and put the latest info.

As bought for 50 British smackers on amazon.co.uk and put to immediate good work in Gimp & inkscape!

---

### Post by Pete Mander on 2008-07-09
Thanks for the information jarvist, the Wacom driver does the trick. Except for one thing: the two buttons on the stylus are now both interpreted as the middle button.
Without the modifications to xorg.conf, the tablet is (mis)recognised as a mouse device, and in this situation each stylus button is interpreted as buttons two and three, the point being button one. The pressure sensitivity only works with the Wacom driver configured, but both buttons produce button two events, and the third button is lost. Has anyone found a way to correctly interpret the two stylus buttons?

---

