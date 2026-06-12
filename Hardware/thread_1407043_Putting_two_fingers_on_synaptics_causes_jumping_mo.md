---
title: "Putting two fingers on synaptics causes jumping mouse"
date: 2010-02-14
forum: Hardware
---

### Post by LynxofCP on 2010-02-14
Hi guys, I decided to try installing ubuntu on the metal of my laptop instead of virtualized and I've run into a bit of a snag that's driving me nuts.

In windows, I've gotten very used to two finger scrolling. Moving to ubuntu, I've found that the moment I put two fingers on my touchpad the cursor starts jumping around like a neurotic mutant teleporting mouse.

Does anybody have any ideas how I can get it to take a few tranquilizers and behave normally?

Thanks

Edit:
Running Ubuntu 9.10 Desktop 64-bit
Laptop: Dell Studio 15 1557

---

### Post by Mechaphoenix25 on 2010-02-23
I can confirm this, clean install of Karmic on a Studio 1558.  I had it work for a while when messing around with my xorg and ati drivers, but it's back again.  :(  any clues on what I did to fix it?

---

### Post by benmoran on 2010-02-23
You have to enable 2-finger scrolling. It's under the menu.
System->Preferences->Mouse
Then click on the touchpad tab and you'll find the option there.

---

### Post by Mechaphoenix25 on 2010-02-24
I did enable two-finger scrolling, it was the first thing I tried.  Not only did it not change anything about the issue, for some reason Synaptics sees the studio 1555/1557/1558 touchpads as non-multi-touch, even though windows 7 has full pinch-zoom capabilities on them.  I did manage to get it fixed by poking around with /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi
I'm posting it below.

```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <!-- Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. -->
        <!-- EXAMPLES:
        Switch on shared memory, enables the driver to be configured at runtime
	--> <merge key="input.x11_options.SHMConfig" type="string">true</merge>

	<!--
	Maximum movement of the finger for detecting a tap
	<merge key="input.x11_options.MaxTapMove" type="string">2000</merge>

	Enable vertical scrolling when dragging along the right edge
	<merge key="input.x11_options.VertEdgeScroll" type="string">true</merge>

	Enable vertical scrolling when dragging with two fingers anywhere on the touchpad
	<merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>

	Enable horizontal scrolling when dragging with two fingers anywhere on the touchpad
	<merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>

	If on, circular scrolling is used
	<merge key="input.x11_options.CircularScrolling" type="string">true</merge>

	For other possible options, check CONFIGURATION DETAILS in synaptics man page
        -->
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="Inspiron 1011">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">90</merge>
            <merge key="input.x11_options.AreaBottomEdge" type="string">4100</merge>
        </match>
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="Inspiron 1012">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">90</merge>
            <merge key="input.x11_options.AreaBottomEdge" type="string">4100</merge>
        </match>
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="HP MiniNote 1000">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">200</merge>
        </match>
    </match>
  </device>
</deviceinfo>

```

I also ended up turning off two-finger scrolling, as it was too inaccurate.

---

### Post by ftaylor on 2010-03-06
I have exactly the same problem. This didn't fix anything for me, did you change/install anything else?

---

### Post by LynxofCP on 2010-03-07
I too tried this method to no avail.

---

### Post by Mechaphoenix25 on 2010-03-07
Sorry guys, about a day or so after I posted that solution, the jumping issue came back.  Since then, it's been on and off, without any change in configuration.  The weird thing is that both the xinput fix and the changed .fdi fixed the issue temporarily, but now neither one works for me at all.  I've been poking around, I have yet to find anything that fixes it on a permanent basis.

---

### Post by jfrorie on 2010-03-24
I'm fairly certain this is related to the bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191)

---

### Post by ehtony110 on 2010-04-18
I'm having a similar problem with my synaptics touchpad as well.  An interesting fact to note is that when "synclient -m 50" is run with 2 fingers on the touchpad, synclient reports that only 1 finger is touching while the mouse x and y coordinates jump all over the place.  So far I have been able to find no patches or workarounds for this probem, and it's really quite frustrating :(

---

### Post by ftaylor on 2010-05-04
This seems to be resolved for me with Ubuntu 10.04.

---

### Post by ehtony110 on 2010-05-06
10.04 did not resolve the issue for me at least.  Are there going to be any synaptics touch pad driver updates available anytime soon?

---

### Post by pravincar on 2010-06-13
Same issue with Ubuntu 10.04 on Acer Timeline 4810T. Also I would like to use the multitouch features like zoom and window switching with the synaptics touchpad. Any ideas?

---

### Post by pravincar on 2010-06-13
Update manager applied loads of updates today and the issue seems to be resolved! Cheers:KS

---

