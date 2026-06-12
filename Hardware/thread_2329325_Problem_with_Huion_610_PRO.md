---
title: "Problem with Huion 610 PRO"
date: 2016-06-30
forum: Hardware
---

### Post by mitherdil on 2016-06-30
It's kind of embarrassing... my graphic tablet seems to be working just fine, but like a mouse, not like a graphic tablet. 

In Inkscape, I can draw free hand lines smoothly, could set the pressure axis of the device in the calligraphic mode. However, in GIMP, I can only drag and drop or click on the stuff... no line are draw with the tablet, just with mouse.

xinput shows 
```
&#9116;   &#8627; HUION PenTablet                             id=13    [slave  pointer  (2)]
&#9116;   &#8627; HUION PenTablet                             id=14    [slave  pointer  (2)]
&#9116;   &#8627; HUION PenTablet                             id=15    [slave  pointer  (2)]
```

I'm using Ubuntu 14.04 with 3.19.0-56-generic kernel and GIMP 2.8.10. 

Any clues?

---

### Post by pete0512 on 2016-08-12
Hi slight problem since the last update (14.04) my tablet that was working fine before doesn't work now, the light on the tablet comes on but the  stylus doesn't move the curser any ideas or should I wait umtil I upgrade to 16.01)?

---

### Post by mörgæs on 2016-08-12
I would run 16.04.1 in a live boot and try the tablet here before making a decision.

---

### Post by pete0512 on 2016-08-12
Hmm after a bit more checking I find it still works with the 3.19.0 kernel but not the new 4.4.0 and re-installing does not appear to help, it does not bode well for the 16.04 version

---

### Post by mörgæs on 2016-08-12
I am not sure I understand your post. Did you try a reinstall of 16.04 which includes kernel 4.4?

---

### Post by pete0512 on 2016-08-19
Now running 16.04, new install, I did try the upgrade route from a usb install but it was not a success so a clean install was needed :) > But ok the Huion does work but no pressure sensitivity as before but the gimp install seems to have lost both wavelet decompose and wavelet denoise, rather a pity as I can't find a suitable substitute any else found this?

---

