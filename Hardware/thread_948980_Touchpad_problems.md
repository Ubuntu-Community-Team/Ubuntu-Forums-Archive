---
title: "Touchpad problems"
date: 2008-10-15
forum: Hardware
---

### Post by ojve on 2008-10-15
Hi!

I'm running Ubuntu Intrepid and I've been trying to get my touchpad mouse moving properly since the install.

I installed gsynaptics and edited xorg.conf. This worked until maybe yesterday or the day before that. I think it was a version upgrade that changed it.

The xorg.conf has been regenerated to a ver short one:
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Whenever I try to change it I get an error when logging in saying Ubuntu is in low graphics mode or some such. All the while I still have no change to touchpad behavior.

I then discovered the 11-x11-synaptics.fdi. I tried enabling SHMConfig through it with no luck (System->Preferences->touchpad still says I need to enable SHMConfig to use it). 

Looking closer at 11-x11-synaptics.fdi I figured that maybe I don't have a Synaptics touchpad. This is how it looks:
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
	<merge key="input.x11_options.SHMConfig" type="string">true</merge>
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
        <merge key="input.x11_options.MaxSpeed" type="string">1.0</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.60</merge>
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

the line 
<merge key="input.x11_options.SHMConfig" type="string">true</merge>

has been added by me.

Does this mean that I have an appletouch touchpad? It seems unlikely, since I have an HP (model dv2935la). How do I find out what brand my touchpad is?

The problems I have are:
- The acceleration is all right, but the cursor speed is way too slow when moving the fingers slowly
- Sometimes the touchpad doesn't even react to my fingers or the cursor   suddenly slows down or stops and then continues

Could anyone please help me with this?


Thx!
//T

---

### Post by kerry_s on 2008-10-15
you should not be messing with that file. everything you need to do is in /etc/X11/xorg.conf, you need to add a section for the touchpad.

first find out what you have:
```
cat /proc/bus/input/devices
```

second add it to xorg.conf:
```
 Section "InputDevice"
   Identifier  "Synaptics Touchpad"
   Driver      "synaptics"
   Option      "SendCoreEvents"
   Option      "Protocol" "auto-dev"
   Option      "SHMConfig" "on"
 EndSection

```

```
Section "ServerLayout"
	InputDevice	"Synaptics Touchpad"
EndSection

```

if you have a alps touchpad like i do it's a little different, i'll put mine, i have click disabled:

```
Section "InputDevice"
        Identifier      "Alps Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents" "true"
        Option          "Device" "/dev/psaux"
        Option          "Protocol" "AlpsPS/2"
        Option          "TapButton1" "0"
        Option          "TapButton2" "0"
        Option          "TapButton3" "0"
        Option          "MinSpeed" "0.60"
        Option          "MaxSpeed" "0.60"
EndSection
```

```
Section "ServerLayout"
	InputDevice	"Alps Touchpad"
EndSection

```

---

### Post by ojve on 2008-10-16
> you should not be messing with that file. everything you need to do is in /etc/X11/xorg.conf

wgrant seems to be saying differently in [<this thread>]("http://ubuntuforums.org/showthread.php?t=905362")

Anyway, I tried what you said. It seems I have an ALPS toughpad. I added the last two part to xorg.conf. Rebooting I get the same error as before. It says Ubuntu is in low graphics mode or some such and then asks me how I want to reconfigure the graphics. Even though I reconfigure the same dialog keeps popping up, no matter how many times I reboot. The only solution is to change xorg.conf back the original.

//T

---

### Post by kerry_s on 2008-10-16
maybe your not doing it right, i'll use the xorg.con you posted. try this:

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "InputDevice"
        Identifier      "Alps Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents" "true"
        Option          "Device" "/dev/psaux"
        Option          "Protocol" "AlpsPS/2"
        Option          "MinSpeed" "0.60"
        Option          "MaxSpeed" "0.60"
        Option          "SHMConfig" "on"
EndSection

Section "ServerLayout"
	Identifier	"Default Screen"
	InputDevice	"Alps Touchpad"
EndSection


```

---

### Post by ojve on 2008-10-16
Trien that with copy/paste, same result. This time even replacing xorg.conf with the backup didn't help. Had to do the sudo dpkg-reconfigure -phigh xserver-xorg

//T

---

### Post by ojve on 2008-10-16
I solved it.

I added the line with SHCMConfig to the alps part of 11-x11-synaptics.fdi and now it works.

Thx for your help anyway!

//T

---

