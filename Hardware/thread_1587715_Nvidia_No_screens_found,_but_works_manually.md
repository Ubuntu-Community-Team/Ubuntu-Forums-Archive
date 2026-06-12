---
title: "Nvidia: No screens found, but works manually"
date: 2010-10-04
forum: Hardware
---

### Post by waperboy on 2010-10-04
After installing the nVidia 260 driver (from x-swat ppa) on Ubuntu 10.04 64 bit, gdm fails to start after reboot, logging
"Loading module nvidia", "No screens found", "Unloading module nvidia" in syslog.

If I then choose to boot to terminal, then do

  sudo modprobe nvidia-current
  sudo services gdm start

It starts into X (with low resolution, but can be changed to high), with drivers nicely loaded, and all is fine after that.

I have to do this after every reboot. I'm very happy that the nVidia driver works perfectly otherwise :)

I've run the nvidia xconfig, blacklisted nouveau.

Any thoughts?

---

### Post by dino99 on 2010-10-04
remove xorg.conf then reboot

sudo rm -f /etc/X11/xorg.conf

---

### Post by realzippy on 2010-10-04
> **dino99 said:**
> remove xorg.conf then reboot

sudo rm -f /etc/X11/xorg.conf

...nvidia driver without xorg.conf?
**Why?**



can you post your nvidia-bug-report file?
Created by:

```
sudo nvidia-bug-report.sh
```

---

### Post by goaltime on 2010-10-04
i have same problem.

---

### Post by waperboy on 2010-10-05
> **dino99 said:**
> remove xorg.conf then reboot

sudo rm -f /etc/X11/xorg.conf

This caused nouveau to be loaded, even though it was blacklisted in blacklist.conf. So I put "nouveau.blacklist=true" as kernel boot option, which resulted in no driver being loaded, just vesa.

sudo modprobe nvidia-current gets me up and running still, but why won't it load it automatically?

Can it be because the module is called "nvidia-current", but it tries to load "nvidia" ?

---

### Post by realzippy on 2010-10-06
..again,run:

```
sudo nvidia-bug-report.sh
```

and post it...

---

### Post by waperboy on 2010-10-08
Have been a bit busy, but here's the nvidia-bug-report, from just after reboot.

---

### Post by realzippy on 2010-10-08
Does
**sudo modprobe nvidia-current**
still work?
According to your logfile you have no nvidia driver installed.
*xorg.conf* still exists.
Have you ever tried to install the nvidia driver manually and disabled nouveau formerly?
----
Suggest to purge nvidia,delete xorg.conf,apt update/upgrade,reboot,
install nvidia-current .....   ;-)

---

### Post by waperboy on 2010-10-08
Thanks for your prompt reply, realzippy.

Yes, modprobe still works. I have removed splash and quiet from kernel boot options, so I see the kernel boot progress. When it comes time to start gdm, screen flashes quickly a few times, then the little low-res gui box comes up, saying it couldn't load the driver. I select to continue to console, and do the modprobe and start gdm, and I'm up and running (like there's no tomorrow, because linux on i7 + loads of RAM + good video card is just a fantastic experience).

nVidia drivers are really loaded, since I can run glxgears with 100000+ frames per 5 secs and 3d games (in Wine too).

(To purge nouveau, I had to add "nouveau.blacklist=true" to kernel boot options, just adding blacklist nouveau to blacklist.conf didn't quite do it)

I'll try your suggestion, although I'm not to keen on doing update, let alone upgrade - I'm afraid it will turn Meerkat on me :)

---

### Post by realzippy on 2010-10-08
No worry,no meerkat when running:
sudo apt-get upgrade
It just gives you newest packages and the .25 kernel for 10.04...
It would be *apt-get distupgrade* which would upgrade to 10.10.

---

### Post by Claus7 on 2010-10-08
Hello,

concerning your problem, I think, that in section "ServerLayout" of your xorg.conf file, you have to put near the option Identifier, the title of your graphics card as well as in the section Device (again in the option Identifier) and not just leave the default.

Also, you have to specify in the screen section the resolutions you want, as well as having in mind in that section to use in the Device option what you used in the identifier above. 

In order to find which title you will use just type lspci | grep VGA and use everything after the : .

Regards!

---

### Post by realzippy on 2010-10-08
> **Claus7 said:**
> Hello,

concerning your problem, I think, that in section "ServerLayout" of your xorg.conf file, you have to put near the option Identifier, the title of your graphics card as well as in the section Device (again in the option Identifier) and not just leave the default.

Also, you have to specify in the screen section the resolutions you want, as well as having in mind in that section to use in the Device option what you used in the identifier above. 

In order to find which title you will use just type lspci | grep VGA and use everything after the : .

Regards!

AFAIK his "ServerLayout" and ""Device" section is ok.If his *xorg.conf* would be corrupted,the driver would not run when starting the module manually.

---

### Post by Claus7 on 2010-10-08
Hello,

> **realzippy said:**
> AFAIK his "ServerLayout" and ""Device" section is ok.If his *xorg.conf* would be corrupted,the driver would not run when starting the module manually.

I faced exactly the same problem with an ati driver. I had tampered multiple times with xorg trying to find out what was causing the problem, either getting the resolution out of range or getting the same message error as the OP has posted. 

With much effort I found out that stopping gdm, tampering with xorg and restarting either gdm or startx, the system was opening normally. The best xorg file was the one with the characteristics I describe, without having to mess with gdm in every boot process.

I'm not 100% sure whether it was the tampering of xorg or an update or something else. I just gave some simple, I think, instructions on how to deal with it. In case it does not work, a backup of xorg will make all the changes that took place, like just never happened.

Finally, posting that file (the OP) would give an insight on what is going on, always having in mind that the problem lies there. Actually, that way, it will eliminate one option.

Regards!

---

### Post by realzippy on 2010-10-08
@claus7 
OP posted his xorg.conf (it is in the nvidia-bug-report).
Here it is,you could specify chanchings op should test:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 260.19.06  (buildmeister@builder101)  Mon Sep 13 04:59:45 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
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
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


____________________________________________

```

Edit:
The only thing I wonder about is the low Hsync rate;would expect resolution issues.

---

### Post by Claus7 on 2010-10-08
Hello,

do you have any affiliation with the OP or something? 

Now the first thing I would try is to put some info about the resolution. Check the manual of your monitor and see what are the resolutions it supports.

Then tamper xorg like this:
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "aaaaxbbbb"
    EndSubSection
EndSection
```

where aaaa and bbbb are the values of one of the resolution settings the card supports. This is pretty simple. There are other tweakings someone could try, yet one thing at a time. This one, should be inserted though, cause you identify manually the resolution you want.

Regards!

---

### Post by realzippy on 2010-10-08
[I]do you have any affiliation with the OP or something?
[/I]
lol no;why?

claus7,
I do not understand what you are going to achieve with those
xorg.conf changes;OP has no troubles (see his post #9),only has to *modprobe* nvidia kernel module manually..see no xorg.conf relation here.
So I am out for the moment;will observe this.

---

### Post by Claus7 on 2010-10-08
Hello,

> **realzippy said:**
> [I]do you have any affiliation with the OP or something?
[/I]
lol no;why?

claus7,
I do not understand what you are going to achieve with those
xorg.conf changes;OP has no troubles (see his post #9),only has to *modprobe* nvidia kernel module manually..see no xorg.conf relation here.
So I am out for the moment;will observe this.

sorry about that, just I did not notice that he had uploaded xorg.conf, so I was startled a little by seeing you posting this.

I will keep an eye on that too. It might be that I have misunderstood the problem and the solution I applied to my case was accidental. I was hoping to help, yet it seems that you grasp better the problem. I'm not familiar with modprobe and how to give a hand on this. Thought xorg might have been the root of the problem. 

My apologies if I directed to a wrong direction.

Regards!

---

### Post by realzippy on 2010-10-08
@waperboy

..can you please post your blacklist.conf?

---

### Post by waperboy on 2010-10-10
Still haven't had the time yet to try anything.

Going to try the purge and reinstall now.

Here's the blacklist.conf:

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

blacklist nouveau
blacklist vga16fb
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

```

(I added some blacklistings at the end after reading some driver-issue post but it didn't help :))

nvidia-graphics-drivers.conf:

```
blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96

```

---

### Post by waperboy on 2010-10-10
Thanks for your time, guys!

I've now done 

service gdm stop
log into console
apt-get remove --purge nvidia*
rm /etc/X11/xorg.conf
apt-get update
apt-get upgrade
reboot

Logged into default X lowres mode,

service gdm stop
log into console
apt-get install nvidia-current
nvidia-xconfig
reboot

The situation is still the same :(

New nvidia-bug-report.

---

### Post by Claus7 on 2010-10-11
Hello,

> **waperboy said:**
> Thanks for your time, guys!

I've now done 

service gdm stop
log into console
apt-get remove --purge nvidia*
rm /etc/X11/xorg.conf
apt-get update
apt-get upgrade
reboot

Logged into default X lowres mode,

service gdm stop
log into console
apt-get install nvidia-current
nvidia-xconfig
reboot

The situation is still the same :(

New nvidia-bug-report.

in case there is a problem with xorg, the commands you post above should be executed as root.

Then post us your xorg.conf file that would have been created. Because that way your ubu machine takes info from xorg. If that is messy, then your booting is messy as well.

After that, you have to check out if this is a file that can stand on its own. Having to do all these steps means that you do manually your configurations, which in turn means that you have to do a little more tweaking than just typing some commands. I point out again that all these apply in case it is a xorg conf thing.

Regards!

---

### Post by realzippy on 2010-10-11
Why have you blacklisted nvidia frame buffer (nvidiafb) ???
Also no need to blacklist nouveau.Here is a working blacklist.conf
from a machine running nvidia 260.xx driver for testing:

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


```

---

### Post by waperboy on 2010-10-12
Of course the commands were executed as root, I just didn't think to type it out in the post :)

I'll try with the original blacklist.conf at first convenience.

Also would like to look through the script that starts gdm in the first place, to see what it does. It's been abstracted away with the service command these days, and /etc/init.d/gdm contains no useful info...

---

### Post by peter wee on 2010-10-28
hi
have the same problem. if i use the nvidia-current drivers it will result in to a black screen. with the nvidia driver from their webpage, i also got no useable screen found !! i tried everythink i found on the web. i nee help!, does anybody solved this problem ?!

---

### Post by realzippy on 2010-10-28
@pw
Welcome!
If you have the same problem,means,you have to run "**startx**" and nvidia driver runs fine,you are right here.
(waperboy not seems to get a fix)
Otherwise,better open an own thread.
Which graphics card do you run?
Which Ubuntu version?

---

