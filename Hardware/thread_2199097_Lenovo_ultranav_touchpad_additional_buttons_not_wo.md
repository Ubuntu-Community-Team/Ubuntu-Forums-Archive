---
title: "Lenovo ultranav touchpad additional buttons not working"
date: 2014-01-12
forum: Hardware
---

### Post by Hellboy256 on 2014-01-12
I have a new Thinpad E540 which has the 3 additional mouse buttons in the touchpad [http://www.lenovo.com/images/gallery/1060x596/lenovo-laptop-thinkpad-e540-touch-touchpad-detail-9.jpg](http://www.lenovo.com/images/gallery/1060x596/lenovo-laptop-thinkpad-e540-touch-touchpad-detail-9.jpg). My previous thinkpad had 3 separate buttons like those [http://www.lenovo.com/images/OneWebImages/SubSeries/gallery/laptops/ThinkPad-T530-Laptop-PC-Overhead-Keyboard-View-gallery-940x529.jpg](http://www.lenovo.com/images/OneWebImages/SubSeries/gallery/laptops/ThinkPad-T530-Laptop-PC-Overhead-Keyboard-View-gallery-940x529.jpg) which worked.  The touchpad itself is working fine just the buttons ain't. In Windows they work, even the middle one for scrolling!! I've installed the package 'configure-trackpoint' but that didn't help! 
Here the recognized input devices:
```

dmesg | grep input
[    0.559561] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.560750] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.133358] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[   11.984388] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input3
[   12.057888] psmouse serio1: synaptics: serio: Synaptics pass-through port at isa0060/serio1/input0
[   12.103377] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input4
[   12.965768] input: Integrated Camera as /devices/pci0000:00/0000:00:14.0/usb3/3-12/3-12:1.0/input/input5
[   13.981071] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   14.049867] input: HDA Intel MID HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input7
[   14.049920] input: HDA Intel MID HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input8
[   14.049956] input: HDA Intel MID HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input9
[   14.079953] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input10
[   14.079996] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input11
[   19.190549] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input12

```

---

### Post by artur7 on 2014-03-22
I have the same problem. 
Features I've noticed so far under windows: 
Three fingers moved to the left: in browser < back, best would be simulating Mouse8 and Mouse9 buttons (which are forward/backward).  
Also, I have been using R500 and it had feature that when I've been clicking middle mouse buttton simultaneously with touchpoint, then I was scrolling.. 
Another thing is four fingers top to bottom minimize all windows (show desktop functionality), 
four fingers to the left switches to previous window (like alt+tab pressed once), four fingers from bottom to the top maximize. 
Three fingers click simulate middle mouse button. 

Also there should be specific regions: top left - LMB, top left - RMB, region between top left and top - middle button. 

Also, one of the most important functions: I think any movement recognition should be ignored after click was performed, especially in e540, which has very deep mouse pad click, and finger mover very often while clicking. 

I noticed that my habbit from experience with Lenovo R500 is that I am very likely to use touchpoint, but missclicks on touchpad are very disturbing; so ignoring movements and accepting only clicks (I mean "deep clicks") if you just had moved by touchpoint should fix the problem. 

I will try to achieve those functionalities soon.

---

