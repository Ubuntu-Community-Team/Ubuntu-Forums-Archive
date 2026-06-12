---
title: "Dell C610 Notebook Resolution. Can't Change!"
date: 2007-04-18
forum: Hardware &amp; Laptops
---

### Post by adampyre on 2007-04-18
Hi,

I am brand new to Linux. Played with Knoppix, played with Fedora Core. I played with red hat about 10 years ago or so and destroyed a dual boot machine. Coming back because I installed Vista and was saddened and ashamed. Abandoning MS and setting foot into the world of Linux. It is strange feeling this new to a computer again, like I'm 13 all over again or something.

Anyway!

I have an old Dell C610 I have installed Ubuntu on and I surprisingly got everything working with only a few days research (wireless, sound card worked by default, everthing)

except, I cannot get resolution any higher than 1024 x 768 no matter how hard I tried. I know there is an ATI card in here, not sure of the specifics, if needed. No matter what I do to the xorg.conf file as far as resolution settings, nothing changes at all. Sometimes it makes the GUI take longer to load, I am assuming that is the system freaking out on my settings for a second, jumping to the cards bios and flipping me off?

anway, any help would be appreciated. I'll keep an eye here if anyone wants to help an MS defector get his Linux learning on.

Thanks!

Adam

---

### Post by joft on 2007-04-18
Do you have a special version of Dell C610? My one and others I had to do with have a display which just can't do more than 1024x768. I'd say that's the highest resolution ...

---

### Post by adampyre on 2007-04-18
Hmm. It is an older laptop w a Pentium 3. I wouldn't be surprised. The previous owner, my father always ran it at a low resolution. I just assumed it's because he was old... ;) 

I know that you can get video cards/monitors that max out at a certain resolution to go higher, but it doesn't display the whole desktop on the screen at one time.... I wonder if this is what I would achieve if I attempted to pursue this any further. Thanks for the input, joft.

---

### Post by joft on 2007-04-19
Hmmm, so you could use a specified virtual screen resultion in your xorg.conf file. There you can say, that you want a higher resoltion and then your display shows a 1024x768 "window" of a bigger virtual screen. This "window" can be moved by moving the mouse pointer to the edges.
See
```
man xorg.conf
```
for more info. Look for "subsection display", item "virtual".

---

### Post by adampyre on 2007-04-19
> **joft said:**
> Hmmm, so you could use a specified virtual screen resultion in your xorg.conf file. There you can say, that you want a higher resoltion and then your display shows a 1024x768 "window" of a bigger virtual screen. This "window" can be moved by moving the mouse pointer to the edges.
See
```
man xorg.conf
```
for more info. Look for "subsection display", item "virtual".

Hey joft, yeah, that's exactly what I was thinking about. Eh, I don't think I would like that. I've decided to live with the 1024 res for now. Thanks for your assistance!

:)

---

### Post by bazdrumma on 2007-05-21
Hi There,
Being new to linux myself, I did have my dell c610 running at 1400 times 1050. But as a tinkerer i installed edgy and low and behold now I'm back to 1024. It seems a lot more stable at this resolution. Before it would quite often load nautilus and then crash back to the login. I think th resolution may have had something to do with it. Anyway a higher resolution is possible but how ?

---

