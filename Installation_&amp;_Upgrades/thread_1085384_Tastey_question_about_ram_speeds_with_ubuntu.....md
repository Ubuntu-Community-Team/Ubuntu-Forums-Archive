---
title: "Tastey question about ram speeds with ubuntu...."
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by Immolatus on 2009-03-03
Heres a head scratcher for you. I just upgraded my linux box to a quad core phenom w/4 gigs ddr2 1066. the odd thing is that ubuntu doesn't seem to like ram speed above 800mhz. Yes my mobo supports it and yes 1 dim per channel. It runs great at 667 and 800, but as soon as I crank it up to 1066, ubuntu hangs at load screen(in particular the part where it is searching for a resume image) any thoughts???:popcorn:

---

### Post by jerrrys on 2009-03-03
very interesting..does this throw any light on the subject?

[http://www.tomshardware.com/forum/256640-30-memory-speed-1066](http://www.tomshardware.com/forum/256640-30-memory-speed-1066)

---

### Post by Immolatus on 2009-03-03
Well...a little. The phenom supports 64 bit and I know you can use more memory with that, so I just installed the 64 bit version of 8.10 and another funny thing happened. kernel panic. Didn't see that one coming. I just don't know at this point, If I can't figure out the 1066 thing then I'll just throw my two old 1g sticks back in and run 6 gigs @ 800mhz because 64 bit uber will run it.

Post Script:  an interesting note. 32 bit registered in the system monitor only 3.2 of 4 gigs, while 64 bit shows 3.9. And I here tell (at least w/wintrash) that 64 bit supports some astronomical ram amounts like 32 gigs. Not that I'm about to go out and buy that much ram and try even though my MOBO theoretically supports 16 gigs. :popcorn:

---

### Post by jerrrys on 2009-03-04
I just upgraded my linux box to a quad core phenom

what mobo you running?

---

### Post by Immolatus on 2009-03-04
Asus M4A78 PRO

---

### Post by neppakyo on 2009-03-04
heh. try using the server kernel.

---

### Post by jerrrys on 2009-03-04
4 x DIMM, Max. 16 GB, DDR2 1066*/800/667 ECC,Non-ECC,Un-buffered Memory
Dual Channel memory architecture
*Due to AMD CPU limitation, DDR2 1066 is supported by AM2+/AM3 CPU for one DIMM per channel only. Refer to [www.asus.com](www.asus.com) for the memory QVL (Qualified Vendors Lists). 

you probally investigate this, im just trying to get up to speed..

heh. try using the server kernel.

kernel..hummmm

---

### Post by Immolatus on 2009-03-04
I'll look in to both. I just tried putting in my old sticks as they are 1066 as well just 1 gig each. Right now I'm running 64 bit with all six gigs installed showing 5.8 gigs, running like a song; although @ 800mhz.

---

