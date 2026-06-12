---
title: "When and from where does ath_hal load?"
date: 2007-09-30
forum: Hardware &amp; Laptops
---

### Post by xerxesv5 on 2007-09-30
There's a 'killswitch' on the front of my lappy for my wifi card. This breaks ath_hal when it tries to detect it (error 13). So, I need to (BEFORE ath_hal does anything)...

- modprobe acer_acpi ... to be able to interact with the switch
- echo "1" > /proc/acpi/acer/wireless ... to turn on the card.

and only THEN let ath_hal do its thing, except I don't have the slightest clue how to accomplish this, /etc/modules wont let me do the echo, and I cant see which init.d script invokes detection.

Please help!

---

