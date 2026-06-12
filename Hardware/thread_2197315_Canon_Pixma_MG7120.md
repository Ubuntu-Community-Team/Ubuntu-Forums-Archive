---
title: "Canon Pixma MG7120"
date: 2014-01-03
forum: Hardware
---

### Post by PratterFak on 2014-01-03
Anyone able to get this printer working with Ubuntu?

This is a fairly new printer. I'm unable to get it to work using Ubuntu 12.04 while directly connected via USB, direct network connection, or network connection via USB to a printer server. I tried using some of the other Pixma MG drivers (even a generic driver) hoping it would, but no luck so far.

Thanks!

---

### Post by aikishugyo on 2014-01-03
When I added support for this printer in gutenprint, it turned out that the MG7100 series can use the same printer driver as the MG6500 series.
I don't know if Canon's driver has a way to edit the driver specs to change any references to the MG6500 to MG7100, but perhaps you can try installing the MG6500 Canon driver.
If you are feeling advernturesome, you could compile the CVS gutenprint code and test that too :-)

---

### Post by LillyDragon on 2014-01-03
Have you tried Michael Gruz's PPA? Official drivers worked for me under Ubuntu 10.04, but not Precise and above. Seeing as your printer is a Pixma model like mine, (Canon Pixma 280) maybe it is supported here?

[https://launchpad.net/~michael-gruz/+archive/canon-trunk/+packages](https://launchpad.net/~michael-gruz/+archive/canon-trunk/+packages)

If not that, then it couldn't hurt to see if driver sources are available for compiling.

---

### Post by aikishugyo on 2014-01-04
Looks like the 3.90 driver does not include the MG6500 or MG7100 series yet.

---

