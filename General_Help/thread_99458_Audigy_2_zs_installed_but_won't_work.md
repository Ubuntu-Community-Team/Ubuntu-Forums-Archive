---
title: "Audigy 2 zs installed but won't work"
date: 2005-12-05
forum: General Help
---

### Post by Fatstink on 2005-12-05
I have an Audigy 2 zs sound card and it's installed but when i run alsamixer it tells me I am using C-Media CMI9880.  Any ideas why?

---

### Post by GameManK on 2005-12-05
because you have integrated sound, that's your hw:0 sound card, and the audigy2 is hw:1
run
alsamixer -c1

---

### Post by Fatstink on 2005-12-05
did that however......it doesn't work still........the audio off the integrated doesn't work either.  Any ideas?

---

### Post by GameManK on 2005-12-05
did you turn up the volume in alsamixer?
what are you using to see if it works?

---

### Post by Fatstink on 2005-12-05
I put the volume all the way up and have the speakers on........I'm testing by running it out to my speakers.

Yes i know my speakers work....windows told me so......

:D

if you have some better ideas I'm all for them because i new to linux and really would like to use it in everyday use. :KS

---

### Post by GameManK on 2005-12-06
I mean, what program in linux are you using to see if your sound works?

Also, if you have analog speakers (most likely i think) make sure the digital out is disabled (muted) in alsamixer

---

