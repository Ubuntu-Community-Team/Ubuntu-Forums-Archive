---
title: "HP Spectre x360 - problems &amp; sollutions"
date: 2015-11-30
forum: Hardware
---

### Post by RobertFM on 2015-11-30
**Hewlett-Packard**
**HP Spectre x360 (13-4150nd)**

Intel® Core i7-6500U with Intel HD Graphics 520


I installed Ubuntu Gnome 15.10 from live USB with UEFI (F9)
Updated to Gnome Shell 3.18


**What Works**

[LIST]
[*](Touch) screen
[*]Touch pad
[*]Touch screen pen (DELL Active Stylus 750-AAHC)
[*]Audio
[*]Bluetooth
[*]Wifi
[*]Media keys
[*]Web-cam
[/LIST]


**What not (yet) works:**

[LIST]
[*]Orientation sensor for auto rotation of screen
[/LIST]

**Problems solved**
Dell stylus button was middle click, now right click. With script below.
```
#!/bin/sh

# swap middle and right button
CM_STORM_RECON_ID=$(xinput list | grep "Touchscreen Pen" | head -n 1 | sed -r 's/.*id=([0-9]+).*/\1/')
xinput --set-button-map ${CM_STORM_RECON_ID} 1 3 2

```

Keyboard not showing in tablet/touchscreen mode. By using "slide for keyboard" extension:
[https://extensions.gnome.org/extension/993/slide-for-keyboard/](https://extensions.gnome.org/extension/993/slide-for-keyboard/)

Touch pad still active in tablet mode. Easily disabled via extension "Toggle touch pad":
[https://extensions.gnome.org/extension/935/toggle-touchpad/]("https://extensions.gnome.org/extension/935/toggle-touchpad/\")

---

### Post by Emily_Shepherd on 2016-03-14
Hiya - did you have any problems with your headphone / speaker config with it? I've got the same laptop but can't get linux to properly recognise when the headphones are connected :/

---

### Post by RobertFM on 2016-03-21
Hi Emily, 

I use Ubuntu Gnome 15.10 with Gnome Staging (Gnome Shell 3.18) and it registers my headphone without any problems. Headphone and microphone work just fine.

What happens when you plug a headphone in the laptop?

---

### Post by christianbrooker on 2016-04-23
have you had any luck with screen rotation? I've just installed gnome 3.20 on ubuntu 16.04. screen rotation still doesn't work and the other problem I'm having is when i physically rotate the screen to portrait and then physically rotate it back again to landscape it enables airplane mode. it's like the sensors are picking the return to landscape orientation as the airplane mode button being pressed.

---

### Post by ptt2 on 2016-06-07
It seems the rotation sensor is not yet supported by the kernel, see [http://ubuntuforums.org/showthread.php?t=2317737](http://ubuntuforums.org/showthread.php?t=2317737) (although earlier versions of the Spectre x360 might use the usb based sensor solution?)

---

### Post by st_ab on 2016-06-09
Would you recommend the Spectre x360?

---

### Post by RobertFM on 2016-06-13
@st_ab, I would definitely recommend the Spectre x360. Esspecially now auto-rotation is working. Battery life is great, screen is gorgeous, laptop is gorgeous  and fast. It is my favourite laptop to date.

@ptt2, by accident I noticed that auto-rotation is working now. I created a new user and noticed that (after standby/resume) the auto-rotation was working. So I moved to a fresh user and rotation is working just fine. I just need to find how to get it working before 1st standby.

---

