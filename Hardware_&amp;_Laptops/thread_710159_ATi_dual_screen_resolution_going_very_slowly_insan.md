---
title: "ATi dual screen resolution: going very slowly insane"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by justleen on 2008-02-28
Hey Team,

I know there have been a brazillion posts about this, en i feel like i've read and tried them all. Nothing helps.. So any hints or tips will be greatly appreciated at the moment.

The problem is with the resulotion of my second monitor, which i just cant get any higher then 800x600 (might even be 640x480, not sure, im guessing on the font/icon size) .
This isnt to bad, since most of my co-workers cant read my screen, its to small for their old eyes, so i can drag a term to the "big screen".. but, i myself find this very very frustrating.

I have a Compaq (HP) NC8430 laptop, with an ATi X1600 mobilty, with a second monitor attached. I have the fglrx drivers installed. fglxinfo is correct,  Bigdesktop is enabled. Compiz works on both screens. Resolution on my laptop screen is right.

If i now try to fix the resolution on the 2nd screen, i have to possible outcomes: my X breaks down completly, or X still works but the resolution is just the same as it was (no matter what i change).

I 've tried with both Mode2, and with Pairmode, neither has effect.
The only thin i can think of, is that the 2nd monitor has no "Screen" section defined in my xorg. conf (trying to add those resulted in a broken X)
Im not even sure wether this is neccesary, since the guides seem to omit this.

IF any one woul be willing to have a look at my xorg.conf , i'd be a very happy camper indeed


Below the relevant portion from Xorg.

> Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "Synaptics Touchpad"
EndSection

Section "Monitor"
        Identifier   "Generic Monitor"
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "Generic Video Card"
        Driver      "vesa"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "DesktopSetup" "horizontal"
        Option      "Capabilities" "0x00000800"
        Option      "Mode2" "1280x1024"
        Option      "EnableMonitor" "lvds,tmds1"
        Option      "ForceMonitors" "lvds,tmds1"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Virtual   1680 1050
                Depth     24
        EndSubSection
EndSection

---

### Post by rvandam on 2008-05-02
Did you ever get yours to work?  I finally got my laptop and external monitor to work.  I used the newest ati driver (via envyng, ask if you don't know what I mean although I'm not 100% certain its necessary) and the --add-pairmode option on aticonfig and then xrandr (and/or the hardy gui for it) works perfectly (just no compiz in bigdesktop mode yet)

Here's the relevant part of my xorg.conf, notice its very clean and simple.


```

Section "Monitor"
    Identifier   "Configured Monitor"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
    Driver      "fglrx"
    Option        "VideoOverlay" "on"
    Option        "OpenGLOverlay" "off"
    Option        "Mode2" "1440x900,1680x1050"
    Option        "PairModes" "1680x1050+1680x1050,1440x900+1680x1050,1440x900+1440x900"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Configured Monitor"
    DefaultDepth     24
EndSection

Section "Extensions"
    Option        "Composite" "Enable"
EndSection

```

---

### Post by sixsmith on 2008-07-09
> **justleen said:**
> The problem is with the resulotion of my second monitor, which i just cant get any higher then 800x600 

OK, take a breath, pardner. I spent several hours on this myself, and a lot of my time was wasted with workarounds for problems with Dapper/Edgy/etc. that were cleanly fixed (breaking the workarounds) in Hardy. I may just be part of this problem but the information I'm presenting here has two advantages:
1) it's not too messy, and therefore less likely to break;
2) my install is less than a month old, so at least it's current.

Now, the tool you want is xrandr, which is pretty mature for Hardy. The **[xrandr wiki]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2")** is very good. It distills everything to 2 steps:
1) clean up your xorg.conf;
2) learn to use xrandr;

It says this about xorg.conf:
> an updated Xorg.conf should:

    * omit dual Device/Screen/Monitor sections
    * omit MonitorLayout option and Screen lines from the remaining Device section
    * omit dual Screen lines from the ServerLayout section
    * omit RightOf/LeftOf indication to the remaining Screen line in ServerLayout section
    * add a "Virtual 2048 2048" (**) line in SubSection "Display" to create a large virtual screen 
If any of that is unclear, it is all explained in detail in the wiki linked above.
Now, as for step 2, I have a Dell laptop with a Dell external monitor, and I can get a desktop stretched over both displays like this:
> xrandr --output LVDS --mode 1400x1050 --pos 0x0 --output VGA-0 --mode 1280x1024 --pos 1400x0
What this does is:
[INDENT]1) sets laptop resolution to 1400x1050;
2) places laptop screen at top left of virual desktop;
3) sets external VGA resolution to 1280x1024;
4) places external screen to the right of laptop screen.[/INDENT]
Hope this helps.
**NOTE: my virtual screen, in this example, is 2680x1050, and accordingly I have "Virtual 2680 1050" in my xorg.conf.
**NOTE 2: these giant virtual desktops do require a lot of memory; if you have old hardware (5+ years), your mileage may vary.

---

