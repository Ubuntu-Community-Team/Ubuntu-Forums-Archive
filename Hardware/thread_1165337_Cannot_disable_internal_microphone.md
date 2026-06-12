---
title: "Cannot disable internal microphone"
date: 2009-05-20
forum: Hardware
---

### Post by lazypeterson on 2009-05-20
I cannot figure out how to turn off my laptop mic. I dual boot with Windows Vista, and shutting it off in Windows is no problem, but I cannot for the life of me get it turned off in Ubuntu 9.04. I've had this problem since 8.10, so it's not a result of the upgrade. I've done a lot of searching and have found similar cases with no solutions. 

Any help would be greatly appreciated! 

(I've already tried everything as far as using volume control).

Thanks

---

### Post by pebo on 2009-05-20
In a terminal, type ```
alsamixer
```
Tab across till you reach "mic". Toggle mute using "m".
hth

---

### Post by lazypeterson on 2009-05-20
I don't actually have a strictly microphone part of alsamixer, I have:

Master
Headphones
PCM
Front
Front Mic Boost
Mic Boost
Beep

I've muted Front, Front Mic Boost, and Mic Boost, but it didn't do anything. Only if I mute Master will the internal mic turn off, but of course that shuts off the volume for everything else too. 

Thanks for your reply, though. This is something I haven't tried yet.

---

### Post by lazypeterson on 2009-05-24
bump

---

### Post by lazypeterson on 2009-05-29
bizzump

---

### Post by lazypeterson on 2009-06-08
Nothing?

---

### Post by twiggyness2000 on 2009-06-15
Did you try changing some of the stuff in the [capture] menu?

```
alsamixer -V capture
```

---

### Post by twiggyness2000 on 2009-06-15
Or, run
```
gnome-volume-control
```
...click on preferences and check the [input source] box, then switch it to something other than MIC.  It's not the 'right' way to fix it, but it could help in a pinch.

---

