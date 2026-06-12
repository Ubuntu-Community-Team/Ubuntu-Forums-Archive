---
title: "LG GH22NP20-R doesn't boot from CD/DVD"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by jedi22 on 2009-04-19
I bought a LG GH22NP20-R super cd/dvd writer but my computer won't boot from a CD or a DVD using it!  Can anyone help me?

---

### Post by lytithwyn on 2009-08-14
I have the same problem with the same drive.  I updated the firmware, but still no joy.  I found that there is ONE computer in my house that, if I install this drive, it will boot from an optical disc.

I think it's just a junky drive.  I only gave $20 for mine.  You?

---

### Post by ubuntologist on 2010-06-11
Hi there,

I *had* exactly the same problem where the LG drive would work fine once the OS had loaded but wouldn't boot from CD.

Tried a number of suggestions and found the one that worked was to assign "CDROM" for ALL boot devices in the BIOS. 
E.g.
1st Boot Device: CDROM
2nd Boot Device: CDROM
3rd Boot Device: CDROM

Oddly enough, this works!

Another suggestion that seems to be along the same lines was to Disable the Quick Boot option in the BIOS.

Hope that helps.

---

### Post by lytithwyn on 2010-06-14
Worked for me!  Thanks ubuntologist!

On my computer it actually fails to boot to the cd, but gives the option to press any key to retry.  I press a key, and it boots like a champ.

I'd previously achieved the same effect by unplugging my hard drive, but it's hard to install an OS that way.  I don't know why I didn't think of this.

---

