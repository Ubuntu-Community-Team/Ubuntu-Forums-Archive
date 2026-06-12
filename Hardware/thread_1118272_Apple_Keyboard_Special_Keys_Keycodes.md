---
title: "Apple Keyboard Special Keys Keycodes"
date: 2009-04-06
forum: Hardware
---

### Post by mkramer on 2009-04-06
I hope everyone is doing well this fine spring evening.  I just plugged in an Apple USB keyboard to my Ubuntu box, and lo and behold, Ubuntu captured the special keys for Vol+, Vol-, and mute, that come with Apple keyboard firmware, and displayed the appropriate Volume bezel HUD as it changed the volume.

While it is exceedingly cool that Ubuntu supports this extra functionality out of the box, I was actually hoping to use Ubuntu to find out what those keycodes are, using xev, so that I could fix a Windows keyboard to work on one of my Mac boxen.  Unfortunately, as in Mac OS X, xev does not show the keycodes for these keys: it looks like the system is eating them and not passing them on.  Since someone had to have known the keycodes in order to write a driver that responds to them, I figure this knowledge is out there somewhere in Ubuntu land.  I wonder if someone can point me in the right place to find this out: either the straight answer, a way to find the answer, would be appreciated.

TLDR: WHat are the special keycodes that Apple keyboard send when you press Vol+/Vol-/Mute/Eject?

 Extra credit: what is a KeymapNotify event?  This is what happens when I press vol+ with a xev window open:

```
KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

```

Thanks in advance my homies.

---

### Post by mkramer on 2009-04-06
As a followup, I found the key codes using sudo showkey -k in a real TTY buffer.

114 - Vol-
115 - Vol+
113 - Mute
161 - Eject
185 - Brightness -
186 - Brightness +

Now I just have to figure out how to send them to the Darwin kernel...

---

### Post by Pseudo-Morph on 2010-05-25
> **mkramer said:**
> As a followup, I found the key codes using sudo showkey -k in a real TTY buffer.

114 - Vol-
115 - Vol+
113 - Mute
161 - Eject
185 - Brightness -
186 - Brightness +



Awesome, this is just what I was looking for. 

I have an [Apple slim aluminium keyboard (0220)]("https://help.ubuntu.com/community/AppleKeyboard#Apple%20slim%20aluminium%20keyboard%20%280220%29"), below is a full list of keycodes

224 - F1/-Brightness
225 - F2/+Brightness
120 - F3
204 - F4
229 - F5
230 - F6
165 - F7/Prev Track
164 - F8/Play/Pause
163 - F9/Next Track
113 - F10/Mute
114 - F11/-Vol
115 - F12/+Vol
161 - Eject
183 - F13
184 - F14
185 - F15
186 - F16
187 - F17
188 - F18
189 - F19

---

