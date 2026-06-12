---
title: "Compaq R3000 Laptop Screen weirdness"
date: 2005-06-08
forum: Hardware &amp; Laptops
---

### Post by rdwtux on 2005-06-08
Hi all, 

I have a compaq r3000 laptop that is generally supported by Ubuntu very well.  I have one issue that I was hoping someone could help with. 

When I close the lid of the laptop and then re-open it, it seems to switch to tty8 or something - blank screen with cursor.. so i have to switch manually back to tty7, unlock the screen saver... then within 10 seconds it switches BACK to tty8 (or blank screen) and I have to switch back again to tty7. 

After this everything is fine and I'm ready to go, however it is fairly annoying. 

I have Hoary on my work laptop (ibm t30) and do not at all have the same issue.  It doesn't seem to be related to the NVIDIA drivers, as it doesn't matter whether I run the "nv" opensource driver or the "nvidia" proprietary driver.

Thanks

---

### Post by jrhodes on 2005-06-08
there's a lid close sensor on that laptop. Odds are, acpid is being 'helpful' and turning off your screen when it detects the lid as being closed, and it just takes a little encouragement to make it turn back on again.

Next time it does that, try hitting the spacebar repeatedly rather than pressing alt+f7.

If that works, then you can go into the laptop's bios setup (F10 at the compaq logo) and tell it to ignore the lid sensor.

---

### Post by Whitewolfe on 2005-06-12
Call me crazy, but I don't find an option in the f10 bios setup to turn off the lid sensor.  Using R3000.  Maybe there's a way to do it from configuration?

-WW

---

