---
title: "DVD burner doesn't work in Linux, works in Windows."
date: 2006-11-13
forum: Hardware &amp; Laptops
---

### Post by zerotek on 2006-11-13
As the title says my Lite-on dvdrw sohw - 1639s doesn't burn dvd's like it should. It reads cds, dvds just fine and burns cds well. I can burn in Windows (same media and everything) so it may be fixable, maybe I got a burner that isn't compatable, but that seems unlikely. I have checked for DMA and it is on. Any help would be awesome, thanks.

---

### Post by David Corrales on 2006-11-13
What do you mean with "like it should"? Permission problems? Doesn't burn even a bit? Only coasters? Which program are you using?

---

### Post by zerotek on 2006-11-13
Sorry in my haste I forgot to mention all the good stuff. I have used K3b and gnomebaker. It spins and says it is burning but then stops says it couldn't complete. Thats it, no actual errors. oh and the disc isn't a coaster, it doesn't even touch it. It happens on all my dvd media

---

### Post by David Corrales on 2006-11-13
Sounds like a permission problem. Try running the burner as root for a test.

---

### Post by zerotek on 2006-11-13
no luck, get the same error "There was an error writing to the disc:
Unhandled error, aborting"

---

### Post by David Corrales on 2006-11-13
Can you from the console to get more error output? Try other burning programs like brasero?

---

### Post by Decade on 2006-11-16
Are you burning the DVD at the right speed?

---

### Post by reison on 2006-11-16
Don't know if this will help you any, but I also have a Lite-On DVW writer--mine's a SOHW 1673S--installed in my Edgy box. Under WinXP and Dapper I had zero problems writing either DVD-R/Ws or DVD+R/Ws. Tonight was the first time I tried to write a DVD-R sice I upgraded to Edgy and I got very similar errors; I tried a DVD+RW and it worked fine. BTW, my DVD-Rs are 8x and my DVD+RWs are 4x.

After reading a few threads thanks to my buddy Google, I tried reducing the write speed to 4.1x instead of "maximum"--WORKED the first time, with the same disks it rejected set at "maximum".

Gotta be a bug...

---

