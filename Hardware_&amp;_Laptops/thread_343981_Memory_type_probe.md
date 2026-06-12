---
title: "Memory type probe?"
date: 2007-01-22
forum: Hardware &amp; Laptops
---

### Post by aweller on 2007-01-22
Dear all,

I would like to purchase 1 Gb of new memory for my machine. Is there a way to 'probe' what type of memory is currently installed (i.e. DDR, DDR2, etc) so that I buy the right type?

Additionally, having opened my machine, it appears that there's 2x512 Mb in it at present. Is it possible to install a 1x1 Gb module instead of 2x512 Mb modules?

Thanks, Andy

---

### Post by aweller on 2007-01-23
Any ideas anyone?

---

### Post by RandomJoe on 2007-01-23
You can try running 'sudo lshw' to get a detailed listing of all the hardware in your system - memory will be in there as well.  Some systems don't give much info, though.

If you know the exact model number for your system (if a Dell, GW, etc) or motherboard (if it was built up) my preferred way is to go to one of the memory manufacturers' websites and use their memory selectors.  Just plug in the info and they will tell you what sort of memory configurations your board can handle, and what part numbers work in it.  Then you can shop prices at whatever place you prefer.

[http://www.kingston.com](http://www.kingston.com)
[http://www.crucial.com](http://www.crucial.com)
Those are two I've used a lot, but there are plenty more around.

As long as the motherboard supports it, there shouldn't be a problem using a 1GB stick, although there are some configurations that require paired memory so you would have to have _two_ 1GB sticks.  There are also some configs (like mine) that don't require the pairs, but run better with them (dual channel).

---

