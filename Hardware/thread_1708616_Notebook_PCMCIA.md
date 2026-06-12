---
title: "Notebook PCMCIA"
date: 2011-03-16
forum: Hardware
---

### Post by sonicmike on 2011-03-16
I have a soundblaster audigy2 zs card for my laptop. Any ideas how I can get it to work thru ubuntu 10.4?

---

### Post by ptptaylor on 2011-03-17
Sounds familiar that card. I think I have tried it in mine and it worked without any modifications. My card was half broken as the input no longer worked, but it outputted fine.
I don't think you need to even install any drivers, although there are no applications for changing the settings.

---

### Post by sonicmike on 2011-03-17
I plugged it in but got no sound from the headphone output.  Its always worked fine before.  I just wasnt sure if I need special drivers or need to activate the pcmcia slot somehow.  How i look at the hardware attached to my laptop like device manager?

---

### Post by IcarusR on 2011-03-17
Install 'gnome-device-manager' package, it's in repositories.

You could check log files to see if system has recognised it.

Or remove it wait a minute then reinsert it & in a terminal type

```
dmesg | tail -n15
```

Check the output to see what it says about the card.

---

### Post by sonicmike on 2011-03-18
@icurus
 
Thanks I appreciate the help.
 
It did recognize it, I just had to change from the default output in the sound preferance.
 
I will download that package and try the cmd line too.
 
Still getting use to all the coolness that is ubuntu
 
:D

---

