---
title: "ThinkPad X61 + Ubuntu 8.10 - Fixes and Minor Issues"
date: 2009-01-04
forum: Hardware
---

### Post by brohken on 2009-01-04
So I installed Ubuntu on my X61 from a USB key and that worked like a dream. I actually kept my hidden windows partition so I can rebuild Vista from the drive just in case. I have a few questions and didn't really see a guide to getting the X61 fully working, so I figured I'd start one here. ThinkWiki.org, which is a great resource, unfortunately only goes to 8.04.


**[SIZE="4"]What Works[/SIZE]**

Mostly everything out of the box. It was a fairly more pleasurable experience then the last time I tried Ubuntu with this laptop. I think that was either 7.10 or 8.04.


**[SIZE="4"]What Almost Works[/SIZE]**

**Wireless** was broken out of the box but reinstalling netapplet from the synaptic package manager fixed that. Ethernet obviously works.

The **middle scroll** button on the ThinkPad seems not be able to scroll out of the box. I fixed that by adding

```
# FIX FOR BROKEN EVDEV/HAL for TrackPoint scrolling:
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Wheel Emulation" 8 1
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Wheel Emulation Button" 8 2
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Wheel Emulation Y Axis" 8 4 5

Add this to /home/user/.profile
```

The **thinkvantage** button and the **fn+space hotkey** are not recognized by default. I got these working, but have no idea what I did. :P If I find the fix, I will post it. If someone knows, please add a post.


**[SIZE="4"]What Doesn't Work[/SIZE]**

**Bluetooth** seems to turn on automatically each time I restart. Now I don't want to disable it completely. Just want to turn it on when my computer starts. Cureently Fn+F5 seems to disable bluetooth so this is really a minor inconvenience. I read a bit on here, but am a noob so don't know if this was solved: [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/280811](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/280811)

**Wireless** doesn't work when resuming from Hibernate or Sleep mode. Netapplet finds the networks, but can't seem to connect.

**Screen dimming and brightness** don't do what I want them to.

What I want: Screen should dim to 1% on battery. Should go to 100% on AC. Screen should dim on idle. Should return to the last brightness when no longer idle.

What happens: The screen doesn't dim/brighten when I go from AC to battery or battery to AC. Screen doesn't dim on idle. Before, it dimmed, but wouldn't go back to it's original brightness when i moved the mouse. I had to manually change the brightness.

Here are my settings:

[IMG]http://img253.imageshack.us/img253/9406/screenshotconfigurationzc2.png[/IMG]

[IMG]http://img246.imageshack.us/img246/3719/screenshotpowermanagemexe4.png[/IMG]

[IMG]http://img246.imageshack.us/img246/5295/screenshotpowermanagemead8.png[/IMG]


[SIZE="4"]**Battery Life**[/SIZE] 

This kind of sucks in Ubuntu 8.10. This is the only real disadvantage that I can see. With normal use, on low brightness I used to get 6-7 hours of use in Windows Vista. In Ubuntu I get barely 4 hours. That's a huge difference and wonder if there's anything I can do to correct this.


Appreciate the help!

---

### Post by brohken on 2009-01-04
**[SIZE="4"]Must Have Software[/SIZE]**

This is a list I'll expand on that is specifically for ThinkPads and works well on the X61.

**Pidgin BlinkLight**: Blinks when someone IM's you in Pidgin. Works very well and is super easy to install. Just search "blinklight" in synaptic package manager and install. It will appear as a plugin in pidgin.

**ThinkFinger**: This is supposed to make the fingerprint reader allow you to fill in your system password. I have not yet tried this and can't confirm if it works.

---

### Post by brohken on 2009-01-08
anyone out there?

---

### Post by srt4play on 2009-01-09
Hi brohken, your fix for trackpoint scrolling works but does not survive suspend/resume.  I have to restart X to get it working again, any ideas?

---

### Post by srt4play on 2009-01-09
brohken, I found the answer to my above problem in [this]("http://ubuntuforums.org/showthread.php?t=964265&highlight=trackpoint") thread.

---

### Post by zhwu on 2009-02-16
Thanks brohken, your post did help me a lot. Any updates for ThinkVantage button and the Fn + Space hotkey issue? It's still not working on my X61.

---

### Post by SaintDanBert on 2009-02-18
> **brohken said:**
> anyone out there?
I have an X61 Tablet, but I'm still running Hardy for a variety of reasons.

Has anyone here managed to get the mouse dial (tablet mode) to work as a mouse input device?

Also, how does one config the stylus button and stylus-eraser?

Lastly, I have Fn+ThinkVantage launch an xterm if anyone cares.  Fn+Space and Fn+F3 are both noop for me. I'd love to have a nice battery state display applet launch for Fn+F3 and a magnifier launch Fn+Space. I simply have not found the apps to use.

~~~ Saint 0;-D

---

