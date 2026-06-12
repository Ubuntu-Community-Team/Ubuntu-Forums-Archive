---
title: "x64 bit ubuntu boots strangely on Compaq f700"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by metroidnemesis13 on 2009-01-04
Hi guys.  I've been a ubuntu user for a while and ran it on a Compaq v2000 but I decided to upgrade, so I put Ubuntu 8.10 64 bit on my new Compaq f700.  It has an interesting problem.  When I boot, it takes me to the orange and black logo screen.  The bar gets maybe a fourth of the way to the right before I have to hold a key.  Then it continues as if nothing happened.  As soon as I release the key it freezes.  If I press it again it continues... etc.  I think it has the same problem with shutdown as well.  The install works great except for that glitch.  What can I do?

---

### Post by jbrown96 on 2009-01-04
> **metroidnemesis13 said:**
> Hi guys.  I've been a ubuntu user for a while and ran it on a Compaq v2000 but I decided to upgrade, so I put Ubuntu 8.10 64 bit on my new Compaq f700.  It has an interesting problem.  When I boot, it takes me to the orange and black logo screen.  The bar gets maybe a fourth of the way to the right before I have to hold a key.  Then it continues as if nothing happened.  As soon as I release the key it freezes.  If I press it again it continues... etc.  I think it has the same problem with shutdown as well.  The install works great except for that glitch.  What can I do?

Try changing from the graphical boot to see where it freezes. When the Grub menu loads, press Esc if you can't see the individual entries. highlight the top entry and press "e", then highlight the second line and press "e" again. Find the part that says "splash" and change it to "nosplash". then press enter and "b". Now you can see all the messages as the system boots.

---

### Post by metroidnemesis13 on 2009-01-04
It just says Aperture beyond 4GB.  Ignoring.  and then it says Loading, please wait...

and then I hit the spacebar, and it said 

"19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/sda6) = dev(8,6)
kinit: trying to resume from /dev/sda6
kinit: No resume image, doing normal boot..."

and then it pauses, until I hold another key

and then it says 

"* Reading files needed to boot... [OK]
* Setting preliminary keymap..."

and then it stops until I hold a key and it goes through more crap.

The only thing I notice out of the ordinary is an error:

"19.681670 wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)

 and then it continues (i think it's talking about my wifi internal card, which hasnt worked from the start)

and then it continues when i hold a key with nothing out of the ordinary, but if i dont it does nothing

---

### Post by metroidnemesis13 on 2009-01-04
Could it be the internal wifi is messing it up?

---

### Post by metroidnemesis13 on 2009-01-05
I tried reinstalling it and it didn't make a difference.

---

### Post by jbrown96 on 2009-01-05
If the wifi is a pci card, could you try removing it? If not, maybe disable it in BIOS and see what happens. 

Do you know the specific model number and manufacturer of the card?

---

### Post by metroidnemesis13 on 2009-01-06
It was already disabled.  I enabled it, but it did nothing.  It's an internal Atheros 5007 b/g Wifi adapter

---

### Post by jbrown96 on 2009-01-06
Have you tried 32-bit?

---

