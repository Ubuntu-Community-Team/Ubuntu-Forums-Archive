---
title: "xorg.conf question (screen shows WHEN rebooting)"
date: 2011-04-29
forum: Hardware
---

### Post by UncleBoarder on 2011-04-29
This is not a defective hardware problem so if there's a better place to post, just tell me.

This is an issue with 2 Nvidia cards and 3 monitors.

Nvidia GeForce 210 (using DFP-0)
Nvidia GeForce GT 330 (using DFP-0 and DFP-1)

All screens are identical and proven good.

No matter how I change the xorg.conf file, the similarity is that screen 0 displays black.

That's "Black" not blank.  I can still move and see the mouse pointer in all three screens, but screen 0 is always BLACK but working.

Well... almost always black.  When I select reboot, all screens display perfectly during the 2 seconds or so it takes for the screens to blank until it goes down for reboot.

I've tried changing the device identifier so that the same xorg Screen Section info is under screen 1, and then the screen works... same info, different screen number and screen1 then works!  But then the new screen0 is black.

I've tried changing to Twinview, then two screens go black!

Is this somehow related to load order??

Here's my current screen 0 section.  I can post the entire xorg.conf file, but which one?  I've now done at least 3 and all have one similarity.  Whatever is under screen 0, is black.

```
Section "Screen"

# Removed Option "TwinView" "1"
# Removed Option "metamodes" "DFP-0: 1920x1200 +0+0, DFP-1: 1920x1200 +1920+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: 1920x1200 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```Oh, I also tried that nvidia command to force DFP...... Option "UseDisplayDevice" "DFP"

Didn't work.

---

### Post by UncleBoarder on 2011-04-29
Log...

root@x8387-u:/var/log# cat Xorg.0.log | grep display
(--) Apr 29 17:05:17 NVIDIA(0): Connected display device(s) on GeForce GT 330 at PCI:1:0:0:
(--) Apr 29 17:05:18 NVIDIA(1): Connected display device(s) on GeForce 210 at PCI:2:0:0:
(--) Apr 29 17:05:18 NVIDIA(2): Connected display device(s) on GeForce GT 330 at PCI:1:0:0:
root@x8387-u:/var/log#

---

### Post by UncleBoarder on 2011-05-02
Found it... it's related to Compiz.  When I return my Appearance - Visual Effects, to "None", my screen appears and works properly.

Further investigation showed that "the cube" worked on one card but not both video cards at the same time.

Actually it worked on either card.  It occurred to me that the the DIFFERENT cards might be a problem...

Yep, that was it.  Changed out the GeForce 210 so I now have two GeForce GT 330's and all is well.  I assume two 210's would also have worked.

---

