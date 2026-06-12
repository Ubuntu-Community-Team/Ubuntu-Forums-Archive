---
title: "Circular Scrolling?"
date: 2008-02-29
forum: Hardware &amp; Laptops
---

### Post by JaggedOne on 2008-02-29
How do I enable circular scrolling on my laptops trackpad? What do I need to add/change my xorg.conf? Also, once I have it enabled how exactly do I use it. Could you describe the motion on the trackpad I make? I have never used or heard of circular scrolling before so I don't really know how it works. Is it like an ipod clickwheel?

---

### Post by MONODA on 2008-03-07
it is like the ipods click wheel. view my tutorial at:
[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)
on howto do this.

---

### Post by JaggedOne on 2008-03-07
Thanks but that link just goes to the Tutorials & Tips forum. I would love a link to the actual tutorial.

---

### Post by MONODA on 2008-03-07
oops the tutorial is still being reviewed by the admins, ill explain it to you here anyway.
ok so first you ahve to make sure that you are using a touchpad with the synaptics driver.
type:
> sudo nano /etc/X11/xorg.conf
search for a section like this:
> Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"

if you found it then you are using the synaptics driver and you should continue. if not do not continue. ok then add these lines at the end of the section:
>         Option          "CircularScrolling"     "on"
        Option          "CircScrollTrigger"     "2"

so it looks like:
> Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
        Option          "CircularScrolling"     "on"
        Option          "CircScrollTrigger"     "2"
EndSection

Option          "CircScrollTrigger"     "2" selects the trigger area to activate circular scrolling. 2 is the top rightcorner while 0 is any edge. the numbers stand for the edge including the sides. as the number increase, the edges changes in a counter clock wise direction. So 0 would be any edge, 1 would be the top, 2 would be the top right, 3 would be the right edge and so on. restart x after doing so.

---

