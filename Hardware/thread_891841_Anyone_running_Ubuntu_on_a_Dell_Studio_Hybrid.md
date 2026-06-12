---
title: "Anyone running Ubuntu on a Dell Studio Hybrid?"
date: 2008-08-16
forum: Hardware
---

### Post by taylorkh on 2008-08-16
If so, what version?  Any issues?  Looks like a neat little unit for light use.

Thanks,

Ken

---

### Post by timothy truckle on 2008-08-18
I am  running Ubuntu 8.04 LTS on a Studio Hybrid. My first attempt to install failed. The I chose  "save graphics mode", which forces X to use the vesa driver, I guess. 

I succeeded with installing Ubuntu. Afterwards I had to set the resolution in xorg.conf to 1680x1050 for my wide screen LCD and install and configure 915resolution to make this resolution available for X. At the moment there is no intel driver shipped with ubuntu which works out of the box, so for the moment I had to stay with the vesa driver.

For getting wlan working I had to install ndiswrapper and configure it to work with the bcmwl5 driver (which I found somewhere in web).

---

### Post by HiBot on 2008-08-23
8.10 Alpha 4 video works if your willing to do a little minor editing of config files.

First off install 8.10 alpha 4 in safe mode graphics.  Once the install is complete make sure the box is fully patched.  Reboot after patching and first make a copy of your /etc/X11/xorg.conf file.  Go back to this file if you mess something up (boot off the CD to do this roll back).
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.save

```
Once you've made a copy of your xorg.conf make the following changes to it.

1. remove the following line
```

      Driver          "vesa"

```
2. In the "Device" section add the following line.
```

        Option          "monitor-LVDS"   "LVDS"

```
3. Modify your "Monitor" section so that it resembles the following.
```

Section "Monitor"
        Identifier      "LVDS"
        Option          "Ignore" "True"
EndSection

```
Save the file and press Ctrl+Alt+Backspace and you should be up and running on the intel driver.

---

### Post by tati on 2008-08-26
```
Once the install is complete make sure the box is fully patched.
```

Sorry, what does this mean?

And are the changes to xorg.config monitor-specific or will they work with all Dells?

---

### Post by HiBot on 2008-08-27
> **tati said:**
> ```
Once the install is complete make sure the box is fully patched.
```

Sorry, what does this mean?

It means you should run the Update Manager and apply all system patches.

> **tati said:**
> 
And are the changes to xorg.config monitor-specific or will they work with all Dells?

The changes shouldn't be monitor specific.  However I only have my one HDTV to hook up via the HDMI port to test with.

---

### Post by oddonto on 2008-09-09
I am running 8.04 on my Dell Studio Hybrid with the vesa driver works "fine", but can't use the dvi only vga signal and only with vesa. Google Earth is a problem and I guess other sophisticated (OpenGL) program.

---

### Post by bryceharrington on 2008-09-09
Here is a Hardy deb that fixes the problem with graphics not coming up when x starts:

[http://bryceharrington.org/ubuntu/Intel/xserver-xorg-video-intel_2.2.1-1ubuntu13.7_i386.deb](http://bryceharrington.org/ubuntu/Intel/xserver-xorg-video-intel_2.2.1-1ubuntu13.7_i386.deb)

It's still not perfect but at least it works now (no xorg.conf modification required).

---

### Post by tati on 2008-09-11
How do Ubuntu noobs use that deb?

---

### Post by miver on 2008-09-15
> **tati said:**
> How do Ubuntu noobs use that deb?
wget [http://bryceharrington.org/ubuntu/Intel/xserver-xorg-video-intel_2.2.1-1ubuntu13.7_i386.deb;](http://bryceharrington.org/ubuntu/Intel/xserver-xorg-video-intel_2.2.1-1ubuntu13.7_i386.deb;) sudo dpkg -i xserver-xorg-video-intel_2.2.1-1ubuntu13.7_i386.deb

---

### Post by miver on 2008-09-15
> **timothy truckle said:**
>  Afterwards I had to set the resolution in xorg.conf to 1680x1050 for my wide screen LCD and install and configure 915resolution to make this resolution available for X. 
Thanks for solution!

---

### Post by tati on 2008-09-19
I just landed a Studio Hybrid and am quite pleased except for two issues:

1. No screen resolution above 1280x1024 is available. (Dell SP2009W 20" Widescreen Flat Panel Monitor with Webcam)
2. Wireless does not work. (Built-in Dell 1505 Wireless-N Networking)

Can anyone help?

---

### Post by tati on 2008-09-19
Turns out the Dell wireless card is a Broadcom 4328. Here are the instructions for making wireless work (follow 2d when you get to the second step): [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Screen resolution is still a mystery, though.

---

### Post by tatewaki on 2008-09-21
A simple solution is to edit your xorg.conf and change:

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection


to:

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
EndSection


And that should do it!

---

### Post by tati on 2008-09-21
That makes my monitor go black and turn off, unfortunately.

---

### Post by erlguta on 2008-10-01
> **tati said:**
> 
1. No screen resolution above 1280x1024 is available. (Dell SP2009W 20" Widescreen Flat Panel Monitor with Webcam)

Hello Tati. I am interested in this Monitor with webcam.
Is it the webcam working in ubuntu?
Does it include microphone?

Thank you and good luck with your Hibryd.

---

### Post by tati on 2008-10-11
I'm no longer working in Ubuntu until the screen resolution is resolved so I don't know whether the webcam works. I don't believe there's an included microphone; I use the headphone with boom that came with my cellphone.

---

### Post by drmz on 2008-12-22
Not sure if it will help anyone, but I've got the Studio Hybrid running at 1280x1024 on an 17" LG (LG1717s) monitor.

Xorg.conf as follows:
```

Section "Device"
   Identifier "Configured Video Device"
   Driver "intel"
   BusID  "PCI:0:2:0"
   Option "LVDSFixedMode"  "false"
   Option "monitor-TV"     "TVOutput"
   Option "monitor-LVDS"   "LVDS"
EndSection

Section "Monitor"
   Identifier "Configured Monitor"
   Option "DPMS"
   HorizSync 30-83
   VertRefresh 56-75
EndSection

Section "Monitor"
   Identifier      "TVOutput"
   Option          "Ignore"        "true"
EndSection

Section "Monitor"
   Identifier      "LVDS"
   Option          "Ignore"        "true"
EndSection

Section "Screen"
  Identifier  "Default Screen"
  Monitor   "Configured Monitor"
  Device    "Configured Video Device"
EndSection

```

I've also got WPA-PSK working with no issues

---

### Post by fivenote on 2009-01-10
I've read the posts here and tried all the suggestions for getting the intel video driver to work (except the suggested hardy deb package).

I'm running intrepid 8.10 on a new studio hybrid. It's working great but only running the vesa video driver.

Any new tips on making it run the intel driver?

Thanks!

---

