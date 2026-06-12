---
title: "What happened to displayconfig-gtk?"
date: 2008-11-28
forum: Hardware
---

### Post by robtg on 2008-11-28
Hi all.  Can someone explain to me why displayconfig-gtk was dropped from Ubuntu?   I did a clean install of 8.10 and nothing I did would get me above 800x600 resolution.  Older releases of Ubuntu did a good job of detecting my laptop's resolution; more recent versions did a miserable job but at least you could use dispalyconfig-gtk to set the correct resolution.  Now there's nothing left but the Screen Resolution application which I've never been able to make work.

Why remove a useful tool like this?

-Rob

---

### Post by Bibek on 2008-11-28
```

 sudo apt-get install displayconfig-gtk

```

---

### Post by jpeddicord on 2008-11-28
It was removed from the system because Xorg supports hotplugging and device autodetection now. However, there are cases where it may not work correctly. A new tool is in the works for 9.04 to tweak X options, but it isn't quite ready at the moment.

What's your graphics chipset? Paste your /etc/X11/xorg.conf as well, even if it doesn't have much in it.

---

### Post by robtg on 2008-11-28
Thanks, but I'm not running Ubuntu at the moment so I don't have the xorg.conf file hady; I was so annoyed at my inability to fix the resolution problem that I installed Pardus Linux over my Ubuntu system.  It didn't do any better job of detecting the proper resolution but it has a KDE tool (vaguely similar to displayconfig-gtk) that lets me specify the laptop's resolution and gives me the results I want.  It's a very old laptop (Compaq Presario with a "Made for Windows Me" sticker on it!) with an ATI Rage Mobility chipset.  As I said, older versions of Ubuntu did a good job of detecting the laptop resolution but not recent versions.  I don't think the device autodetection in Xorg is quite ready for prime time yet.

-Rob

---

### Post by robtg on 2008-11-28
I did try this using Synaptic but I couldn't find the package.  I should have tried your terminal method.  Thank you.

-Rob

---

### Post by jpeddicord on 2008-11-28
> **robtg said:**
> I did try this using Synaptic but I couldn't find the package.  I should have tried your terminal method.  Thank you.

-Rob

It won't work in the terminal either; the package doesn't exist anymore, sorry.

[http://packages.ubuntu.com/search?suite=intrepid&arch=any&searchon=names&keywords=displayconfig-gtk](http://packages.ubuntu.com/search?suite=intrepid&arch=any&searchon=names&keywords=displayconfig-gtk)

---

### Post by thejennie on 2009-04-10
[nevermind!]

---

### Post by 0liv on 2009-05-11
Any way to install displayconfig-gtk on Ubuntu 9.04??

Because now I've reinstalled Jaunty, I'm stuck with an flickering 800x600 display... And it's very upsetting when webdesigning :shock:

I tried to tweak xorg.conf by hand but nothing worked, 
I also tried the [COLOR="DarkRed"]sudo dpkg-reconfigure -phigh xserver-xorg[/COLOR] but it did not solve my problem.

HELP!!](*,)

---

### Post by aston4 on 2009-06-30
really kind of messed up that this important tool was just tossed out, and nothing to replace it. Once again Ubuntu is dead to me for some rediculous reason.  Back to windows

---

### Post by aston4 on 2009-06-30
> **robtg said:**
>   I don't think the device autodetection in Xorg is quite ready for prime time yet.

-Rob


understatement

---

### Post by Esa on 2009-07-06
> **jacobmp92 said:**
> It was removed from the system because Xorg supports hotplugging and device autodetection now. However, there are cases where it may not work correctly.

Yes, really,

I updated Jaunty to an old pc, it has WinFast GeForce2 MX 64MB and Eizo FlexScan L365 (1024x768 ), resolution is automatically awful 640x480 after installing Nvidias restricted driver (initially it was 800x600).

Gnome-display-properties directs to use Nvidia-settings but both are useless, max resolution available is 640x480.

Then I renamed xorg.conf and restarted X, resolution changed to 800x600.

Nvidia-settings tells to:
sudo nvidia-xconfig (New xorg.conf file written..) restarted X and Eizo says "signal error" but display is still readable (1600xsomething resolution is used and tens of other available!).

Now I could change resolution to 1024x768, but "signal error" is still blinking (fH: 68.5kHz, fV: 84.8Hz).

Chanced display refresh from "auto" to "75 Hz", restarted X and ...
got "signal error" (fH:105.7kHz, fV:84.5Hz) with blank screen :(

After blind login screen stays blank - grrr... have to continue after some sleep.

Auto detect was nice,  Cheers, Esa

---

### Post by Esa on 2009-07-07
> **Esa said:**
> ... have to continue after some sleep.

OK, actually last night I edited xorg.conf (correct frequences for Eizo and 1024x768 to first mode) and screen was ok  - except:

1) Somehow borders disappered around windows, so I can't now minimize or close windows that way.

2) Terminal window is just blank white square, nothing visible.

3) ctrl-alt-F1 (and others) bring blueish garbled screen.

So, how to edit xorg.conf now :)

Previous 9.04 install to another old pc with some no-name-ATI-clone display adapter went just fine.

  Cheers, Esa

---

### Post by Esa on 2009-07-07
> **Esa said:**
> So, how to edit xorg.conf now :)

Resolved: GDM has failsafe terminal option, that way I managed to edit xorg.conf - changed "nvidia" to "nv" and after blank screen + hard reboot everything looks just fine.

It seems that all trouble starts when display is not detected automatically and wrong frequencies and resolutions are used:

(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:E-EDID segment register" registered at address 0x60.
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0):   ... none found
(II) NV(0): Unable to detect display type...
(==) NV(0): ...Using default of CRT


If anyone is interested, this is the latest working xorg.conf:

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Eizo"
    ModelName      "L365"
    HorizSync       24.0 - 60.0
    VertRefresh     55.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nv"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


 Cheers, Esa

---

### Post by MikeDK on 2009-07-15
actually there are more and more screens i see around that dont work under ubuntu just had problems with my friends machine wich used to be mine, never had problems with it using 7.10 gutsy, so i found out that my friends screen an LG L192ws didnt work at all biggest resolusion was 800x600 when it should get 1440x900, so tryed with my own screen an Acer AL1916w wich works well under jaunty, but not under ibex with an AGP 7600GS 256, so i manually edited xorg.conf to get it right, then it works fine.
But i've never had those kinds of issues on ubuntu....never.

hope the new applikation thats in development comes out soon.

Kind Regards MikeDK

Oooh and if its the applikation xorg-options-editor-gtk i would really say it sucks at this time, dont work very good yet and for newcomers to ubuntu, its surdenly not the app to use, if they get problems with screens

---

### Post by Vakman on 2009-07-15
> **0liv said:**
> Any way to install displayconfig-gtk on Ubuntu 9.04??

Because now I've reinstalled Jaunty, I'm stuck with an flickering 800x600 display... And it's very upsetting when webdesigning :shock:

I tried to tweak xorg.conf by hand but nothing worked, 
I also tried the [COLOR="DarkRed"]sudo dpkg-reconfigure -phigh xserver-xorg[/COLOR] but it did not solve my problem.

HELP!!](*,)
Do you an Intel graphics chip? If so follow this [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
If that does not work follow this: [http://www.ivankristianto.com/2009/06/howto-fix-ubuntu-jaunty-904-intel-graphics-problem/](http://www.ivankristianto.com/2009/06/howto-fix-ubuntu-jaunty-904-intel-graphics-problem/)
Good luck

> **robtg said:**
> Hi all.  Can someone explain to me why displayconfig-gtk was dropped from Ubuntu?   I did a clean install of 8.10 and nothing I did would get me above 800x600 resolution.  Older releases of Ubuntu did a good job of detecting my laptop's resolution; more recent versions did a miserable job but at least you could use dispalyconfig-gtk to set the correct resolution.  Now there's nothing left but the Screen Resolution application which I've never been able to make work.

Why remove a useful tool like this?

-Rob
I agree 100%. That was indeed a useful tool. Not sure why it was removed. Just because something is now auto detected does not mean you remove the other way. Now, I don't mind since things are always fine for me. Almost always once I have the right drivers. But still some people would like this back.

---

### Post by edu1962 on 2009-08-12
[URL="http://forums.linuxmint.com/viewtopic.php?f=90&t=20326&p=120317"]Found this solution on a Mint Forum.
[/URL]

---

### Post by mrtorture on 2009-08-18
I'm having this same problem on 9.10 ...

Ubuntu shouldn't be more "user-friendly"? Then why they have removed displayconfig-gtk that was very useful? ... Can't understand this guys, seriously... This auto-dectect thing never worked for me...

---

### Post by aston4 on 2009-12-31
Issue still here.  Installed lastest 9.10 on friends machine to fix her problem (she hated vista), but can't adjust refresh rate to match monitor.  will try mandriva I guess

---

### Post by clarkkillick on 2011-04-03
I have the same problem.  I installed Ubuntu 8.04 on a PC for a friend, but her monitor doesn't auto-detect, so displayconfig-gtk was very helpful.  Now I can't upgrade her system to Ubuntu 10.04 unless I'm prepared to leave her monitor horribly flickery.

edu1962's solution does not work for me. dpkg complains that python must be <<2.6 for guidance-backends_0.8.0svn20080103-0ubuntu16_i386.deb.  I also tried guidance-backends_0.8.0svn20080103-0ubuntu16.2_i386.deb and got the same result.

---

