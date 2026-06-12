---
title: "Wrong Synaptics Vertical Scroll Width"
date: 2008-11-01
forum: Hardware
---

### Post by James_the_dude on 2008-11-01
Hello,

I installed Intrepid yesterday and I just can't seem to find a fix for this little annoyance:

On my synaptics touchpad there is a section (separated by a ridge of raised plastic) on the right side that one uses to scroll. The problem is that the area of the touchpad that actually activates scrolling extends about a centimeter wider than to the left than it should.

I had this same issue in Hardy, and I was able to fix it by finding the the "input device" section of my xorg.conf and adding the line

     Option     "RightEdge"     "5950"

In Intrepid there was no section for my touchpad in my xorg.conf so I added the code

Section "InputDevice"
     Identifier "Synaptics Touchpad"
     Driver "synaptics"
     Option "RightEdge" "(many values tried from 4000 to 10000)"
EndSection

No matter what value I tried this had no affect on the right side scrolling edge. Does anyone know why that may be?

---

### Post by James_the_dude on 2008-11-02
I really hate to "bump" this, and I apologize, but I'm sure someone must know what's going on here.

---

### Post by monkeys on 2008-11-18
In Intrepid, the xorg isn't used anymore. Instead, something called HAL's being used. It's not too difficult to understand, but I've tried several solutions to this problem and still have found no solution.

My [post]("http://ubuntuforums.org/showthread.php?t=984618") has a link to one of the solutions that's been tested and fallen through. But it should be informative, at least!

---

### Post by James_the_dude on 2008-11-28
Okay, this is a start. Hal... hardware abstraction layer I believe. The changes in the right edge value that I change in /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi don't seem to make any difference, even after logging in and out.

Here are the contents of that file:

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="Synaptics TouchPad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
	<!-- Arbitrary options can be passed to the driver using 
	     the input.x11_options property since xorg-server-1.5. -->
	<!-- EXAMPLE:
	<merge key="input.x11_options.LeftEdge" type="string">120</merge>
	-->
      </match>
      <match key="info.product" contains="AlpsPS/2 ALPS">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="appletouch">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="bcm5974">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.LeftEdge" type="string">0</merge>
        <merge key="input.x11_options.RightEdge" type="string">6000</merge>
        <merge key="input.x11_options.TopEdge" type="string">0</merge>
        <merge key="input.x11_options.BottomEdge" type="string">800</merge>
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizScrollDelta" type="string">0</merge>
        <merge key="input.x11_options.VertScrollDelta" type="string">40</merge>
        <merge key="input.x11_options.PressureMotionMinZ" type="string">10</merge>
        <merge key="input.x11_options.FingerLow" type="string">16</merge>
        <merge key="input.x11_options.FingerHigh" type="string">80</merge>
        <merge key="input.x11_options.FingerPress" type="string">256</merge>
        <merge key="input.x11_options.PalmDetect" type="string">0</merge>
        <merge key="input.x11_options.PalmMinWidth" type="string">10</merge>
        <merge key="input.x11_options.PalmMinZ" type="string">200</merge>
        <merge key="input.x11_options.MinSpeed" type="string">0.8</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">1.2</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.10</merge>
        <merge key="input.x11_options.MaxTapMove" type="string">25</merge>
        <merge key="input.x11_options.MaxTapTime" type="string">223</merge>
        <merge key="input.x11_options.MaxDoubleTapTime" type="string">200</merge>
        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>
        <merge key="input.x11_options.RTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">0</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```

---

### Post by hyperform on 2009-01-09
I just got this problem here.  Setting options in xorg.conf DOES have an effect for me.  First, I ran synclient -m 1 to get the numeric values of the dimensions of my touchpad, then in xorg.conf I just added 

"Option"   "VertEdgeScroll"   "1"
"Option"   "RightEdge"        "975"  #right max is 1000
"Option"   "PalmDetect"       "1"    #this actually WORKS for once

This took me back to normal.  Before the scroll edge was only the very furthest right edge and I couldn't reliably get it to work.  I tried installing ksynaptics, qsynaptics, etc. and none of them had any effect.  Gsynaptics just manages basic functions like acceleration and speed, so I left those alone in xorg.conf so I can use gsynaptics on those parameters.  Since I also like using the right top corner as a "middle button" click I added that option too with the option RTCornerButton.

As far as I can tell editing that hal file has nothing to do with anything.

---

### Post by joshuajtl on 2009-03-01
Great help.

[http://blog.eddiemonge.com/2008/08/03/scrolling-area-adjustment-for-touchpads-using-ubuntu/](http://blog.eddiemonge.com/2008/08/03/scrolling-area-adjustment-for-touchpads-using-ubuntu/)

---

