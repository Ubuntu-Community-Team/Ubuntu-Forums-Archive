---
title: "How to enable dual monitor for Ubuntu 11.04 + ATI Radeon X300 card?"
date: 2011-05-03
forum: Hardware
---

### Post by Physicist on 2011-05-03
I am trying to enable dual monitor for my Ubuntu 11.04 and ATI Radeon X300 video card. Here is the information about my monitors:
```

$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV370 5B60 [Radeon X300     (PCIE)] [1002:5b60]

```

and

```

$ sudo lshw -C display
*-display:0             
   description: VGA compatible controller
   product: RV370 5B60 [Radeon X300 (PCIE)]
   vendor: ATI Technologies Inc
   physical id: 0
   bus info: pci@0000:01:00.0
   version: 00
   width: 64 bits
   clock: 33MHz
   capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
   configuration: driver=radeon latency=0
   resources: irq:47 memory:ec000000-edffffff memory:efde0000-efdeffff ioport:dc00(size=256) memory:efe00000-efe1ffff
*-display:1 UNCLAIMED
   description: Display controller
   product: RV370 [Radeon X300SE]
   vendor: ATI Technologies Inc
   physical id: 0.1
   bus info: pci@0000:01:00.1
   version: 00
   width: 64 bits
   clock: 33MHz
   capabilities: pm pciexpress bus_master cap_list
   configuration: latency=0
   resources: memory:efdf0000-efdfffff

```


If I try to run System -> Preference -> ATI Catalyst Control Center, it'll pop up a window saying
```

No ATI graphics card is installed or the ATI driver isn't configured properly. 

Please install ATI driver appropriate for your ATI hardware and configure it using aticonfig.

```

I have packages

```

fglrx, fglrx-dev, fglrx-amdcccle, jockey-common, jockey-common, jockey-kde, jockey-gtk

```

installed but

```

$ sudo aticonfig --initial 
aticonfig: No supported adapters detected

```


When I try to use menu System -> Preference -> Monitor, unselect "same image in all monitors", "Detect monitors", arrange my two monitors horizontally, and press "Apply", then it says

```

The selected cofiguration for displays could not be applied

required virtual size does not fit available size: requested=(2720,1024),minimum=(320.200),maximum=(1440,1440)

```

What should I do?

This is very important for me as it is used as my primary work configuration. Please help!

---

### Post by grimey on 2011-05-03
Hi there,

I am having the same problem. 
HP Envy 17 laptop using display port and HDMI output to 2 monitors (1920x1200 each). This was working in 10.10. 
It appears to be a false limitation around resolution restrictions as there is no problem outputting to one of my monitors.

---

### Post by grimey on 2011-05-03
I got this to work.
Update the /etc/X11/xorg.conf file to set a larger maximum size for the virtual screen. 

A minimal xorg.conf that should achieve this is:

Section "Screen"
    Identifier      "Default Screen"
    Device          "Default Video Device"
    SubSection "Display"
        Virtual         4864 1200
    EndSubSection
EndSection

I used the "requested" screen size value that appears in the error message. In your case, use 2720 1024

Hope it works for you!

---

### Post by Physicist on 2011-05-03
Thank you. That works. How did you find out it needed a xorg.conf file?

---

### Post by grimey on 2011-05-04
A combination of searching and trial and error :D

---

### Post by calippus on 2011-06-07
Hello I have the same problem, could you help me?

The selected cofiguration for displays could not be applied  required virtual size does not fit available size: requested=(2732,768 ) ,minimum=(320.200),maximum=(1366,1366)

---

### Post by Physicist on 2011-06-07
Update the /etc/X11/xorg.conf file to set a larger maximum size for the virtual screen. 

Here is what I have
```

Section "Screen"
Identifier "Default Screen"
Device "Default Video Device"
SubSection "Display"
Virtual 2720 1024
EndSubSection
EndSection

```

---

### Post by eatonst on 2011-06-20
This worked for me on an x64 11.04 Radeon x550. 

Thanks for the post!

---

### Post by Yellow Pasque on 2011-06-20
> **Physicist said:**
> I have packages

```

fglrx, fglrx-dev, fglrx-amdcccle, jockey-common, jockey-common, jockey-kde, jockey-gtk

```

installed

You should not have fglrx installed. Use these commands to get 3D acceleration working again:
```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```

---

### Post by desiph3r on 2012-03-12
I don't have  /etc/X11/xorg.conf. Please see below.


etc/X11$ ll
total 88
drwxr-xr-x  10 root root  4096 2012-02-08 12:27 ./
drwxr-xr-x 133 root root 12288 2012-03-12 11:10 ../
drwxr-xr-x   2 root root  4096 2011-04-25 19:05 app-defaults/
drwxr-xr-x   2 root root  4096 2011-04-25 19:05 cursors/
-rw-r--r--   1 root root    14 2011-04-25 19:04 default-display-manager
drwxr-xr-x   4 root root  4096 2011-04-25 19:00 fonts/
-rw-r--r--   1 root root 17394 2010-02-18 19:02 rgb.txt
lrwxrwxrwx   1 root root    13 2012-02-07 21:17 X -> /usr/bin/Xorg*
drwxr-xr-x   3 root root  4096 2011-04-25 19:05 xinit/
drwxr-xr-x   2 root root  4096 2011-02-08 08:27 xkb/
-rwxr-xr-x   1 root root   709 2010-11-02 17:17 Xreset*
drwxr-xr-x   2 root root  4096 2012-02-08 12:27 Xreset.d/
drwxr-xr-x   2 root root  4096 2012-02-08 12:27 Xresources/
-rwxr-xr-x   1 root root  3730 2010-12-01 22:34 Xsession*
drwxr-xr-x   2 root root  4096 2012-02-08 12:27 Xsession.d/
-rw-r--r--   1 root root   265 2010-02-18 19:02 Xsession.options
-rw-r--r--   1 root root   601 2011-04-25 18:54 Xwrapper.config


*-display:0             
       description: VGA compatible controller
       product: RV370 5B60 [Radeon X300 (PCIE)]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:44 memory:dc000000-ddffffff memory:dfde0000-dfdeffff ioport:dc00(size=256) memory:dfe00000-dfe1ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV370 [Radeon X300SE]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:dfdf0000-dfdfffff



01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)] [1002:5b60

---

