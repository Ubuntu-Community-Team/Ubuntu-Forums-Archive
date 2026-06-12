---
title: "Terratec 5.1 Fun, with bass sound"
date: 2007-06-11
forum: Hardware &amp; Laptops
---

### Post by shazm on 2007-06-11
how can I set up real surround sound for my terratec 5.1. fun?
I tried all mixers, with 3D Control and all. Nothing worked, can anyone please help me?
Thanks!

---

### Post by shazm on 2007-06-14
can't be, answer! please!

---

### Post by cisoprogressivo on 2007-06-17
I have the same problem with a Terratec DMX 6Fire...
Nobody has a solution?

---

### Post by ezekiel0815 on 2007-06-25
Hi, I've also the terratec 5.1 fun.
You've to create .asoundrc with this content:

pcm.20to51 {
     type route
     slave.pcm surround51
     slave.channels 6
     ttable.0.0 1
     ttable.1.1 1
     ttable.0.2 1
     ttable.1.3 1
     ttable.0.4 0.5
     ttable.1.4 0.5
     ttable.0.5 0.5
     ttable.1.5 0.5
}

But this will only work with surround coded media, there is also a possibility to upmix normal stereo signals, but I just haven't got it yet
greetz

// [http://ubuntuforums.org/showthread.php?t=31829&highlight=terratec](http://ubuntuforums.org/showthread.php?t=31829&highlight=terratec) should help

---

