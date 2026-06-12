---
title: "vpcf115fm - no nvidia video drivers work"
date: 2010-02-02
forum: Hardware
---

### Post by neo4228 on 2010-02-02
I have the sony vpcf115fm core i7 laptop with the nvidia gt 330m mobile video card running Ubuntu 9.10 and have not been able to get any of the nvidia drivers working.  I have tried the 195.30 and 190.53.  Has anyone else had any luck with this laptop?

---

### Post by AimOn on 2010-02-02
I'm struggling with the same problem with a Nvidia Geforce Go 7600.
What are your symptoms? Can you install them and do they not work? Or do you have problems installing them? If so, have a look at EnvyNG.

---

### Post by neo4228 on 2010-02-02
The drivers install and upon reboot I get a black screen.  I then have to boot up in recovery mode and restore my xorg.conf to the original using the "Vesa" drivers.  Ubuntu runs fine other than the video card.  Right now the max resolution I can get with the current driver is 800x600, which makes everything really big on the desktop.

---

### Post by jayded on 2010-02-04
Works perfectly. I have both external and internal LCDs running.
Use the xorg.conf below and follow the steps.

1. Make sure you have the latest nvidia drivers installed for your kernel first.

2. Boot into Windows. Download Phoenix EDID Designer. [http://www.tucows.com/preview/329441](http://www.tucows.com/preview/329441)
Use the export function and ensure it's in RAW format.

3. Boot into Ubuntu. Change the CustomEDID Option (See below) for /etc/X11/xorg.conf to match the path of the EDID raw file.

4. Restart X.


```

Section "ServerLayout"

    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
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

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "MS_ Nvidia Default Flat Panel"
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: unknown, VertRefresh source: unknown
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL S2009W"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 330M"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 330M"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "ConnectedMonitor" "DFP-0,CRT"
    Option         "CustomEDID" "DFP-0:/etc/X11/sonyedid.raw"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "ConnectedMonitor" "DFP-0,,CRT"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by neo4228 on 2010-02-08
That worked....I changed the xorg.conf so it did not look for second device:
 
Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "MS_ Nvidia Default Flat Panel"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 330M"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 330M"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "ConnectedMonitor" "DFP-0,CRT"
    Option         "CustomEDID" "DFP-0:/etc/X11/sonyedid.raw"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by dabrue on 2010-02-14
neo4228, 
So everything works? I am thinking of also getting a vcpf115fm, and I want to be sure that I can use ubuntu. 
Are you getting full resolution and color depth? Does suspend work when you close the lid? Do you know if
the HDMI output works with this workaround?

---

### Post by jayded on 2010-02-16
> **dabrue said:**
> neo4228, 
So everything works? I am thinking of also getting a vcpf115fm, and I want to be sure that I can use ubuntu. 
Are you getting full resolution and color depth? Does suspend work when you close the lid? Do you know if
the HDMI output works with this workaround?

Everything works for me besides the following (but they may work just great with the right config/drivers) :

1. The internal speakers. Line out does work though. I think this is due to a missing or incorrect intel audio driver.
2. Never tried HDMI.

What else works :
1. Full resolution with color depth and external monitors works perfectly. Using the latest NVidia drivers. 
2. Suspend/resume works perfectly.
3. Full hibernate/wake works perfectly.
4. SD port, eSata (fast!) works great too.
5. Sound controls and brightness etc.

This laptop is fast ! (Almost never see more than 30% CPU usage even when running VMware). The internal hard drive is the bottle neck.

Have fun !

---

### Post by dabrue on 2010-02-16
Excellent, thanks for the info!

---

### Post by dabrue on 2010-02-17
So it looks like I got the video working all right, the advice you gave definitely did it. However, Ubuntu 9.10 does not seem to recognize the wireless card and does not claim to have a wifi device. Was there anything special that needed done for this? Other google searching so far has not turned up anything.

---

### Post by jayded on 2010-02-17
> **dabrue said:**
> So it looks like I got the video working all right, the advice you gave definitely did it. However, Ubuntu 9.10 does not seem to recognize the wireless card and does not claim to have a wifi device. Was there anything special that needed done for this? Other google searching so far has not turned up anything.

Get the latest compat-wireless drivers and follow the install instructions. The driver works great.
[http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)

---

### Post by dabrue on 2010-02-17
Ah ha. I looked for this through Synaptic to see if there was a version available. I tried installing the linux-backports-modules-wireless package, and this worked also. Thanks for your help! It seems everything is working now.

---

### Post by scathlock on 2010-02-17
Hello, I have the same video card in samsung laptop. I tried attached xorg.cong byt it doesn't work at all. Maybe You could help me?

---

### Post by jayded on 2010-02-17
> **scathlock said:**
> Hello, I have the same video card in samsung laptop. I tried attached xorg.cong byt it doesn't work at all. Maybe You could help me?

You will need to extract your own EDID for your monitor OR you may not need an EDID at all. See Step 2 and the EDID ref line in the xorg.conf

---

### Post by scathlock on 2010-02-17
I've extracted EDID.
I'm not sure where is the problem because driver seems to work except that I can't adjust brightness (it's set to max - my eyes are full of pain) and sometimes appear artifacts on exit or logon.

---

### Post by dabrue on 2010-02-18
I have a similar issue with the screen. If I close the lid and let it go to suspend, and then open it again, it never recovers. The screen goes from white to black in a motley sort of 
way, and then I have to reboot. 

I suspect that it may be that I am not using the newest driver. I am now using nvidia's version 185 from synaptic, but I may try downloading 190/195 from nvidia directly and see if this gives improvement.

---

### Post by dabrue on 2010-02-18
Upgrading to the nvidia 190 driver version did not help. I still get messy screen when trying to recover from suspend. Perhaps I have an error in my xorg.conf, I'm not sure. Any advice anyone has on this would be appreciated.

---

### Post by D!EGO on 2010-03-12
> **jayded said:**
> Works perfectly. I have both external and internal LCDs running.
Use the xorg.conf below and follow the steps.

1. Make sure you have the latest nvidia drivers installed for your kernel first.

2. Boot into Windows. Download Phoenix EDID Designer. [http://www.tucows.com/preview/329441](http://www.tucows.com/preview/329441)
Use the export function and ensure it's in RAW format.

3. Boot into Ubuntu. Change the CustomEDID Option (See below) for /etc/X11/xorg.conf to match the path of the EDID raw file.

4. Restart X.


```

Section "ServerLayout"

    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
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

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "MS_ Nvidia Default Flat Panel"
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: unknown, VertRefresh source: unknown
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL S2009W"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 330M"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 330M"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "ConnectedMonitor" "DFP-0,CRT"
    Option         "CustomEDID" "DFP-0:/etc/X11/sonyedid.raw"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "ConnectedMonitor" "DFP-0,,CRT"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```


Hello. I downladed Phoenix EDID Designer. Is there a dat file to download? Or do you know where can I find the info to fill a new EDID?
I own a toshiba satellite A505-S6035.
thx

Sorry. Soft threw error while getting edid info. Rebooted windows and got the raw hex.

---

### Post by rfay on 2010-03-26
Anybody interested in this thread will be interested in the project that is trying to address all issues with the Sony F11* laptops:

[http://code.google.com/p/vaio-f11-linux/]("http://code.google.com/p/vaio-f11-linux/")

---

### Post by conexo on 2010-12-14
Hey guys, i have the solution for the problem, it works for me.

Here is the configuration:

First, install the right driver, here i got 2 links that could work
1. [nvidia-current_256.53-0ubuntu3_amd64.deb]("http://launchpadlibrarian.net/56414517/nvidia-current_256.53-0ubuntu3_amd64.deb")
2.   [https://launchpad.net/ubuntu/maverick/i386/nvidia-current/256.53-0ubuntu3](https://launchpad.net/ubuntu/maverick/i386/nvidia-current/256.53-0ubuntu3) 		 	   		  
and a third one: [amd64 build of nvidia-graphics-drivers 256.53-0ubuntu3 in ubuntu maverick RELEASE]("https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/256.53-0ubuntu3/+build/1973339") but its also the same than the 1.

Then
write in the terminal this: "sudo gedit /etc/X11/xorg.conf"
In the screen that should appears, verificate that the device section is right like this one:

Section "Device"
    Identifier     "InternalCard"
    Driver         "nvidia"
    Option         "ConectedMonitor"
    Option         "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"
    Option         "RegidtryDwords" "EnableBrightnessControl=1"
    VendorName     "NVIDIA Corporation"
EndSection

if not correct it and then click save.
Reboot the computer, and before stars ubuntu should appear a fast screen saying NVIDIA.

Good luck.!!!  :p

---

