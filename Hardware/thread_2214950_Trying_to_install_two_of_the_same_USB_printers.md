---
title: "Trying to install two of the same USB printers"
date: 2014-04-03
forum: Hardware
---

### Post by rmflagg-gmail on 2014-04-03
Hi Everyone,

   I have two Zebra LP2844 printers, each with a different settings and different size labels.  The system is running 12.04.

   After installing both, it became apparent that both of the install printers were pointing to the same printer and the second printer was being completely ignored.

   How do I set this up so that each printer is uniquely identified?

Thanks,
RM Flagg

---

### Post by kurt18947 on 2014-04-04
Hi

No expert here and not familiar with Zebra printers but how are they connected?  If they were connected via network, can they be assigned static I.P. addresses?  If connecting via USB,  the device URI  usually includes the device serial number in my experience.  The printer administration app varies  by distro.  I'm using gnome-shell which uses a dumbed-down 'printers' app.  I install "system-config-printers" from the repositories which I find more informative.

---

