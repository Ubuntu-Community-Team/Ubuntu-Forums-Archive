---
title: "Losing resolution fix on reboot"
date: 2006-12-12
forum: Hardware &amp; Laptops
---

### Post by Simon4tk on 2006-12-12
I had a problem with my nvidia FX5500 card in that the screen resolution would only offer a choice of one - 640x480.

After searching the forums, I found a fix:

[INDENT]sudo apt-get install nvidia-glx[/INDENT]
[INDENT]sudo nvidia-xconfig[/INDENT]

Then pressing CTRL-ALT-BS the NVIDIA logo was displayed and I was back in the required resolution of 1024x768 with all the possible options for screen resolution available to me.

This was fine ... until I rebooted when I end up back with only 640x480 resolution. If I rerun **sudo nvidia-xconfig**, the problem is fixed again but is there another step I am missing to ensure the "fix" is permanent?

---

### Post by adaptr on 2006-12-12
Your fix is not really a long-term solution.

What you need to do to get your monitor and video card set up right is edit the xorg.conf file and adjust some values.

First find out what frequencies your monitor supports - both horizontal retrace and vertical refresh frequencies are needed.
Your monitor's documentation will have this information, or else you can Google it.

Next, write down which resolutions your card supports - and which ones you actually want to use.

Edit xorg.conf with those values handy, and things will more or less be obvious; look for the "Monitor" section to edit the frequencies, and the "Screen" section, subsection "Display", to add and edit the resolutions.
When you're done, restart the X server (Ctrl-Alt-Backspace).
Now you can choose the resolutions and refresh rates you have filled in.

---

### Post by Simon4tk on 2006-12-12
> **adaptr said:**
> Your fix is not really a long-term solution.

What you need to do to get your monitor and video card set up right is edit the xorg.conf file and adjust some values.

First find out what frequencies your monitor supports - both horizontal retrace and vertical refresh frequencies are needed.
Your monitor's documentation will have this information, or else you can Google it.

Next, write down which resolutions your card supports - and which ones you actually want to use.

Edit xorg.conf with those values handy, and things will more or less be obvious; look for the "Monitor" section to edit the frequencies, and the "Screen" section, subsection "Display", to add and edit the resolutions.
When you're done, restart the X server (Ctrl-Alt-Backspace).
Now you can choose the resolutions and refresh rates you have filled in.

I have checked out the information and the range of resolutions seems to be already covered:

Section "Monitor"
    Identifier     "SDM-HS73"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5500]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5500]"
    Monitor        "SDM-HS73"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection

The monitor supports any of the define resolutions and the graphics card supports Horizontal 28-80MHz and Vertical 48-75MHz, I normally use 60MHz as the Refresh rate.

---

### Post by adaptr on 2006-12-12
> The monitor supports any of the define resolutions and the graphics card supports Horizontal 28-80MHz and Vertical 48-75MHz
That is not important: **you have to tell it those frequencies!**
Better drop the MEGAHertzes while you're doing that, too - or the results may not *quite* be what you expected...

You may also want to consider disabling the **ddc** extension, since this tries to get the monitor's capabilities from the monitor itself, and it tends to screw them up.

---

### Post by Simon4tk on 2006-12-12
> **adaptr said:**
> That is not important: **you have to tell it those frequencies!**
Better drop the MEGAHertzes while you're doing that, too - or the results may not *quite* be what you expected...

You may also want to consider disabling the **ddc** extension, since this tries to get the monitor's capabilities from the monitor itself, and it tends to screw them up.

Many Thanks. That seems to have done the trick. I assumed that the way to disable ddc was just to insert **#** in front of **Load DDC** in the Modules Section.

---

