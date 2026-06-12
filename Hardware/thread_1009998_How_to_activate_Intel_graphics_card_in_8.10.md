---
title: "How to activate Intel graphics card in 8.10"
date: 2008-12-13
forum: Hardware
---

### Post by elfstone2 on 2008-12-13
Hello,
im a little bit confused with the new 8.10 xorg.conf.. 

I have an Intel x4500 graphics card, but how do i activate the driver? Or how can i check, what driver is used?

lspci says:
```
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
```


glxgears gives 340fps (which is a little slow)

xorg.conf looks like this:
```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

and i already have installed:
sudo apt-get install xserver-xorg-video-intel - libgl1-mesa-glx - libgl1-mesa-dri

But how can i load the intel driver?
Thx for help :)

---

### Post by elfstone2 on 2008-12-16
Can someone help me please? Do you need more information? If so, what do you need?

Thx...

---

### Post by iponeverything on 2008-12-16
take a look at /var/log/Xorg.0.log

or this might get the info that you need

```
grep -i driver /var/log/Xorg.0.log

```

---

### Post by elfstone2 on 2008-12-16
Ok, i got this:
```
         X.Org Video Driver: 4.1
        X.Org XInput driver : 2.1
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(==) Matched vesa for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 4.1
(II) VESA: driver for VESA chipsets: vesa
        ABI class: X.Org Video Driver, version 4.1
        ABI class: X.Org Video Driver, version 4.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.1

```

This confirms my fears, that the vesa driver is running.. how can i switch to intel?

Greetings and thx for the help so far,
Thomas

---

### Post by iponeverything on 2008-12-16
try changing the device section of your /etc/X11/xorg.conf to:

Back up the orginal one first.

```

Section "Device"
Identifier "Configured Video Device"
Driver "intel"
EndSection

```

---

### Post by idigginfo on 2008-12-19
Thanks for the post.  I have the same question, and I tried to change the "device" section to Intel as per your instructions. but when I try to save the file, it tells me 
"Could not save the file /etc/x11/xorg.conf.  You do no have the permissions necessary to save the file.  Please check that you typed the location correctly and try again."

I am new to Linux, this is my first time running Ubuntu on a laptop, and it works but the graphics leave something to be desired. 

How do I fix the permissions so I can save changes to this file?

---

### Post by mstill3 on 2008-12-19
try running 'sudo gedit /etc/X11/xorg.conf'

---

### Post by elfstone2 on 2008-12-23
Well, at least i can try to use the intel driver now.. but it fails on startup of X with an error like "no device".. i think, there might be some problems with the inteldrivers already described in other threads.. too bad :(

---

