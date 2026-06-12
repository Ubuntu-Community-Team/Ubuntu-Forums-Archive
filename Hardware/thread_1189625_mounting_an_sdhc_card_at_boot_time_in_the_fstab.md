---
title: "mounting an sdhc card at boot time in the fstab"
date: 2009-06-16
forum: Hardware
---

### Post by undecidable on 2009-06-16
I have standard kubuntu 9.04 installed on an eee1000 with two ssd cards (8+32gb).  Works just beautifully, looks fantastic. 
   
I am trying to boot with a card in the sdhc slot as a 3rd drive to hold filesystem data. 

The boot-time filesystem check often fails with a "superblock could not be read" error on the sdhc card, and offers me a maintenance shell or control-D prompt to continue.  I elect to continue and it boots normally without the sdhc card mounted, and I can mount it manually later.

I suspect it is a timing issue with the sdhc card not being ready quickly enough because:
.  when I set the card in the fstab to automount, it fails ~3/5 times 
.  if I set the card to noauto, the failure rate is reduced to ~1/3 times.
.  the failure rate seems to be further reduced if I use noauto plus set the final fstab parameter <pass> to 3 though my sample is not big enough to quote a number.
.  however I set <pass> to 3 but remove the noauto, the failure rate goes up again.

To get it to boot consistently without failing on the sdhc card, I need to set the <pass> parameter to 0 which then does not do a boot time check of the sdhc card.  It then mounts normally and after boot can be used normally.  

Of course I would prefer not to bypass the boot-time check - does anyone have any experience of this or have any ideas?

---

