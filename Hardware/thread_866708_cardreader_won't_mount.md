---
title: "cardreader won't mount"
date: 2008-07-22
forum: Hardware
---

### Post by markschu on 2008-07-22
My cardreader (trust 30-in-1 USB2 Card reader CR-1300p) loses, some minutes after putting in SD card, the connection (in ubuntu 8.04). If I try again Mounting I get the error:

mount: /dev/sdc1 is not a valid block device

in lsusb:

code:

[PHP]mark@mark-desktop:~$ lsusb
Bus 008 Device 001: ID 0000:0000 
Bus 007 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 007 Device 001: ID 0000:0000 
Bus 006 Device 001: ID 0000:0000 
Bus 005 Device 002: ID 046d:c047 Logitech, Inc.
Bus 005 Device 001: ID 0000:0000 
Bus 004 Device 001: ID 0000:0000 
Bus 003 Device 001: ID 0000:0000 
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 001: ID 0000:0000  [/PHP]

Please help?

---

### Post by coffeecat on 2008-07-22
Is that with just one SD card, or have you tried others? That might help to decide whether there's a problem with the particular card or the card reader.

---

