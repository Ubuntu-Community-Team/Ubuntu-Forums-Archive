---
title: "[REQUEST] How to on ALPS/ Synaptics Touchpad installation"
date: 2005-04-17
forum: Hardware &amp; Laptops
---

### Post by laggerzero on 2005-04-17
I have been searching though these forums for awhile now and have seen many different suggestions but no definate answer. If someone could write a HOWTO on installing the synaptics drivers, applying the kernel patch, and writing the configs I'd greatly appreciate it.

---

### Post by malmjako on 2005-04-18
Is the included driver not working? I have a HP Omnibook 6000 and it uses the synaptics driver for the touch pad. I haven't installed any extra drivers for it.

---

### Post by aburda on 2005-04-18
From what I have gathered to get the ALPS touchpad working (on my Toshiba) I need to apply a kernel path that is in /usr/share/doc/xorg-driver-synaptics/alps.patch.gz  I've been fighting with this for a while now and am going to figuire out how to apply a kernel patch sometime tomorrow.  I gather I am going to have to recompile a special kernel and in that recompilation I'm going to have to somehow insert this special source code?

Aaron

---

### Post by mendicant on 2005-04-18
Untested commands follow:

```

% sudo aptitude install linux-source-2.6.10 kernel-package
% cd /usr/src
% sudo tar -x -j -f linux-source-2.6.10.tar.bz2
% cd linux-source-2.6.10
% sudo gunzip -c /usr/share/doc/xorg-driver-synaptics/alps.patch.gz | sudo patch -p1
% sudo cp /boot/config-2.6.10-5-386 ./.config ## or whatever you are currently running--note that there are two dots there, since the file is <dot>config
% sudo make-kpkg --us --uc --initrd --append_to_version "-5-386-alps" kernel_image kernel_headers kernel_source
% cd ..
% sudo dpkg -i kernel*alps*deb

```

I haven't tested these commands, but they look approximately correct.  If anything fails, it will happen before the sudo dpkg line, which means you won't have screwed anything up.

Then just copy the InputDevice section from /usr/share/doc/xorg-driver-synaptics/README.alps and tweak to suit yourself, such as setting MaxTapTime to 0 to disable click-on-tap behavior, and reboot.

---

### Post by laggerzero on 2005-04-18
OK, 

The Good News:

it completed without error and it says that the driver is loaded!   :grin: 

The Bad News:

I can't turn off hardware tapping or change any settings  ](*,) 



so what should I do now?

---

### Post by mendicant on 2005-04-18
How are you trying to change the settings?  On the vaio on which I did this, I use the following, which disables the tap to click.

> 
Section "InputDevice"
  Identifier    "Configured Mouse"
  Driver        "synaptics"
  Option        "CorePointer"
  Option        "Device"                "/dev/psaux"
  Option        "Protocol"              "auto-dev"
  Option        "LeftEdge"              "120"
  Option        "RightEdge"             "830"
  Option        "TopEdge"               "120"
  Option        "BottomEdge"            "650"
  Option        "FingerLow"             "14"
  Option        "FingerHigh"            "15"
#  Option       "MaxTapTime"            "180"
  Option        "MaxTapTime"            "0"
  Option        "MaxTapMove"            "110"
  Option        "EmulateMidButtonTime"  "75"
  Option        "VertScrollDelta"       "20"
  Option        "HorizScrollDelta"      "20"
  Option        "MinSpeed"              "0.4"
  Option        "MaxSpeed"              "0.5"
  Option        "AccelFactor"           "0.01"
  Option        "EdgeMotionMinSpeed"    "15"
  Option        "EdgeMotionMaxSpeed"    "15"
  Option        "UpDownScrolling"       "1"
  Option        "CircularScrolling"     "1"
  Option        "CircScrollDelta"       "0.1"
  Option        "CircScrollTrigger"     "2"
EndSection


---

### Post by mendicant on 2005-04-18
[QUOTE=mendicant]How are you trying to change the settings?  On the vaio on which I did this, I use the following, which disables the tap to click.[/QUOTE]

Oh, and my /etc/X11/Xorg.0.log contains:
> 
(II) Synaptics touchpad driver version 0.13.6
(--) Configured Mouse auto-dev sets device to /dev/input/event4
(**) Option "Device" "/dev/input/event4"
(**) Option "LeftEdge" "120"
(**) Option "RightEdge" "830"
(**) Option "TopEdge" "120"
(**) Option "BottomEdge" "650"
(**) Option "FingerLow" "14"
(**) Option "FingerHigh" "15"
(**) Option "MaxTapTime" "0"
(**) Option "MaxTapMove" "110"
(**) Option "EmulateMidButtonTime" "75"
(**) Option "VertScrollDelta" "20"
(**) Option "HorizScrollDelta" "20"
(**) Option "EdgeMotionMinSpeed" "15"
(**) Option "EdgeMotionMaxSpeed" "15"
(**) Option "UpDownScrolling" "1"
(**) Option "CircularScrolling" "1"
(**) Option "CircScrollTrigger" "2"
(--) Configured Mouse ALPS touchpad found
...
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
(--) Configured Mouse ALPS touchpad found


---

### Post by laggerzero on 2005-04-18
this is mine:

```
Section "InputDevice"
Identifier "Alps Touchpad"
Driver "synaptics"
Option "CorePointer"
Option "Device" "/dev/input/event1"
Option "Protocol" "event"
Option "LeftEdge" "120"
Option "RightEdge" "830"
Option "TopEdge" "120"
Option "BottomEdge" "650"
Option "FingerLow" "14"
Option "FingerHigh" "50"
Option "MaxTapTime" "0"
Option "MaxTapMove" "110"
Option "EmulateMidButtonTime" "75"
Option "VertScrollDelta" "20"
Option "HorizScrollDelta" "20"
Option "MinSpeed" "0.3"
Option "MaxSpeed" "0.75"
Option "AccelFactor" "0.015"
Option "EdgeMotionSpeed" "40"
Option "UpDownScrolling" "1"
EndSection
``` 


```
(II) Synaptics touchpad driver version 0.13.6
(**) Option "Device" "/dev/input/event1"
(**) Option "LeftEdge" "120"
(**) Option "RightEdge" "830"
(**) Option "TopEdge" "120"
(**) Option "BottomEdge" "650"
(**) Option "FingerLow" "14"
(**) Option "FingerHigh" "50"
(**) Option "MaxTapTime" "0"
(**) Option "MaxTapMove" "110"
(**) Option "EmulateMidButtonTime" "75"
(**) Option "VertScrollDelta" "20"
(**) Option "HorizScrollDelta" "20"
(**) Option "UpDownScrolling" "1"
(**) Option "CorePointer"
(**) Alps Touchpad: Core Pointer
(II) XINPUT: Adding extended input device "Alps Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel Input Handler" (type: Other)
Synaptics DeviceInit called
SynapticsCtrl called.
``` 


I tried changing it to what you guys had but no luck.

---

### Post by awaldram on 2005-04-18
If you install 2.6.11 kernel the alp/synaptics is built in.

I use it on my s6010 (Alps)

you might have better sucess with this though no garentees

---

### Post by laggerzero on 2005-04-18
i'm getting the 2.6.11 kernel off of the breezy repositories right now.
 I'll let you know how it works out.


Thanks for all the help thus far

---

### Post by laggerzero on 2005-04-18
YES!!!

It Worked  :grin: 

the only problem i'm having is i get a kernel panic when gnome starts up. I'm installing KDE right now to see if that fixes it. It looks like there will be alps support in breezy when it comes out though which I'm very happy about :D

---

### Post by mendicant on 2005-04-18
Glad it works for you, but I'm a little puzzled that the custom kernel didn't work for you.  

If you can't get things working with the Breezy kernel, you could also try setting the FingerHigh number really high, so nothing you do will count as a touch.  Or, you could use TouchpadOff "on" to disable it completely.  I still like the scrolling feature on it, that's why I only turned off tapping.

---

### Post by laggerzero on 2005-04-18
one big problem

it seems that gamin/gam_server are causing kernel panics every time i boot up. anyone have a fix for this?

---

### Post by laggerzero on 2005-04-18
Back to the first method.


After examining the outputs more closely this time, i saw this after i tried to patch it:


gunzip: /usr/share/doc/xorg-driver-synaptics is a directory -- ignored


is that the problem?

---

### Post by mendicant on 2005-04-18
Ah--oops.  I forgot the patch file.   You should use:

% sudo gunzip -c /usr/share/doc/xorg-driver-synaptics/alps.patch.gz | patch -p1

Sorry about that.  That's why I should have tested the commands...

---

### Post by laggerzero on 2005-04-18
YES!!!


Thank you so much!!

I've been struggling with this for weeks and its finally working.


I think this howto should go in the tips and tricks section aswell.

---

### Post by awaldram on 2005-04-19
Sorry a bit late

fix for kernel 2.6.11 hang in gnome

add 'noinotify' to the nonaltoptions in /boot/grub/menu.lst

---

### Post by anando on 2005-04-20
When I try to patch the alps stuff, I get the following error - PLEASE help !!

sengupta >> sudo gunzip -c /usr/share/doc/xorg-driver-synaptics/alps.patch.gz | patch -p1
patching file drivers/input/mouse/Makefile
patch: **** Can't rename file /tmp/ponJKZh5 to drivers/input/mouse/Makefile : Permission denied

What am I doing wrong here ?

---

### Post by anando on 2005-04-20
ok the following fixed the problem above - I neded to say sudo patch ...


sudo gunzip -c /usr/share/doc/xorg-driver-synaptics/alps.patch.gz | sudo patch -p1

---

### Post by anando on 2005-04-20
[QUOTE=awaldram]If you install 2.6.11 kernel the alp/synaptics is built in.

I use it on my s6010 (Alps)

you might have better sucess with this though no garentees[/QUOTE]


Can you please give me a step by step insruction to install the 2.6.11 kernel from thebreezy repository. 

I tried the synaptics patch with my 2.6.10 kernel - everything worked - EXCEPT now my wireless card was not getting detected - i will take a shot with 2.6.11.

Many thanks for your help.

- Anando

---

### Post by mendicant on 2005-04-20
[QUOTE=anando]ok the following fixed the problem above - I neded to say sudo patch [/QUOTE]

I added this in the howto section. Thanks.

---

### Post by rhaces on 2005-06-02
I had the same problem, i have a Toshiba Satellite A20 Series. I did just how you told, the patch and everything and it woked perfectly, but it came another problem. when i boot with my new kernel with alps i have no terminal screens (like ctl+alt+F1), i have no wireless card (i do a ifup ath0 and it tells me that there is no ath0).

Please help cause i found this a great sollution exept for this.
Thanks

---

### Post by mendicant on 2005-06-02
You need to either rebuild the linux-restricted-modules-<version> package, or build the madwifi drivers.  If you also use the fglrx or nvidia binary driver, you'd also need to rebuild those.  That's a little out of the scope of this howto, but you can build the madwifi drivers by looking here:

[http://www.marlow.dk/site.php/tech/madwifi](http://www.marlow.dk/site.php/tech/madwifi) ## debianized install instructions
[http://madwifi.sourceforge.net/](http://madwifi.sourceforge.net/) ## madwifi driver site

---

### Post by JALenon on 2005-06-02
Hi, thanks for this thread.

I'm new to Linux and this line is unclear to me.

*% sudo cp /boot/config-2.6.10-5-386 ./.config ## or whatever you are currently running--note that there are two dots there, since the file is <dot>config*


What goes in place of ## in the line above?

---

