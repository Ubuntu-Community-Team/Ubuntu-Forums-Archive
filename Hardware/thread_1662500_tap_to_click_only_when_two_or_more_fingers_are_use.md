---
title: "tap to click only when two or more fingers are used"
date: 2011-01-08
forum: Hardware
---

### Post by peridotfaceted on 2011-01-08
I have a new laptop (HP G62) and am trying to get the touchpad into a comfortable state. The physical touchpad buttons are a single flexible bar supported in the middle, so that clicking both buttons at once is very awkward. So I needed another way to get button-3 clicks (for example to paste text into a terminal). Tap-to-click works; now tapping with two fingers gives me button 2 and three fingers gives me button 3. Great. Unfortunately, tapping with one finger gives me button 1 - and there's no very clear distinction between a tap and ordinary mouse motion (see all the "I hate tap-to-click" posts), so I have stray clicks all over the place. What I would like to do is make tap-to-click work only for two- or three-finger taps, but not one-finger taps. Is this possible?

The touchpad appears to be a genuine synaptics touchpad (driver reports SynPS/2), and it supports multitouch (so I had to download an out-of-the-repository package. synaptics-dkms, to get two-finger anything working). Neither the extremely limited mouse preferences dialog nor the gpointing-device-settings application offer this as an option, as far as I can tell. I am running Maverick (amd64, if it matters). 

The touchpad not tactilely distinguishable from the rest of the laptop surface, having the same crossing-lines texture, so touchpad edges are awkward to locate (hence the need for two-finger scrolling). The touchpad also has a recessed LED in the top left corner; under windows one can tap the LED (probably in fact one is tapping the top left corner of the touchpad) and it toggles both the LED and the touchpad. This also doesn't work under Linux, but it's not a priority.

My ideal solution would be to have one-finger taps do nothing, just as when tap-to-click is off. Two-finger taps would be middle-button presses. Three- or more-finger taps would not be necessary; I can right-click with the physical button. But in any case it would be enough to disable one-finger tapping in any way that still allowed me to produce middle-button clicks without having to press both buttons simultaneously.

Is there some sort of configuration tool that will let me make these changes?

Thanks.

Edit:

I found an awful kludge that gets the system working. First of all, synclient -l lists many configuration options, one of which is the magic one. So as a first attempt I ran:
```

synclient TapButton1=0

```
(there are also TapButton2 and TapButton3, which control which button two- and three-finger tapping generates). This deactivates one-finger tapping. Unfortunately, this configuration setting doesn't persist; after some time it goes back to the way it was. So the awful kludge is to simply write a shell loop that runs this command every five seconds, and put it in my startup programs. The real solution would be to find the program that keeps resetting this and fix it...

---

