---
title: "usb keyboard"
date: 2008-12-30
forum: Hardware
---

### Post by sandy8925 on 2008-12-30
hi i recently bought one of those flexible keyboards with a usb interface. it works fine with the ps2 converter{usb to ps2} on my desktop but it doesn't work in usb in either windows or ubuntu. there was no cd along with it. could someone help me to get it working?

---

### Post by Hydrid on 2008-12-30
Could you give more info about your keyboard please! e.g Brand,Model etc...

---

### Post by richg on 2008-12-30
In terminal type this   lsusb

Here is an example of my PC with a rubber based roll up USB keyboard I bought on ebay for about $15.00.

lexon@lexon-desktop:~$ lsusb
Bus 005 Device 004: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 005 Device 003: ID 0409:005a NEC Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 03f0:2404 Hewlett-Packard 
Bus 001 Device 005: ID 04a9:220d Canon, Inc. CanoScan N670U/N676U/LiDE 20
Bus 001 Device 004: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 001: ID 0000:0000  
lexon@lexon-desktop:~$ 


Rich

---

### Post by sandy8925 on 2008-12-31
Sorry but there's no info about brand or model. I'll have to search for the cover. I did try typing lsusb but it just showed 4 root hub devices. The keyboard wasn't listed at all.I didn't have any other usb devices conencted.

---

### Post by sandy8925 on 2009-01-01
Here's the output for the lsusb command:


sandeep@main-comp:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

apparently it hasn't been detected at all.

---

### Post by sandy8925 on 2009-01-15
Well actually it has only 80 keys so it's probably not acccepted as a standard keyboard. Is there anyway I can make it work like making an entry in xorg.conf ?

---

