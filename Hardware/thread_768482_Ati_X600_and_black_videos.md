---
title: "Ati X600 and black videos"
date: 2008-04-26
forum: Hardware
---

### Post by iraiscoming223 on 2008-04-26
Hello Everyone!:)
Have a tiny problem out here!
I've an ATI X600 Mobility Radeon on my laptop, and when I switch to Desktop Effects (metacity compositing as well) windows showing videos (totem, and so on..) turns to black.
There's no way to see the video but keep moving the window around.
Anyone know how to get rid of it please?
Thanks in advance!
Marco

Things to know:
- Yes, I have installed the latest ATI drivers
- I'm using Ubuntu 8.04
- The compiz setting for "Video Playback" is set to on (no changes if set to on)
- No, I don't want to use a hammer to get rid of it :lolflag:

p.s.(One day I found a trick to use Mplayer with a patch that let it plays video with composite enabled... but that's not the idea I have in mind.. :P)

---

### Post by Artsaypunk on 2008-04-28
Sorry I can't help ease your pain.  I thought I'd just add my woes.  I have the exact same symptoms with an ATI Radeon Mobility x300.  I also notice that my CPU runs extremely high with effects enabled and often peaks out at 100% just by opening an application.  I installed the drivers through EnvyNG, and they seem to be installed correctly by my eye (but then I'm still new to ubuntu).

There are so many threads concerning the ATI cards, and I've searched through them for hours, but I can never find any solutions that match my situation.  It's quite frustrating.  If anyone has any ideas, let me know what outputs would be helpful.

---

### Post by iraiscoming223 on 2008-04-28
> **Artsaypunk said:**
> Sorry I can't help ease your pain.  I thought I'd just add my woes.  I have the exact same symptoms with an ATI Radeon Mobility x300.  I also notice that my CPU runs extremely high with effects enabled and often peaks out at 100% just by opening an application.  I installed the drivers through EnvyNG, and they seem to be installed correctly by my eye (but then I'm still new to ubuntu).


Well, I've never had that kind of problem (fortunately) but I've read somewhere (dunno where, sorry) that it was something concerning an ATI setting. maybe (don't trust me so much, I barely know what I'm talking about! :P) something with (in)direct rendering and/or overlay...
Give it a try, use
```
sudo aticonfig
```
and scroll through the options... =)

And, this is just a small hint, installing drivers from AMD packages is not that hard, give it a try... :)
If you want an (outdated) how-to on how to install ATI drivers (that's for my card, though), have a look [here]("http://www.wannanic.com/blog/index.php?postid=119")... I wrote this on Dec, 2007. 
Let me know if that (I mean the ATI settings, apart from the guide) has been useful for you... :)

Greetings From Italy! ;)
Marco

---

### Post by Artsaypunk on 2008-04-29
> **iraiscoming223 said:**
> 
```
sudo aticonfig
```
and scroll through the options... =)

I'll take a look, although I hate changing settings that I don't truly understand, as it's just about the worst form of trial and error.  Sometimes you fix the problem and don't even know how you did it! 

> And, this is just a small hint, installing drivers from AMD packages is not that hard, give it a try... :)

I tried installing the drivers directly in gutsy and found that the repository versions worked better for me. But you're right, it wasn't that hard.   Back then, I wasn't satisfied with the card setup, but it was "mostly" working with the repositories and Xgl.  This time, I read up on Envy and thought I'd give that a try for maintaining the driver.  That's what I'm currently running with, but I did try the repository version on a clean install and I got basically the same choppy results.

I love everything about Ubuntu, and despite my video problems I've completely switched over.  Unfortunately, my CPU ramping up (presumably the video card isn't handling the display and the CPU is forced to instead) causes other little problems (I can get the CPU up to 80% just by wobbling a window around).  So if I can just get this worked out I'll be a happy open source convert.

If anyone can add some input here are some stats for my situation.

Dell Inspiron 9300
RAM: 1.2 GB
Processor: 1.73 Ghz
Video Card: ATI Mobility Radeon X300

Here is the output for fglrxinfo:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X300
OpenGL version string: 2.1.7412 Release
```

Here is the xorg.conf

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Driver		"fglrx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

---

### Post by iraiscoming223 on 2008-04-29
ok, I'm sorry it didn't work... Let's wait for some guru coming down :P

---

### Post by Artsaypunk on 2008-05-06
Doesn't look good does it...

Well, from hours of searching these forums and making posts for help that no one responds to, it seems like there might be no answer to this.  Maybe we'll just have to wait for another ATI driver release... although it didn't help much last time.

---

### Post by iraiscoming223 on 2008-05-06
> **Artsaypunk said:**
> Doesn't look good does it...

Well, from hours of searching these forums and making posts for help that no one responds to, it seems like there might be no answer to this.  Maybe we'll just have to wait for another ATI driver release... although it didn't help much last time.

Yeah, I guess this is the only way...
I gave up hope a long time ago! ;) And I gave up "Compizing" as well! :lolflag:

---

