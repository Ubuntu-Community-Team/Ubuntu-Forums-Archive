---
title: "resolution not supported - samsung tv"
date: 2018-03-02
forum: Hardware
---

### Post by jgw on 2018-03-02
I have a samsung tv which was working fine up to about 4 days ago and then it stopped.  The tv tells me that the resolution is not supported.  My display card is a GF108 [GeForce  440].  I checked for any driver updates and found one at the geforce site which I installed (its running right now whilst I type this).  I am using binary driver 390.25 from nvidia 390 (open source).  I think I was using an nivdia 340 before that but my machine was undergoing strange so it may have been anything <sigh>  Anyway, I am now using the latest and greatest from nvidia.  I have attached a picture of my drivers and what is chosen, etc.

My display info:
 *-display               
       description: VGA compatible controller
       product: GF108 [GeForce GT 440]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:30 memory:fd000000-fdffffff memory:f0000000-f7ffffff memory:f8000000-f9ffffff ioport:e000(size=128) memory:c0000-dffff

When I boot the system I can watch it right up to the point when the graphics start to display and then I get the error.  I called samsung and talked to one of their techs.  She took control of my tv and diddled around a bit, asked me, again, what kind of computer (3 time) and then told me that samsung didn's support linux or ubuntu.  So, I am basically screwed.  I did a search for the problem and found a couple of folks asking about the same thing but they never got a response (I am hoping somebody has a thought on this one).

If there was some way I could switch in and out of the graphic display error I could run through all the drivers and find the one that was working.  My problem with that is that I have to disconnect the computer and move it to where my terminal is so I don't have a chance to test anything.  

I would be grateful for any thoughts on this one.

Thank you..........................

---

### Post by #&amp;thj^% on 2018-03-02
is the samsung TV 4K?

---

### Post by jgw on 2018-03-03
Thank you for the reply

Yes, says its resolution is 3840x2160 and the picture size thing is 16x9  (forget what that is called).  Also know that my display card has the following:
Maximum Digital Resolution 2560x1600
Maximum VGA Resolution   2048x1536

I think my problem is that the resolutions are being set by the nvidia dard automatically and I gotta fix that which I can do, I think, in the display settings.  I will mess with that stuff tomorrow and see what happens.

I would be grateful for any suggestions.  I have noticed, for instance, that when I am connected to my monitor I can do just about anything but, then, when I try it on the tv I have to reset my computer (using hdmi on the tv and a standard video connector when dealing with the monitor)    I also know that there is a way as it worked fine, for a month, before disaster struck.

Thanks again!

---

### Post by #&amp;thj^% on 2018-03-03
@jgw I'm not sure if I can help here with your card, but we can look for some clue's.
to find any possible clues with:
```
grep "NVIDIA(GPU-0)" /var/log/Xorg.0.log
```
Also have a look in "/etc/X11" for multiple "xorg.config" files, in-fact we can do that now with:
```
cd /etc/X11 && ls
```
Paste back the returns.

---

### Post by jgw on 2018-03-03
Thanks for the reply!

Here are the results:
/etc/x11         [https://pastebin.com/HeWBqDHd](https://pastebin.com/HeWBqDHd)
nvidia log       [https://pastebin.com/QbzvxbJp](https://pastebin.com/QbzvxbJp)

In my searches I found that the tv will accept 1920x1080 but the problem then goes to whether the hdmi is version 2.  The thing that is bugging me is that I had this thing running for almost a month before it stopped working so I know its possible.  I have no idea what may have changed.

I should also tell you that I cannot do anything when connected to tv as it keeps on telling me I have a bad mode.  I have called them and chatted with them asking them what, exactly that means and have yet to have anybody tell me a thing.  Then I say I am on linux and they say "we don't support that" and will not speak anymore.  Its all very strange.  I am getting the impression that Samsung actually doesn't have a clue about their own machine.

---

### Post by #&amp;thj^% on 2018-03-03
I need to check this please:
```
cd /etc/X11 && ls
```
Mine looks like:
```
cd /etc/X11 && ls
xinit  xorg.conf  xorg.conf.d  Xsession.d
```

---

### Post by jgw on 2018-03-03
thanks for the reply and my apologies.  Must have screwed up.  Here it really is:

greg@movies:~$ cd /etc/X11 && ls
app-defaults             xinit               Xreset      Xsession.options
cursors                  xkb                 Xreset.d    xsm
default-display-manager  xorg.conf           Xresources  Xwrapper.config
fonts                    xorg.conf.backup    Xsession
rgb.txt                  xorg.conf.failsafe  Xsession.d

---

### Post by #&amp;thj^% on 2018-03-04
This "I" have never understood** "multiple xorg.conf files**"??? I ran into that early on in development on 16.04, but here on 18.04 beta not seeing it any more. (Yay! :))
Mine:
```
app-defaults                      rgb.txt    Xreset.d          xsm
cursors                           xinit      Xresources        XvMCConfig
default-display-manager           xkb        Xsession          Xwrapper.config
default-display-manager.dpkg-tmp  xorg.conf  Xsession.d
fonts                             Xreset     Xsession.options

```
I have tried to help others here in the past months with this here in UF, but my hacks don't always work for others due to different hardware, the way the driver was written (For that version) and such.
But we have come this far now so may we see the text in your "xorg.conf.backup" and "xorg.conf".

---

### Post by jgw on 2018-03-04
xorg.conf:                        [https://pastebin.com/Nbfa7At4](https://pastebin.com/Nbfa7At4)
xorg.conf.backup:            [https://pastebin.com/3h3Kizhi](https://pastebin.com/3h3Kizhi)
xorg.conf.failsafe:            [https://pastebin.com/rQnB3psJ](https://pastebin.com/rQnB3psJ)

Threw in the last because it was there <G>

---

### Post by #&amp;thj^% on 2018-03-04
Try this, I see where some changes had automatically been made.
rename the **"xorg.conf.backup"** to **"xorg.conf"** and also rename the **"xorg.conf"** to **"xorg.conf.backup" **
Reboot and see if any better now.
**EDIT: BTW Mine Reads:**
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 378.13  (buildmeister@swio-display-x86-rhel47-05)  Tue Feb  7 19:37:00 PST 2017

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 367.35  (builduser@rw)  Fri Jul 15 21:07:27 CEST 2016

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
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
    ModelName      "HP w2338h"
    HorizSync       24.0 - 83.0
    VertRefresh     48.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 560 Ti"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "DVI-I-1: nvidia-auto-select +0+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    Option         "Coolbits" "12"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Device"
    Identifier  "intel"
    Driver      "modesetting"
    BusID       "PCI:0:2:0"
    Option      "AccelMethod"  "sna"
    #Option      "TearFree" "True"
    #Option      "Tiling" "True"
    #Option      "SwapbuffersWait" "True"
EndSection
```

---

### Post by jgw on 2018-03-04
I bit the bullet and started trying nvidia (my display card is from them).  I tried 340.107 and it worked!  I am typing and using the samsung tv for a monitor!  My problem with that had my wife on my case bigtime so I got adventuresome.  I have all our movies and tv stored on this system <sigh>  Thank goodness its on my data drive.  

I also royally screwed up the xorg.conf and xorg.conf.backup files but I had previously put both of them on pastebin so I could get them back <g> and since stuff is working I just figured to leave them alone.  I learned that I screwed up when I restarted and was told that my resolution was seriously wrecked and found I had duly screwed those files (don't ask - I wasn't paying attention, I fear)

Anyway, this seems to be working but I have no idea for how long.  

Thank you, very much, for your help.  

Oh, I notice you have something from the Dalai Lama - I met him once, a very long time ago, when he was in Seattle.

---

### Post by #&amp;thj^% on 2018-03-05
> **jgw said:**
> I bit the bullet and started trying nvidia (my display card is from them).  I tried 340.107 and it worked!  I am typing and using the samsung tv for a monitor!  
That's Great News! :) It's nice when things just work.;

> **jgw said:**
> 
I also royally screwed up the xorg.conf and xorg.conf.backup files but I had previously put both of them on pastebin so I could get them back (don't ask - I wasn't paying attention, I fear)


Been there a time or two myself. :D I have a strong embedded habit now of "BACK UP- BACK UP_ BACK UP!" :)
> **jgw said:**
> 
Oh, I notice you have something from the Dalai Lama - I met him once, a very long time ago, when he was in Seattle.
He is a Truly Remarkable Human Being.
Great Job jgw and Best Regards.

---

### Post by jgw on 2018-03-05
I forgot to add that my display card does hdmi 1 and not hdmi 2.  In spite of that its working on a 4k tv.  As far as I can tell its all on the driver.  The driver I was using was one I got from the geforce site.  They have a utility wherein you enter your board number, and your operating system and it tells you which one you want to use.  Here are a couple of links on this one.  It seems you want to install it instead of letting the nvidia site to it to make it stick (that's how I did it)  
[https://askubuntu.com/questions/737434/nvidia-gt-440-issue-after-installing-nvidia-drivers](https://askubuntu.com/questions/737434/nvidia-gt-440-issue-after-installing-nvidia-drivers)
[https://linuxconfig.org/how-to-install-the-latest-nvidia-drivers-on-ubuntu-16-04-xenial-xerus](https://linuxconfig.org/how-to-install-the-latest-nvidia-drivers-on-ubuntu-16-04-xenial-xerus)
I am mentioning this one as I thought it was pretty slick to have the manufacturer supporting their products for linux.  On the down side their latest and greatest didn't work for me but one older did.  I don't do very clever things with my graphic card so they both seemed to work, pretty much, the same.  

Perhaps, if somebody else is using an nvidia/geforce board and have the same problem this might help them in their quest.

Thanks again for all the help!

---

