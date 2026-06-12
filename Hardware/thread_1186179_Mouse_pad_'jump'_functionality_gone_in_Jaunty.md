---
title: "Mouse pad 'jump' functionality gone in Jaunty"
date: 2009-06-13
forum: Hardware
---

### Post by afinger on 2009-06-13
I recently updated to Jaunty, and it seems really nice. 

One thing i noticed, however, is that the mouse pad functionality has changed since previous versions of Ubuntu. You can no longer quickly 'jump' over the screen -- this could previously be done by pressing a point on the mouse pad with one finger while at the same time another finger press down another point in the mouse pad. Then releasing the first finger quickly moves the pointer to the new point determined by the second finger. This no longer works in Jaunty, the pad is only sensitive to one finger at a time. 

Am I the only one with this problem? Is this just some option which you can change? Or why has this function just been removed? I did not find anything under Preferences/Mouse.

Glad for suggestions.

---

### Post by briguy47 on 2009-06-14
> **afinger said:**
> I recently updated to Jaunty, and it seems really nice. 

One thing i noticed, however, is that the mouse pad functionality has changed since previous versions of Ubuntu. You can no longer quickly 'jump' over the screen -- this could previously be done by pressing a point on the mouse pad with one finger while at the same time another finger press down another point in the mouse pad. Then releasing the first finger quickly moves the pointer to the new point determined by the second finger. This no longer works in Jaunty, the pad is only sensitive to one finger at a time. 

Am I the only one with this problem? Is this just some option which you can change? Or why has this function just been removed? I did not find anything under Preferences/Mouse.

Glad for suggestions.

This is probably because of an update to your pad's driver.  I know a lot of people find the dual-sensitivity an annoyance, so maybe the developers coded it out.

Without the specs of your mousepad, I can't know for sure, but that's my best guess.  :)

---

### Post by afinger on 2009-06-14
> **briguy47 said:**
> This is probably because of an update to your pad's driver.  I know a lot of people find the dual-sensitivity an annoyance, so maybe the developers coded it out.

Without the specs of your mousepad, I can't know for sure, but that's my best guess.  :)

Thanks for the answer. I actually imagine that the dual sensitivity speeds up my browsing -- so it would be nice to have it back :p.  Here's some information about my pad (fram hardinfo) if it helps:

Name   SynPS/2 Synaptics TouchPad
Type   Mouse 
Bus   0x11
Vendor   2
Product   0x7
Version   0x1b1
Connected to   isa0060/serio1/input0

---

### Post by briguy47 on 2009-06-14
Thanks for the info.  I was looking up the Synaptics driver that's included with Jaunty and it mentions Multi-Finger taps:
>  * Multifinger taps: two finger for middle button and three finger for right
   button events. (Needs hardware support. Not all models implement this
   feature.)

I don't know if the version that shipped with Intrepid had that feature, but if I were a betting man, I'd put my money down that that feature is messing with the behavior.  Unfortunately, I don't know of a way to turn it off.  But I'll keep an eye out. :)

---

### Post by afinger on 2009-06-15
That makes sense. Thanks for taking time to help mate.

---

### Post by briguy47 on 2009-06-15
My pleasure!  :D

---

### Post by RD1 on 2009-06-15
> I recently updated to Jaunty, and it seems really nice.

One thing i noticed, however, is that the mouse pad functionality has changed since previous versions of Ubuntu. You can no longer quickly 'jump' over the screen -- this could previously be done by pressing a point on the mouse pad with one finger while at the same time another finger press down another point in the mouse pad. Then releasing the first finger quickly moves the pointer to the new point determined by the second finger. This no longer works in Jaunty, the pad is only sensitive to one finger at a time.

Am I the only one with this problem? Is this just some option which you can change? Or why has this function just been removed? I did not find anything under Preferences/Mouse.

Glad for suggestions.


OMG!! You mean, that was a feature?!?!? I always thought it was a bug and I was so pleased when the behaviour stopped! :D LOL

---

