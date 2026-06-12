---
title: "ATI Mobility Radeon HD 5650 problem"
date: 2010-11-15
forum: Hardware
---

### Post by Stevaz on 2010-11-15
First off, basically a 100% fresh newbie when it comes to Ubuntu.  I have installed 10.10 on my laptop, and everything seems to working fine.  But it suggests to install drivers for this video card, and after I do, I can't get past terminal.  I try 'startx' and it gives me a "no screens found" error.  I have also tried a fresh install, and installed the drivers directly from:

[COLOR="Blue"][http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)[/COLOR]

and I still can't get past terminal. ](*,)

As of writing this, I can no longer even get *to* terminal, I get a repeating -->
"failed command: READ FPDMA QUEUED"
status: { DRDY ERR }
error: { UNC }

worst part of this is I'm writing this post in Win 7 #-o

Thanks for any help

Edit:  I can get to the gui on a fresh install without installing the ATI driver, but it is extremely slow starting and shutting down after I shut down the first time.

---

### Post by bama_boy on 2010-12-22
Try to use aticonfig --initial to update your Xorg.conf

Here is my xorg.conf for same video card

```

root@bt:~# cat /etc/X11/xorg.conf

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "Configured Monitor"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "Configured Video Device"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Configured Video Device"
        Monitor    "Configured Monitor"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection


```

I have Toshiba Satellite L650D laptop

---

