---
title: "PCMCIA problem"
date: 2005-08-24
forum: Hardware &amp; Laptops
---

### Post by Nate53085 on 2005-08-24
I was trying to figure out how to get my Compact Flash adapter to work ok.  I was getting 2 beeps, cardctl status looked ok, I really didn't know what to do.....so I killed the card manager.  After reboot, it doesn't come back.  Can someone tell me how to get it back?  Then maybe help me troubleshoot why my card isn't mounted?

Thanx in advance.

----------------------------------------------

EDIT

Somehow card manager is fixed.

user@NateUbuntu:~$ cardctl status
Socket 0:
  3.3V 16-bit PC Card
  function 0: [ready]
Socket 1:
  no card

AND

user@NateUbuntu:~$ cardctl ident
Socket 0:
  product info: " LEXAR ATA FLASH CARD    ", "TWISTER", "TRC03"
  manfid: 0x4e01, 0x0200
  function: 4 (fixed disk)
Socket 1:
 no product info available

But no mounting as a USB device.  Any ideas?

---

