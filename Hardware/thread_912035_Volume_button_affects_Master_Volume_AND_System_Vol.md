---
title: "Volume button affects Master Volume AND System Volume"
date: 2008-09-06
forum: Hardware
---

### Post by Ailurus on 2008-09-06
Hi all,

I recently installed Ubuntu on my IMB Thinkpad (T60), and most things work very well. 
One of the things that doesn't is that when I press the volume+ button on my laptop, the master volume is affected by it, as well is the the system volume (with this I mean the general volume of my laptop). Because of this, the volume increases exponential which is of course not my intention ;).

I installed tpb, which provided a blue volume bar in my screen, under the small orange one of Ubuntu. Speaking of it, the blue one is suddenly gone... Hmm nevermind, this one indicated the volume of the system (I think), the orange something different.

Any ideas how to fix this?

Pieter.

---

### Post by kostkon on 2008-09-06
> **Ailurus said:**
> Hi all,

I recently installed Ubuntu on my IMB Thinkpad (T60), and most things work very well. 
One of the things that doesn't is that when I press the volume+ button on my laptop, the master volume is affected by it, as well is the the system volume (with this I mean the general volume of my laptop). Because of this, the volume increases exponential which is of course not my intention ;).

I installed tpb, which provided a blue volume bar in my screen, under the small orange one of Ubuntu. Speaking of it, the blue one is suddenly gone... Hmm nevermind, this one indicated the volume of the system (I think), the orange something different.

Any ideas how to fix this?

Pieter.
Open your sound preferences (i.e. *System -> Preferences -> Sound*) select the *Devices* tab and go to the *Default Mixer Tracks* section. From there, you should select your sound card from the *Devices* drop-down menu and below select which volume level you want your laptop's volume buttons to control.

I assume that currently two volume levels are selected. Just select one, better this to be the *Master* volume level, and that's it, problem solved.

---

### Post by Ailurus on 2008-09-06
Thank you, but there was just one option selected, "Master". A friend of mine told that none of the indicators (Master, PCM) ought change, like in Windows XP.

Think of the volume-button as the one on your radio or something, you directly change the volume with it. The master (and PCM) are two other possibilities to change the volume, neither should be affected by the button itself! 
Maybe you thought I was talking about a volume-button on a keyboard, but it's the one on my laptop.

When I select nothing at all, the Master volume still changes when I use the button.

---

### Post by Ailurus on 2008-09-07
Any more ideas :)? Maybe from people that use a T60 (or something equal) themselves? Every time I change the volume, I now have to adjust 2 or 3 things until it's OK, which isn't optimal...

---

### Post by montoya_007 on 2008-09-07
> **kostkon said:**
> Open your sound preferences (i.e. *System -> Preferences -> Sound*) select the *Devices* tab and go to the *Default Mixer Tracks* section. From there, you should select your sound card from the *Devices* drop-down menu and below select which volume level you want your laptop's volume buttons to control.

I assume that currently two volume levels are selected. Just select one, better this to be the *Master* volume level, and that's it, problem solved.

My buttons where displaying only the volume on screen. It looked like it worked when I pressed the buttons, but it didnt affected the sound. This solved my problem. Thanks!!!

---

### Post by AnythingBut on 2008-11-01
Hey Ailurus,

I think [http://ubuntuforums.org/showthread.php?p=6081235](http://ubuntuforums.org/showthread.php?p=6081235) applies to you.  It's Intrepid specific, but it links to an older thread that has a fix for Hardy and Gutsy.

---

