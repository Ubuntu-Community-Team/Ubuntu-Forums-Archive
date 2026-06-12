---
title: "ALSA Channels"
date: 2008-09-17
forum: General Help
---

### Post by OutOfReach on 2008-09-17
Ok, I just compiled ALSA and the sound works on my custom kernel (2.6.26.5). But when I try to push the volume up or down, the levels of the channels change. Even when I try to do it from the volume applet. Basically when I put the volume up, sometimes it actually goes up but it just goes down (either one or both channels).
Any link or response will be appreciated.

EDIT: OR if any one of you can tell me how to keep the (Master) channels locked together PERMANENTLY, then I'd be happy.

---

### Post by OutOfReach on 2008-09-20
Bump.

---

### Post by solarwind on 2008-09-20
Exact same problem and situation here.

---

### Post by mikewhatever on 2008-09-21
I use the default Alsa that comes with Hardy and am not sure it's the same, but clicking on the icon beneath the sliders and above the speaker does lock and unlock the channels.

---

### Post by solarwind on 2008-09-21
> **mikewhatever said:**
> I use the default Alsa that comes with Hardy and am not sure it's the same, but clicking on the icon beneath the sliders and above the speaker does lock and unlock the channels.

Doesn't lock for this ALSA. Changing the sliders unlocks it and it goes wonky. So does pressing the buttons on the laptop.

---

### Post by OutOfReach on 2008-09-21
I've tried pressing that lock/unlock button already but the the sliders just go crazy when I try to put the volume up or down either from the applet or the laptop buttons.

---

### Post by solarwind on 2008-09-21
> **OutOfReach said:**
> I've tried pressing that lock/unlock button already but the the sliders just go crazy when I try to put the volume up or down either from the applet or the laptop buttons.

Same here.

Both of us have kernel 2.6.26.5 (compiled ourselves) and alsa >= 1.0.17.

---

### Post by OutOfReach on 2008-09-21
Bump.

---

### Post by OutOfReach on 2008-09-24
Bump.

---

### Post by OutOfReach on 2008-09-27
Bump

---

### Post by stylishpants on 2008-09-27
You're screwed AFAICT.  It sounds like an ALSA bug, or possibly a weird misconfiguration.  All you can do to actually solve the problem is find an alsa version that works properly for your hardware, or wait for one if none exists.

There's a remote chance that it is your alsa configuration that's screwed, this may be a possibility if you've been messing with ~/.asoundrc and friends. 

I too am in this boat, my USB sound card's driver seems to be buggy in recent Ubuntu releases (that's the Creative Soundblaster MP3+, with USB ID 041e:3010).  Raising or lowering the volume by pressing the up/down volume buttons seems to have about a 30% chance of setting the left channel to 0.

I worked around it like this:
1. disable the volume up/down buttons (System->Preferences->Keyboard Shortcuts)
2. map the volume up/down buttons to call a custom volume-changing script that avoids the problem
(Applications->System Tools->Configuration Editor, then edit /apps/metacity/keybinding_commands)

This custom volume-changing script works like this:
1. use amixer to get the current volume
2. use amixer to balance the volume (raise the lower channel's volume to match the higher)
3. use amixer to set the volume to the newly desired value (just bump it up or down by a fixed increment, based on the script's command-line options)
4. use amixer to balance the volume again

Good luck.

---

