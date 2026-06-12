---
title: "how do i clone my lappy to my 60 inch tv"
date: 2008-07-03
forum: Hardware
---

### Post by darkmdbeener on 2008-07-03
ive been trying to figure this out for the longest time. my xorg.config for my divice is as followed
```
Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection
```

thank you

EDIT
also if i do the detict devices i get a very blurry screen and my resolution changes.

---

### Post by darkmdbeener on 2008-07-03
anyone?

---

### Post by darkmdbeener on 2008-07-03
oh come on some one has to be able to help me

---

### Post by darkmdbeener on 2008-07-03
please....

---

### Post by darkmdbeener on 2008-07-04
help??

---

### Post by starcannon on 2008-07-04
use the cable's needed, generally a dvi or dsub cable to the t.v. is easiest, then at post or grub press the FN+specific-key-4-external-monitor, then toggle through either "Only external" "Only Laptop LCD" and "Both external and Laptop LCD" watch the t.v. and laptop screen to see the various effects.

Once you've decided on your combination, then once to the desktop go to System-->Screen Resolution and set the appropriate resolutions. There may be a way to do this from your desktop, but at the moment the only way I know to do these things is to decide the monitor at post or grub.

GL

---

### Post by JafaarNhh on 2008-07-04
haha im runing my computer on a lcd right now
:lolflag:

---

### Post by starcannon on 2008-07-04
> **JafaarNhh said:**
> haha im runing my computer on a lcd right now
:lolflag:

How did you do it?

---

### Post by darkmdbeener on 2008-07-04
mine always gets blurry on the screen and never gets past 1280*720
also shrinks my lappys screan

---

### Post by darkmdbeener on 2008-07-05
alright i tested it the same thing happends i get a huge blurry image that wont go to the right resolution

---

### Post by starcannon on 2008-07-05
I'm at a loss, I have that gpu chipset in my Asus Eee and it just works on my 42inch Plasma Widescreen. sorry I really am of no more help. perhaps someone with more experience can help, hang in there, and give your post an occasional bump and eventually someone who knows will come along.

---

### Post by sayakb on 2008-07-05
Im not sure about this. Even if you find a way to get this working, your i915 onboard graphics may/may not support such a big image on the screen. The maximum image size for i945 is 2048x1024 (or something). I may be wrong though..

---

### Post by jackhe22 on 2008-07-06
Simple, do what you did to get the blurry screen and go to screen resolution. Set it to 1024x768, and youre done!

---

### Post by darkmdbeener on 2008-07-08
nope that doesnt work either.

the thing is the vga works fine but has a black boreder around it (which i can handle for now) but when useing tv out (s-video) it can only stay blurry a friend was telling me it had to do with a xorg file written wrong. but i dont know . no mater if i change the resolution its always blurry

EDIT 
also is i945 the same as Intel?

---

### Post by darkmdbeener on 2008-07-09
bump for help

---

