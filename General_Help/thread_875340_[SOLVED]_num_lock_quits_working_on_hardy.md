---
title: "[SOLVED] num lock quits working on hardy"
date: 2008-07-30
forum: General Help
---

### Post by trmentry on 2008-07-30
I have a laptop with an external keyboard hooked up to it.  For weeks I've had no issues.  Then today.. my num lock quits working.  The light comes on, but no numbers on screen when keys pressed on num pad.  I tried toggling it, but no help.

This happened before and the only thing I could to do restore was a reinstall.  I'm really not wanting to do that.

I'm really hoping someone has some ideas or at least of places to look to get data to get help.

Thanks

---

### Post by drs305 on 2008-07-30
Just curious: if you run 'xev' from terminal and hit the numlock key does it respond and return Keycode 77 ?

---

### Post by trmentry on 2008-07-30
> **drs305 said:**
> Just curious: if you run 'xev' from terminal and hit the numlock key does it respond and return Keycode 77 ?

Yup.  ```

KeyPress event, serial 31, synthetic NO, window 0x4e00001,
    root 0x13b, subw 0x0, time 8497459, (1150,-180), root:(1157,685),
    state 0x2010, keycode 77 (keysym 0xff7f, Num_Lock), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

```

---

### Post by drs305 on 2008-07-30
I know on my computer the numlock key can get disabled by wrong key combinations. Your keyboard recognizes you are typing the numlock key. Try CTRL-SHIFT-Numlock and see if that restores it.

---

### Post by trmentry on 2008-07-30
> **drs305 said:**
> I know on my computer the numlock key can get disabled by wrong key combinations. Your keyboard recognizes you are typing the numlock key. Try CTRL-SHIFT-Numlock and see if that restores it.

WhooHoo!  That did it.  Thanks.

---

### Post by xbyte1024 on 2009-02-25
> **drs305 said:**
> I know on my computer the numlock key can get disabled by wrong key combinations. Your keyboard recognizes you are typing the numlock key. Try CTRL-SHIFT-Numlock and see if that restores it.

You are my hero :guitar:

---

### Post by holdorph on 2010-12-09
Man, this has been bugging me for a couple of weeks, but by the time I'd get around to googling it, I always forgot about the problem.  Finally, I looked it up, and this solved it!  Thanks.

---

