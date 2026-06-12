---
title: "nVidia 6800GT Driver Issue"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by atomicmoose on 2007-10-26
Hey all, I just installed Ubuntu (7.04) on a new machine that I plan to use mostly for watching HD content. Problem is, I cannot get the video driver to do any resolution better than 1024x768 and on my 21" monitor, that is giving me a headache.

Any help/direction on this is appreciated.


Moose

---

### Post by Steve1961 on 2007-10-26
Have you installed the nvidia driver?  If not you might be best off using [envy]("http://albertomilone.com/nvidia_scripts1.html")

If you still have trouble with your resolution:

sudo gedit /etc/X11/xorg.conf

and make sure the resolution you require is in this section:

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV43 [GeForce 6600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

and that the refresh rates are correct for your monitor

---

### Post by atomicmoose on 2007-10-26
> **Steve1961 said:**
> Have you installed the nvidia driver?  If not you might be best off using [envy]("http://albertomilone.com/nvidia_scripts1.html")

If you still have trouble with your resolution:

sudo gedit /etc/X11/xorg.conf

and make sure the resolution you require is in this section:


<snip>I am grabbing the official nVidia driver now...If that doesn't work, I will try that link and then finally the xorg.conf edit.

Thanks!

---

