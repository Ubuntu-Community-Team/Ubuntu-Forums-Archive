---
title: "module summa not found"
date: 2007-01-26
forum: Hardware &amp; Laptops
---

### Post by el_itur on 2007-01-26
I'm writing this since [this](http://www.ubuntuforums.org/showthread.php?t=52978&highlight=summa) is an old topic.

I'm trying to make my graphics tablet work on edgy and modprobe keeps saying > FATAL: Module summa not found.

So does the X.org.log.

Have this module been removed from the kernel or is it on LRM?

Thanks in advance

---

### Post by el_itur on 2007-01-29
so far I've done this:
install LRM, no luck, this module isn't there.
apt-get install xsever-xorg-input-summa. No luck, modprobe didn't catch it. 

I will restart to see what happens

---

### Post by el_itur on 2007-01-29
Well xserver-xorg-input-summa did the trick, now my tablet is recognized by X. Still I have no motion. I will try to see if I can configure the X properly to make it work

---

### Post by el_itur on 2007-01-29
this is the output for xorg.0.log
```
(==) SummaSketch III: tablet size is -32.-76in. x -32.-76in., -16384x-16384 lines of resolution
(==) SummaSketch III: using tablet area -20480 by -16384, at res 500 lpi
(==) SummaSketch III: Using increment value of 1
```

Wich is incredibly wird since all the values are negative. I should say ```

(==) SummaSketch II+: tablet size is 12.00in. x 12.00in., 6000x6000 lines of resolution
(==) SummaSketch II+: using tablet area 6000 by 6000, at res 500 lpi
(==) SummaSketch II+: Using increment value of 4
```

I'm not an expert of xorg configuration. So I'm working almost blind. Any help is welcome

---

### Post by laharrin on 2008-04-24
Wondering if you had any advice for getting a SummaSketch II working?

---

