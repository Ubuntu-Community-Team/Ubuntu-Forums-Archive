---
title: "Getting 1920x1200 display using fglrx?"
date: 2010-03-10
forum: Hardware
---

### Post by the_jest on 2010-03-10
I just installed 9.10 on a Lenovo Thinkpad W500. This has a "switchable" graphics mode, with a discrete ATI FireGL V5700 (reported by lspci as a Radeon HD 3650) and an integrated Intel chip, the details of which I forget. In the BIOS you can decide between these chips, or a switchable mode that doesn't work with Linux yet, as far as I can tell, but I don't really care because it's always plugged in so I might as well go for the ATI.

I've installed the fglrx drivers, but the automatic configuration tops out at 1680 x 1050, with the screen image centered in the display with black bands around the edges. The display is definitely 1920 x 1200, and when I do select the Intel chip in the BIOS, I get 1920 x 1200, going all the way to the edges, as I'm supposed to.

How can I get the full display size under fglrx? My xorg.conf, which I haven't touched since it was auto-generated, is below, but I've looked at a few threads here and they've just said that the driver "should" recognize the display size and I shouldn't have to touch the configuration file. But I apparently do. For what it's worth, the Xorg.0.log does finish up with fglrx recognizing a bunch of 1920x1200 modelines.

Thanks. If there are any other configuration things I should know about, I'm all ears; I'm not that knowledgable about X configuration. I mainly will be using this for development, perhaps dual-headed with an external monitor, and would occasionally like to watch movies on it.

---
Section "Screen"
    Identifier    "Configured Screen Device"
    Device    "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Virtual    2960 1050
    EndSubSection
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "fglrx"
EndSection
---

---

### Post by khelben1979 on 2010-03-11
I wonder what driver you chose from the ATi website, because I can't see that your model of the graphics chip is supported. (I see that the FirePro 5700 is supported though)

---

### Post by markbuntu on 2010-03-12
That is most likely a mobility HD360 or some close variant since that is how it reports itself to the driver. 

Did you try the detect displays in the Catalyst Control Center.

Another thing you can try is changing the "virtual" line in xorg.conf to 3840x1200.

---

