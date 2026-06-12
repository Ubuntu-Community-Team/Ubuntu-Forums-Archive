---
title: "Speakers keep playing when headphones plugged in"
date: 2007-11-28
forum: Hardware &amp; Laptops
---

### Post by STRESSY on 2007-11-28
Hi, before this topic i read the others but can't find the solution

here we go...
i have a Compal ifl90 with a realtek 268 HDA soundcard..
When i plug my headphones the speakers keep playing and i listen both ways...
I went to alsa-mixer but theres no Headphone volume only Master and PCM..
After install the OS haven't sound after that i inserted in alsa-base model=acer and then it worked the sound. I already tried model=laptop update alsa drivers but nothing
if i change model=something different from acer e don't have sound anywhere

---

### Post by mouseboyx on 2007-11-28
goto the sound recorder then goto File > open volume control

if  there is a tab that says switches then goto it and headphone switch should be there.

---

### Post by askander on 2007-11-29
I also have the same problem, I did what recommended but nothing, as a matter of fact, in the switches tab, I don't have any Headphones option, just "line in", "IEC958", and "intmic"

I really would like a solution for this... anyone?

---

### Post by chadliness on 2007-11-29
I had this issue under Feisty (hp dv2000 laptop, NVIDIA audio) and it was fixed when I upgraded to Gutsy.  I remember reading a post on the forum that said it was something to do with the version of ALSA and Gutsy comes with a newer version.

---

### Post by STRESSY on 2007-11-29
> **mouseboyx said:**
> goto the sound recorder then goto File > open volume control

if  there is a tab that says switches then goto it and headphone switch should be there.

i already done it but i don't have headphones option..
i tried a lot of stuff..
but still don't working..

when i put in alsa-base model=laptop ou model=auto i have headphones options but the speakers don't work and headphones neither..

could someone help me?:(

---

### Post by STRESSY on 2007-11-29
any ideia guys?

---

### Post by Espionage724 on 2007-11-29
I also have this problem but only under Gusty. I never had this problem on edgy.

---

