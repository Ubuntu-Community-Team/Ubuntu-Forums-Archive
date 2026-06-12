---
title: "Install hanging on HP a450n"
date: 2008-07-30
forum: General Help
---

### Post by cgaudio on 2008-07-30
Greetings Wise Ones,

I'm just starting, so If I'm in the wrong place, somebody please point me. 

Installing from the Gutsy CD, I get the logo and the progress bar, but after a couple minutes the graphics go crazy and a couple minutes after that, I get rolling yellow screen. 

This is my first experience with Linux so, when answering, assume that I know NOTHING. (I got sick of Windows crashes.)

Thanks!
-Chuck

---

### Post by spiderbatdad on 2008-07-30
how much ram? ubuntu requires around 512 minimum for good experience. Xubuntu is for lower ram models. HP often boots with noapic nolapic options.

Boot options:[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I recommend deleting --quiet splash and replacing that with the boot options of choice...not adding them after --quiet splash.

---

### Post by cgaudio on 2008-07-30
The HP has a gig of RAM.

How do I delete --quiet splash from the CD before install?

I tolja, I'm a rank beginner: noapic, nolapic, whatthepic?
-chuck

---

### Post by cgaudio on 2008-08-11
Hey, no kidding. 
-c

---

### Post by cgaudio on 2008-08-20
Hey, guys, I looked at the boot options and they might as well be in Greek! I tried appending noapci, but it came right back to the menu. I have no idea what an APCI system is anyway. I can give you lots more examples about how ignorant I am about Ubuntu, but I thought I covered it pretty well on my first posts.

If somebody can help me with this install, I'd appreciate it! 
-Chuck

---

### Post by spiderbatdad on 2008-08-20
Ok. have you been able to boot the live cd with or without specific boot options? Have you installed Ubuntu on your computer?

---

### Post by cgaudio on 2008-08-25
> **spiderbatdad said:**
> Ok. have you been able to boot the live cd with or without specific boot options? Have you installed Ubuntu on your computer?


Please see my first post. Am I screwed?
Thanks!
-Chuck

---

### Post by cgaudio on 2008-09-01
You experts are awfully quiet. Hard to believe that nobody's encountered this problem. Or am I too new and stupid to bother with.

The boot problems page leaves a lot to be desired as far as this newbie is concerned. Tells you you can add options, but says neither what they do nor how to add them, syntax, etc.

Here's some more things I've tried that didn't work: Add "grub" to quiet splash--, delete quiet splash, delete quiet splash and add grub there, delete intrid.gz quiet splash, delete intrid.gz quiet splash and add grub, delete casper/..., delete casper/... and add grub. 

I'm dyin' here!
-chuck

---

### Post by cgaudio on 2008-09-14
Folks, my first post was over a month ago, and I still haven't got Ubuntu installed. As you can see, most of the posts are me, begging. 

Maybe someone could suggest another forum, or tutorial, and point me??
Thanks!
-Chuck

---

