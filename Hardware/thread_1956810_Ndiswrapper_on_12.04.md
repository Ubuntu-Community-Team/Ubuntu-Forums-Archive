---
title: "Ndiswrapper on 12.04"
date: 2012-04-11
forum: Hardware
---

### Post by Galael on 2012-04-11
Hi

I would like to use ndiswrapper on 12.04, but it generates an error:

Ndiswrapper module not found

I know that ndiswrapper is installed and that the driver I use worked on 10.04. Is there something I need to know to make ndiswrapper work on 12.04?

Thank you

I am trying to install a DWL-G650+ PCMCIA card

---

### Post by stchman on 2012-04-11
Usually ndiswrapper is used to get wireless cards working using the Windows driver.  What kind of chipset does your wireless card have?

---

### Post by Galael on 2012-04-11
It says AR5212/AR5213 from Atheros

---

### Post by stchman on 2012-04-12
Did you try Ubuntu 11.10?  I played with 12.04 and because it's in Beta means that it may have unpredictable behavior and some things might not work.

Create a LiveUSB of 11.10 and see if that works for you.

---

### Post by Galael on 2012-04-12
I was finally able to install madwifi drivers and make them load on startup

---

