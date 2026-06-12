---
title: "Disabling 'tap's from a touch pad"
date: 2008-12-05
forum: Hardware
---

### Post by hydrogen18 on 2008-12-05
Hi, I have kubuntu 8.10 x86-64 on my compal ifl90 laptop. Everything is working fine for the most part, except I cannot figure out how to disable the 'tap to click' feature of my touchpad under kubuntu. This is exceptionally problematic as it is completely impractical to use with this enabled. I've tried playing with syndaemon but anytime I use it I get the following error:

```

ericu@sager-ubuntu:~$ syndaemon
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  148 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  10
  Current serial number in output stream:  10
ericu@sager-ubuntu:~$



```

any idea how to go about disabling the tap to click feature?

---

### Post by Zorael on 2008-12-05
I think you want to have a look at **/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi**.
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
        <merge key="input.x11_options.RightEdge" type="string">1280</merge>
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
        <merge key="input.x11_options.**[COLOR="DeepSkyBlue"]MaxTapTime[/COLOR]**" type="string">223</merge>
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
Perhaps set MaxTapTime to 0?

edit: Normally you'd simply have to disconnect and reconnect a device to get HAL to reload its settings for that device, but if yours is a laptop and the touchpad is connected via some internal PS/2 port that's fairly difficult. So I guess the best way is to simply log out, Ctrl+Alt+Backspace, then see if it worked.

edit²: er, or do you have to save the changed file into **/etc/hal/fdi/policy/**, too? Someone clarify, please.

---

### Post by hydrogen18 on 2008-12-06
I tried adding the line for MaxTapTime and setting it to 0 in both

```

/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi
/etc/hal/fdi/policy/11-synaptics-options.fdi

```

And restarted the X server between each change and test. No change in functionality, taps are still enabled.

Any more ideas?

---

### Post by elysion on 2008-12-22
I've been looking for a solution to this also. Also would be nice to get the circular scrolling to work. I found a webpage that had instructions on how to get the 2 finger scrolling to work, but it did not work for me. I've tried to edit the 11-synaptics-options.fdi files, but that did not work for me. Any suggestions?

---

### Post by gumpu on 2008-12-23
Adding 

<device>
     <match key="input.x11_driver" string="synaptics">
         <merge key="input.x11_options.MaxTapTime" type="string">0</merge>
     </match>
</device>

to 

/etc/hal/fdi/policy/preferences.fdi

and then rebooting solved it for me.

---

