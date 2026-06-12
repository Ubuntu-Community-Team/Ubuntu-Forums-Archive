---
title: "Windows key / super key / meta key"
date: 2009-01-10
forum: Hardware
---

### Post by fhsm on 2009-01-10
My laptop (thinkpad t43) didn't come with a windows key on the keyboard.  Under XP, IBM gave me a utility to map the right alt key to act like the windows key.  

How I can do the same thing in ubuntu?  My searching has left me without an answer at a level I can understand and a bit confused about nomenclature: what's the difference between a super key and a meta key?

---

### Post by fhsm on 2009-01-12
After a lot of googling I tried the following

put 'keysym Alt_R = Super_R' into ~/.Xmodmap and run

```
 xmodmap ~/.Xmodmap 
```

To check the setup use xev.  Which I did and get the following when pressing the right alt key:

```
 KeyPress event, serial 35, synthetic NO, window 0x2200001,
    root 0x65, subw 0x0, time 1298472, (286,-242), root:(897,395),
    state 0x0, keycode 108 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False 
```

Whereas my left alt key, amongst other differences, shows up as Alt_L, not Super_R.

Problem is my right alt is still working as an alt key not as a super key.  Suggestions?

---

### Post by robobot on 2009-02-01
Try replacing 'keysym Alt_R = Super_R' with 'keysym Alt_L = Super_L'. That should map your left Alt key to left Super.

---

### Post by fhsm on 2009-02-06
For anyone interested down the road the fix for this is in my case is ~/.Xmodmap: ```

! Make the right alt key say that it is a Super / Meta key
keycode 108 = Super_R Meta_R Super_R Meta_R Super_R Meta_R
! Add those codes to the correct modifiers 
add mod1 = Meta_R
add mod4 = Super_R
! remove them from the default mod lists
remove mod1 = Super_R
remove mod1 = Alt_R

```

worth noting if you try to apply this at the command line you'll get an error.  If however you let it auto apply on boot everything will work just fine.

---

### Post by jdb-JimBo on 2011-07-29
> **fhsm said:**
> After a lot of googling I tried the following

put 'keysym Alt_R = Super_R' into ~/.Xmodmap and run

```
 xmodmap ~/.Xmodmap 
```

To check the setup use xev.  Which I did and get the following when pressing the right alt key:

```
 KeyPress event, serial 35, synthetic NO, window 0x2200001,
    root 0x65, subw 0x0, time 1298472, (286,-242), root:(897,395),
    state 0x0, keycode 108 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False 
```

Whereas my left alt key, amongst other differences, shows up as Alt_L, not Super_R.

Problem is my right alt is still working as an alt key not as a super key.  Suggestions?
fhsm's post above worked Great!

I also have an IBM / Lenovo Thinkpad with NO Windows keys, this ~/.Xmodmap
entry did the trick, and Quick!  Thanks fhsm!!!  Unity should be a little easier now?

JimBo

---

