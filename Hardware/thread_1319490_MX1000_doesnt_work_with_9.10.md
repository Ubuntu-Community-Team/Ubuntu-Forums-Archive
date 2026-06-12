---
title: "MX1000 doesnt work with 9.10"
date: 2009-11-08
forum: Hardware
---

### Post by Amios on 2009-11-08
Hey folks, im a little bit confused about my resend update of my OS to "Karmic Koala"
Since that, my mouse "MX1000" doesnt seem to work. I opend the xorg.conf to figure out the problem but. It seems that my configuration doesnt work with Karmic.



xorg.conf before update
```

 
 Section "ServerLayout"
     Identifier     "Default Layout"
     Screen         "Default Screen" 0 0
 #   Monitor        "Configured Monitor"
     InputDevice    "Keyboard0" "CoreKeyboard"
     InputDevic     "Logitech MX1000" "SendCoreEvents"
 EndSection
 
 Section "Module"
     Load           "glx"
 EndSection
 
 Section "InputDevice"
     # generated from default
     Identifier     "Keyboard0"
     Driver         "keyboard"
 EndSection
 
 Section "InputDevice"
         Identifier      "Logitech MX1000"
         Driver          "evdev"
         Option          "Device"    "/dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse"
         Option          "HWHEELRelativeAxisButtons" "7 6"
     Option          "Sensitivity" "1"
 EndSection
 
 Section "Monitor"
     Identifier     "Configured Monitor"
 EndSection
 
 Section "Device"
     Identifier     "Geforce 6600gt"
 #    Driver         "nvidia"
 EndSection
 
 Section "Screen"
     Identifier     "Default Screen"
     Device         "Geforce 6600gt"
     Monitor        "Configured Monitor"
     DefaultDepth    24
     SubSection     "Display"
         Depth       24
         Modes      "nvidia-auto-select"
     EndSubSection
 EndSection
 
 
```xorg.conf currently:
```

 Section "Monitor"
     Identifier    "Configured Monitor"
 EndSection
 
 Section "Screen"
     Identifier    "Default Screen"
     Monitor        "Configured Monitor"
     Device        "Configured Video Device"
     DefaultDepth    24
 EndSection
 
 Section "Module"
     Load    "glx"
 EndSection
 
 Section "Device"
     Identifier    "Configured Video Device"
     Driver    "nvidia"
     Option    "NoLogo"    "True"
 EndSection
 
 
```i think i have to put this code
```
Section "InputDevice"
         Identifier      "Logitech MX1000"
         Driver          "evdev"
         Option          "Device"    "/dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse"
         Option          "HWHEELRelativeAxisButtons" "7 6"
     Option          "Sensitivity" "1"
 EndSection
```some where into my current xorg.conf.

Thanks

---

### Post by khelben1979 on 2009-11-08
When you edit the xorg.conf file by hand you can make the configuration file corrupt if you do it wrong.

My recommendation would be that you rebuild your configuration file from scratch by download the appropiate video drivers from either nVidia or ATi (or another brand if that's the case).

Whether you decide to edit the xorg.conf file by hand or not is of course up to you, just make sure to create a backup file in case something goes wrong, otherwise you have no working graphics which means no working x server.

---

### Post by Amios on 2009-11-09
Of cause, i wouldnt cange it, my mouse would work with all buttons. I just want bring that mx1000 back to work, thats all. And i realy have no idea how, cause there are no dirvers from Logitech for Ubuntu

---

### Post by khelben1979 on 2009-11-09
> **Amios said:**
> Of cause, i wouldnt cange it, my mouse would work with all buttons. I just want bring that mx1000 back to work, thats all. And i realy have no idea how, cause there are no dirvers from Logitech for Ubuntu

You have the hardware support for that mouse if it's compiled in the Ubuntu Linux kernel, otherwise you can always learn to create your own (not to recommend to newbies, though).

---

### Post by Amios on 2009-11-13
there are no driver for this mouse created by logitech.
Isn't there any way to bring a mouse whith more than 5 Buttons to work and to configure and bind each of themin an unique way?

---

### Post by khelben1979 on 2009-11-13
> **Amios said:**
> there are no driver for this mouse created by logitech.
Isn't there any way to bring a mouse whith more than 5 Buttons to work and to configure and bind each of themin an unique way?

I'm using the Logitech MX 1000 on a Debian Lenny system over here and it works just fine, including all the buttons it has on it.

Are you saying that the mouse doesn't work at all or are you saying that the buttons ain't working?

---

### Post by Amios on 2009-11-13
well the mouse works fine, but i want to use all buttons. Thumb, MW_Right, MW_Left....

---

### Post by khelben1979 on 2009-11-13
I see. 

There's a couple of applications which can fix this. [IMWheel]("http://imwheel.sourceforge.net/") is one of them. I've never tried it myself, but it might be worth a try.

```
sudo apt-get install imwheel
``` to get it.

---

### Post by Amios on 2009-11-13
would be nice, if you post your .imwheel.rc with all buttons working :)

---

### Post by khelben1979 on 2009-11-15
I'm sure there must be a GUI somewhere for Linux which can fix this, but in the meantime you can have a look at [this page]("http://adventuresinswitching.blogspot.com/2007/12/getting-my-logitech-mx1000-mouse-to.html").

---

### Post by Amios on 2009-11-15
ok, i took a look at the page you posted. And that result in the same problem why i created this thread. I can not change my xorg.conf, so that the discribed points are totaly irrelevant. Would be fine if you can post your .imwheel.rc havent found any GUI for imwheel

---

### Post by marcdutonkin on 2009-11-15
With a fresh install of Karmic kubuntu, there is not even an xorg.conf file. Though, my MX1000 works fine, but with only 2 buttons running, "Previous" and its contrary. 
Furthermore, as reported above, the procedure based on evdev driver, xvkbd tool, xbindkeys and xmacro programs, does not give any result.

---

### Post by Amios on 2009-11-15
marcdutonkin, i just tryed btnx
```
sudo apt-get install btnx
```
To run it, type > btnx-config and procede to all configuration steps.

its realy nice and seems to work with only one problem, namely "it'll send multible commands by pressing one button, like browserback and whatever you bind to that key"

I hope khelben1979 will post his .imwhellrc very soon :)

---

### Post by khelben1979 on 2009-11-15
> **Amios said:**
> ok, i took a look at the page you posted. And that result in the same problem why i created this thread. I can not change my xorg.conf, so that the discribed points are totaly irrelevant. Would be fine if you can post your .imwheel.rc havent found any GUI for imwheel

Why can't you change your xorg.conf?

This is the section which needs to be edited:
```
Section "Pointer"
            Protocol        "IMPS/2"        #change for your mouse type.
            Device          "/dev/psaux"    #change for your device.
            BaudRate        1200            #This is probably not needed!
            Resolution      100             #And neither is this!
            ZAxisMapping    4 5             #This is necessary!
            Buttons         3               #Use this instead of Emulate3 stuff!
        EndSection
```
[URL="http://imwheel.sourceforge.net/README"]
My source for the above[/URL].

---

### Post by Amios on 2009-11-16
please send me your .imwheelrc

---

### Post by khelben1979 on 2009-11-16
> **Amios said:**
> please send me your .imwheelrc

I have none. I have not been able to use imwheel myself.

---

### Post by Amios on 2009-11-16
and which program do you use instead?

---

