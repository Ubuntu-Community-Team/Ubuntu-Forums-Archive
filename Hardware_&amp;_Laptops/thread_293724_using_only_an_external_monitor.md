---
title: "using only an external monitor?"
date: 2006-11-05
forum: Hardware &amp; Laptops
---

### Post by OhCarolineNo on 2006-11-05
Hi, I've just installed 6.10 on a laptop (the 1280x800 resolution Dell 700m, intel 855gm integrated graphics) and I have an external monitor (the cheap and great 1600x1200 samsung) that I want to hook up to the vga port on the 700m. I've been able to get dual screen working with xinerama but the different resolutions seemed to prevent me from doing basic stuff like maximizing windows in their own monitor and/or dragging windows across desktops (even though i don't have two instances of x running). Is this a normal problem? If not, I'd really appreciate any advice folks might have on how to get a windows xp-comparable dual screen setup with two odd resolutions (it's one thing that MS did alright at, although not perfectly).

but regardless of whether it's me or xinerama or whatnot, my main question is this: can you use only an external monitor and not the laptop screen? I've attached my hand-edited xorg.conf (it's kinda messy, I haven't much experience editing these things). when i boot with the serverflag for multihead layout, I sure enough get a display on my external monitor and not my laptop (yay!) but the display says that x couldn't start up because no monitors were found, and I just get the commandline prompt. Is something missing from my xorg? do I have to edit something in gdm too? halp plz! thanks so much everyone

---

### Post by tatare99 on 2006-11-11
I also have a Dell 700m and I have exactly the same problem...

I bought an external LCD monitor and I'd like to have a 1280x1024 resolution on it (and nothing on my laptop)

Does anyone have an idea?

Thanks in advance!

---

### Post by OhCarolineNo on 2006-11-11
Whoa, i thought my thread had gotten buried. Reassuring to know i'm not alone in my woes. I still haven't found a solution myself. Hence my calling out: if anyone's at least got recommendations on where to search for info even, i'd be really appreciative. Google usually hooks me up after a few hours to days of persistence, and it's just let me down this time. No xorg pages seem to even deal with this issue. If anyone can guide me, i'll come back and post a solution if I figure it out.

(thanks again to anyone who took the time to read through my blahblahblah)

---

### Post by insub2 on 2006-11-12
i have a hp nx6110 and to switch toggle between laptop only, both, external only, i push Fn+F4.  does you model have anything like this?  if you don't have this feature, *i* can't help you.  someone somewhere said something about checking if the feature is allowed in your BIOS.

please note, i don't have xinerama running so i am not sure if that effects anything.

i'll see if there is anything i can do with xorg.conf to get resolution to be set up different and get back to you.

---

### Post by tatare99 on 2006-11-12
Hi,

I finally managed to get my external monitor working ! :-) I'm happy !
I have a Dell 700m and an external L1919S.
Here is what I do:
when GRUB shows up, I press Fn+F8, then the output is redirected to my external monitor. The important thing is press Fn+F8 when GRUB shows up.

Then, I just have to change the resolution of the screen by adding in the modes: "1280x1024"
i.e.
Modes		"1280x1024" "1280x800" "1024x768"
And then, it just works !
I have the output on my external LCD monitor (with a 1280x1024 resolution) and nothing on the laptop... exactly what I wanted :-)
And when I restart my laptop without pressing Fn+F8 when GRUB shows up, the display is as usual on my laptop at 1280x800... it's great !

---

