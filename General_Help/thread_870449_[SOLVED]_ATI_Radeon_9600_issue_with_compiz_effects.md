---
title: "[SOLVED] ATI Radeon 9600 issue with compiz effects"
date: 2008-07-25
forum: General Help
---

### Post by aaronp on 2008-07-25
Hi All,

Trying to enable desktop effects using an ATI Radeon 9600 and restricted ati fglrx drivers in Hardy.

I was using Gutsy until yesterday. Running Compiz-check led me to try the xgl driver because without xgl installed I get 'FAIL' on the first check and fifth check. But when enabling xgl I get constant hard locks with 'reset' button being the only option. I uninstalled the xgl drivers and things work fine again but no effects.

Anyway....
Funnily enough I upgraded to Hardy from Gutsy just yesterday and now running compiz-check (without using xgl drivers) yields all 'OK' results:

```


Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV350 AR [Radeon 9600]
 Driver in use:         fglrx
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


```

However, I feel there is still something wrong - I am now able to enable the desktop effects without the xgl driver but if I do I am getting some weird misrendered triangles in the top right corner of my screen randomly upon opening applications and the occasional hard lock when trying to switch between desktops or super-tab between apps. Are there still some settings that I am not getting right?

thanks
Aaron

---

### Post by aaronp on 2008-07-27
Disregard. Reading around I decided to try removing the proprietary fglrx drivers and using the open source ati driver instead. Have been toying with compiz-fusion effects all day with no crash so far (touching wood as i type....)

Anyone interested in doing the same thing:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

Thanks
Aaron

---

### Post by sputnikkk on 2008-07-27
> (touching wood as i type....)

Hahaha - that just made me LOL!

Totally OT and non PC humor ....

Reminded me of grampa ... always saying "Son, leave it alone - it'll grow" to all the grandsons.

---

### Post by aaronp on 2008-07-28
I think you might have read something into my post that wasn't there! lol
'touching wood' (real wood) for good luck - as in the superstitious saying. Not touching 'my own personal wood' if that's what you were implying...lol

Anyway, glad it could make you LOL. Since posting that I've had 4 hard locks. After the first 2 I disabled compiz and got 2 more so am completely stumped now.
Will post this in a new thread though because it doesn't seem compiz related.

Aaron

---

