---
title: "Monitor not detected"
date: 2010-01-27
forum: Hardware
---

### Post by sathya_myl on 2010-01-27
Hi,
I have a desktop with Dualcore 2.0Gz processor with acer AL1716W monitor. I have installed ubuntu 9.10 dual boot with xp. My monitor is not recognised by ubuntu and none of the visual effects are active. i couldn find a driver also. 

I am new to ubuntu. Please help me to resolve the issue. Thankyou all in advance.

---

### Post by chewearn on 2010-01-27
Please tell us the make and model of graphics card.

---

### Post by sathya_myl on 2010-01-29
I dont know how to find that. Kindly help me on this. Thanks in advance.

---

### Post by chewearn on 2010-01-29
Run this terminal command:
```
lshw -c display
```Copy/paste the output here; enclose the text between [noparse]```
 
```[/noparse] tag.

---

### Post by sathya_myl on 2010-01-30
Here's the outptut I got,

       description: VGA compatible controller
       product: 82945G/GZ Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=i915 latency=0

---

### Post by sathya_myl on 2010-01-30
```
description: VGA compatible controller
       product: 82945G/GZ Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:d2500000-d257ffff ioport:c000(size=8) memory:c0000000-cfffffff(prefetchable) memory:d2580000-d25bffff
```

---

### Post by chewearn on 2010-01-30
You have Intel graphics card, the driver for this already built-in.  There is no additional driver you need to load after install.

To activate visual effect, go to:
Top Panel Menu > System > Preferences > Appearance > Visual Effects tab

Select "Normal" or "Extra".

---

### Post by sathya_myl on 2010-02-01
I tried that option, but it showing some error like "Desktop effects could not be enabled".

---

### Post by chewearn on 2010-02-02
Please run compiz-check to find out the problem:
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

### Post by sathya_myl on 2010-02-03
I ran the above mentioned script and got the following output

```
Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

```

---

### Post by chewearn on 2010-02-03
It seems you are using the "vesa" instead of "intel" driver.  Can you tell us which version of Ubuntu you are running?

If unsure, run this:
```
cat /etc/lsb-release
```

Note:
Intel Graphics was going through major changes in Ubuntu 9.04 (Jaunty Jackalope) and I believe the driver was blacklisted then.

---

### Post by 18wheeler on 2010-02-03
> **chewearn said:**
> It seems you are using the "vesa" instead of "intel" driver. Can you tell us which version of Ubuntu you are running?
 
If unsure, run this:
```
cat /etc/lsb-release
```
 
Note:
Intel Graphics was going through major changes in Ubuntu 9.04 (Jaunty Jackalope) and I believe the driver was blacklisted then.
 
I have a similar problem ([http://ubuntuforums.org/showthread.php?t=1397534](http://ubuntuforums.org/showthread.php?t=1397534)). Could you tell me how to use intel video driver? when I tring to install intel video driver using apt-get, I was told the newest one is already installed ??

---

### Post by sathya_myl on 2010-02-04
My Ubuntu version is 9.10

---

### Post by chewearn on 2010-02-04
Okay, Intel driver in 9.04 and 9.10 have been going through major changes.  There were multiple regressions and it's difficult to find good information on how to solve problems.

Therefore, if you need your Ubuntu installation to continue working (i.e. you got project deadline or term paper to complete), then I strongly suggest not to proceed.

---

First, can you post your xorg.conf.

```
cat /etc/X11/xorg.conf
```

---

### Post by sathya_myl on 2010-02-04
```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```

---

### Post by Grenage on 2010-02-04
Change:

```
    Driver        "vesa"
```

to:

```
    Driver        "intel"
```

---

### Post by Inky69 on 2010-02-16
Sorry, hijacking this thread a bit.....

When I type lshw -c display, it shows :

*-display UNCLAIMED
  description : VGA compatible controller
  product: M56GL [Mobility FireGL V5200]

I have a Lenovo T60p running Ubuntu 9.10.

Now, the dual display used to work, until I unplugged the working Dell monitor and plugged in an HP monitor into the VGA port and a Viewsonic into the DVI port. It detected the new monitors, asked me to configure them and then never displayed the screen correctly since. The Display detector, only sees the internal LVDS monitor.....

Any ideas on how to force a detection? Corrupted settings somewhere...

Ian

---

### Post by chewearn on 2010-02-16
> **Inky69 said:**
> Sorry, hijacking this thread a bit.....

When I type lshw -c display, it shows :

*-display UNCLAIMED
  description : VGA compatible controller
  product: M56GL [Mobility FireGL V5200]

I have a Lenovo T60p running Ubuntu 9.10.



Sorry, that's an ATI graphics, which I have no experience with.  I will have to defer to someone else to help you.

---

### Post by Inky69 on 2010-02-17
OK.

I think the problem could be more the graphics sub-system of Ubuntu 9.10 has gone awry. Boot up sequence continually states "Low graphics mode, fix, reconfigure, cancel?". Yet once logged in, I'm running at 1400x1050 quite happily.

xrandr does nothing to outputs or resolution, simply returns "connected 1400x1050+0+0" and a maximum of 1400x1050"

Ian

---

### Post by Vinnare on 2010-02-18
I've installed Ubuntu only yesterday in my new laptop everything worked out fine till I installed the nVidia display driver suggested by its search. When I rebooted, the display went blank after displaying the normal ubuntu startup circles. Actually the display gets switched off and NOT BLACK (you can mke that difference easily) but the system keeps on. You can infact even log in if you type the password (as if blindfolded, of course ), you know this by the welcome music. Then you can do the work too if you know how to use the keyboard.

When I tried starting in the recovery mode then I did as suggested in most of the other forums i.e. type the command:
sudo dpkg-reconfigure xserver-xorg
but unlike as suggested the rest of the process does not follow and the command line reappears.

Please suggest some solution. My GPU is NVIDIA GT330M. Processor is core i5 520M.
I'm new to linux.

Thnx anyhow

---

### Post by chewearn on 2010-02-18
> **Vinnare said:**
> I've installed Ubuntu only yesterday in my new laptop everything worked out fine till I installed the nVidia display driver suggested by its search. When I rebooted, the display went blank after displaying the normal ubuntu startup circles. Actually the display gets switched off and NOT BLACK (you can mke that difference easily) but the system keeps on. You can infact even log in if you type the password (as if blindfolded, of course ), you know this by the welcome music. Then you can do the work too if you know how to use the keyboard.

When I tried starting in the recovery mode then I did as suggested in most of the other forums i.e. type the command:
sudo dpkg-reconfigure xserver-xorg
but unlike as suggested the rest of the process does not follow and the command line reappears.

Please suggest some solution. My GPU is NVIDIA GT330M. Processor is core i5 520M.
I'm new to linux.

Thnx anyhow

Firstly, I believed the "sudo dpkg-reconfigure xserver-xorg" command don't work any more (for fixinf video issue) in recent Ubuntu release due to changes in Xorg.

Secondly, NVIDIA GT330M appeared to be extremely new.  The linux NVIDIA driver is not supporting this GPU yet.
[http://forums.nvidia.com/index.php?showtopic=156267](http://forums.nvidia.com/index.php?showtopic=156267)

If you would like to continue with Ubuntu, you best bet right now is to revert to VESA driver.  Then, wait for next release (Ubuntu Lucid Lynx 10.04) for a new driver to be rolled in.

---

### Post by Vinnare on 2010-02-18
> **chewearn said:**
> Firstly, I believed the "sudo dpkg-reconfigure xserver-xorg" command don't work any more (for fixinf video issue) in recent Ubuntu release due to changes in Xorg.

Secondly, NVIDIA GT330M appeared to be extremely new.  The linux NVIDIA driver is not supporting this GPU yet.
[http://forums.nvidia.com/index.php?showtopic=156267](http://forums.nvidia.com/index.php?showtopic=156267)

If you would like to continue with Ubuntu, you best bet right now is to revert to VESA driver.  Then, wait for next release (Ubuntu Lucid Lynx 10.04) for a new driver to be rolled in.

Thnx for help

But how do we revert to VESA driver. Please help me I'm new to Ubuntu, or Linux as such

---

### Post by chewearn on 2010-02-18
Okay, not sure but try see if this will work.

Boot into safe mode, go to:
Top panel menu > System > Administration > Hardware Drivers

Select the activated driver, and click the "Deactivate" button on the lower right.

---

### Post by Vinnare on 2010-02-18
> **chewearn said:**
> Okay, not sure but try see if this will work.

Boot into safe mode, go to:
Top panel menu > System > Administration > Hardware Drivers

Select the activated driver, and click the "Deactivate" button on the lower right.

I have already tried that but that does not work. In fact earlier there used to an option of logging in low graphic mode, but now I don't even get that option. In recovery mode I can access only through command lines.
Please suggest some other method.

---

### Post by chewearn on 2010-02-18
> **Vinnare said:**
> I have already tried that but that does not work. In fact earlier there used to an option of logging in low graphic mode, but now I don't even get that option. In recovery mode I can access only through command lines.
Please suggest some other method.

Can you post the content of /etc/X11/xorg.conf

---

### Post by Vinnare on 2010-02-20
> **chewearn said:**
> Can you post the content of /etc/X11/xorg.conf

Although when I log in as root through the recovery mode I get a message Permission Denied. I need to type the command as such, isn't it? I even tried sudo but that didn't work (although I shouldn't have needed it in root!) If things don't work out I plan to reinstall.

---

### Post by chewearn on 2010-02-20
To read the content of /etc/X11/xorg.conf
```
cat /etc/X11/xorg.conf
```You might want to look into the directory /etc/X11 because there might be a back-up copy of xorg.conf from before you change the driver to nvidia.

This will list the files in the directory:
```
ls -al /etc/X11
```Look at the date of the files.  Unless there is no original xorg.conf to began with (not sure about Karmic Koala).

If there is no earlier xorg.conf, you could rename the current one.
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

### Post by Vinnare on 2010-02-21
The result of /etc/X11/xorg.conf is:
> 
Section     "Screen"
           Identifier         "Default Screen"
           DefaultDepth   24
EndSection

Section      "Module"
           Load               "glx"
EndSection

Section      "Device"
            Identifier         "Default Screen"
           Driver             "nvidia"
           Option             "NoLogo"             "True"
EndSection
 

I guess this means that the driver installed is Nvidia. My display is not working since I installed it, so what doI do to revert to the default drivers. Because the display worked until I installed the nvidia driver.

---

### Post by chewearn on 2010-02-21
Rename xorg.conf to xorg.conf.backup
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

### Post by Vinnare on 2010-02-21
When I did that and tried rebooting in the normal mode then the the internal speaker started beeping continuosly. I had to switch off the system using power key. Then I went through the recovery mode and names the file back to original.

I think I am planing to reinstall now. What do ya think?

---

### Post by chewearn on 2010-02-21
If reinstalling is the simplest/fastest way to solve this, by all means.

---

### Post by Vinnare on 2010-02-22
But I hope I understood the problem.

Thanks for the help.

---

### Post by sathya_myl on 2010-04-12
Hi chewearn,

           Thank you for your help. The issue is solved and its working fine now. Since I am new to Ubuntu it took this much time for me to understand what you told.

---

### Post by Jazzmaster94 on 2010-04-17
I have a similar issue for an ATI Radeon X1350 Pro.  I can use VGA just fine, but I cannot use DVI.  During boot I can see GRUB just fine, and the Vista partition runs just fine through DVI.  It just seems to be Ubuntu that is having the issues with DVI, like during boot nothing appears and my processor light is off meaning it is at the login screen waiting for input.

---

