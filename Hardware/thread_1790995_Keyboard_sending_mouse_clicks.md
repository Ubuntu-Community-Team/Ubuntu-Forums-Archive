---
title: "Keyboard sending mouse clicks"
date: 2011-06-25
forum: Hardware
---

### Post by aata844 on 2011-06-25
Alright, I have this new backlit keyboard that changes colors. It's useful and all, except, the problem is, the button to change colors is sending mouse clicks. 
There are 4 colors, blue, red, purple, and off. 
When the button is pressed switching from blue to red, it makes ubuntu think the middle mouse button is being held. 
When the button is pressed switching from red to purple, its the left mouse button being held.
When the button is pressed switching from purple to off, the right mouse button is being held. 
Off to blue is perfect, no clicks are being sent. 
But the 3 others make the computer unusable.

So, is there any way I can suppress Ubuntu's reaction to this key being pressed from this device? Any new drivers maybe? Any sort of fix? 

If this should be in another forum, please move it. It had to do with hardware so I thought it fit but the description didn't seem to fit...

---

### Post by gardnan on 2011-06-25
If you would post the exact model of keyboard, and any related drivers, I am sure that would help people figure it out, but it is likely that this is an as of yet unsupported hardware device. But then again, I wouldn't be the person to know...

---

### Post by aata844 on 2011-06-26
But the keyboard works perfectly fine except for this button. It's a Saitek Eclipse II, Model Number KU-0603, with only the default drivers, haven't installed any myself. I'm using the regular USA mapping.

---

### Post by gardnan on 2011-06-26
Hmm, this problem seems a little too specific to one piece of hardware for these forums. The chances of someone on here knowing anything in depth about your device is exceptionally slim. I would recommend checking elsewhere, the best place for this type of question is on the Saitek Website ([http://www.saitek.com/](http://www.saitek.com/)), or their forums ([http://www.saitekforum.com/](http://www.saitekforum.com/)). Also, the manual for your model is available online ([http://www.saitek.com/manuals/Eclipse_II_manual.pdf](http://www.saitek.com/manuals/Eclipse_II_manual.pdf)) but it doesn't reference any Linux specific instructions. To me though, it seems likely that there just isn't proper driver support for this keyboard yet.

---

### Post by aata844 on 2011-06-26
So, there's no way at all to stop Ubuntu from reacting to it? From interpreting that as a click? Ah well, I guess I'll try their place, thanks.

---

### Post by Tortel on 2011-08-13
I have been getting this too.
I think it has to do with a kernel driver change since around 2.6.39, maybe 38.

Ive found that pressing all the buttons on the mouse after changing colors makes it work.

---

### Post by aata844 on 2011-08-14
Thank you Tortel! I can't believe I never found that.

---

### Post by mlerley on 2011-08-25
I am having this exact issue.  I've had the keyboard for months and it worked perfectly well until last night when I decided to bite the bullet and finally upgrade from Maverick to Natty.  Now it is exhibiting this behavior.  Certain Microsoft keyboards seem to have the same problem -- there's a lot of discussion on [this bug]("https://bugs.launchpad.net/ubuntu/maverick/+source/linux/+bug/636311") that seems to be the same sort of thing.  I'm on kernel 2.6.38-11 at the moment; I'll reboot with the previous 2.6.35-30 and see if the problem goes away.  There's some discussion in the comments on that bug about the problem coming and going with different kernel versions. At any rate it seems to not be fixed and somebody should probably escalate this to the proper channels (whatever they may be).

**Update:**

Well, that was a bust.  Does the same thing with 2.6.35-30.  I'm pretty sure that's the kernel I was on before I upgraded.  I think perhaps something has changed with udev that's making X think inappropriate things about the keyboard (e.g., it's a mouse).  I'll try the press-all-buttons thing for now and go add a note to that bug about this.

---

### Post by L_R_N on 2011-09-25
There's a thread on [Debian User Forums]("http://forums.debian.net/viewtopic.php?f=7&t=70507") about this.

---

