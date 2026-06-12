---
title: "Asus G50V - Karmic Multitouch issues"
date: 2009-12-23
forum: Hardware
---

### Post by Zilliano on 2009-12-23
I know my laptop comes with a Synaptics touchpad (Or at least, that's what both Windows and the Ubuntu terminal tell me), and I've got it running the synaptics driver according to the terminal, but I can't seem to get it to do two finger scrolling or any of the other multitouch features. Is it simply incapable? I was under the impression that all Synaptic touchpads were able to use at least some form of multitouch, but I could be wrong.

Before it's asked, I do have SHMconfig set to "yes", though I've tried true and on as well, to no effect.
System > Preferences > Touchpad will open, but none of the settings in it affect the touchpad seemingly, and the sliders reset whenever I exit out of it.
However, I can edit by using the Touchpad tab in Mouse, and it allows me to select two-finger scrolling, but when I try to use it nothing happens.

Any help is greatly appreciate... I would love to get Multitouch working if I can.

---

### Post by Zilliano on 2009-12-24
I'm guessing no one has any help for me on this issue?

---

### Post by Zilliano on 2009-12-24
Oh come on. Someone at least tell me it's hopeless or something.

---

### Post by Zilliano on 2009-12-24
What a great Christmas present, a half-functioning touchpad. >_>

---

### Post by Zilliano on 2009-12-24
I've been fiddling, and it still only shows one finger. I know it's synaptics, but is there a way of determining if my particular model is a Synaptics that doesn't support multitouch?

---

### Post by Zilliano on 2009-12-30
I'm at my end with this. >.<

---

### Post by sleepee on 2010-01-01
i have the exact same problem..
apparently there's a way to fix it though...  it seems other people have been able to enable it by editing xorg.conf but i'm not sure..

---

### Post by Zilliano on 2010-01-03
> **sleepee said:**
> i have the exact same problem..
apparently there's a way to fix it though...  it seems other people have been able to enable it by editing xorg.conf but i'm not sure..

Yeah, I'm figuring that the laptop is just viewing the pad as a mouse, and not a synaptics pad. I wish someone with knowledge of this would help. >.<

---

### Post by beefstu on 2010-01-04
different laptop but could have same solution to make it work [http://blog.twinapex.fi/2009/10/11/setting-up-multi-touch-scrolling-for-ubuntu-9-10-karmic-koala-linux-on-asus-eee-1005ha-netbook/](http://blog.twinapex.fi/2009/10/11/setting-up-multi-touch-scrolling-for-ubuntu-9-10-karmic-koala-linux-on-asus-eee-1005ha-netbook/)

Best of luck!

---

### Post by poet_imp on 2010-01-15
This script is from the link above. I have tested it on my Thinkpad T61 running Kubuntu 9.10 and it works flawlessly! It does take some getting used to, though.

```
#!/bin/sh
#
# Use xinput --list-props "SynPS/2 Synaptics TouchPad" to extract data
#

# Set multi-touch emulation parameters
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1

# Disable edge scrolling
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 8 0 0 0 

# This will make cursor not to jump if you have two fingers on the touchpad and you list one
# (which you usually do after two-finger scrolling)
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 32 110


```

---

### Post by not-too-sharp on 2010-02-17
Can't be done.  The Synaptics touchpad on the G50V has a newer version of the touchpad firmware.  This version will not recognize multiple fingers and is also not pressure-sensitive. I don't know how to check the version under Ubunu, but my G50V is set up to dual-boot alongside Vista.  Synaptics has a Windows utility that will graph finger pressure and it shows no difference between one, two or three fingers, nor does it change with varying finger pressure.  I do know how to check the firmware version using Windows, but I'm currently booted into Koala.  Sorry.

I would like to find a way to either downgrade the firmware in the touchpad or physically replace it with an earlier version.  I know from experience that the older versions of the Synaptics touchpads did indeed support multi-touch gestures.  I will (if I ever remember to) contact Synaptics via telephone to inquire about sending my touchpad in and having the firmware downgraded, or seeing if they have an earlier version that will be a drop-in replacement.  I have attempted contacting them via e-mail without any response.  Go figure.

Hope this helps...
dicky

---

