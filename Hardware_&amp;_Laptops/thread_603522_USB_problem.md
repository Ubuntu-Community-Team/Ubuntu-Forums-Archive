---
title: "USB problem"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by kafkaian on 2007-11-05
Hi, have an Asus P5V-VM DH which mounts USB media from the integral motherboard USB sockets but not via the front and rear USB sockets that are connected via leads to the motherboard.

I have checked the BIOS to see if any switch makes a difference but nothing.

The jumpers on the motherboard differentiate between Wake-up and not and don;t seem to make a difference.

Checked the leads several times.

Inserting my Sony drive into various orifices, lsusb seems to list them all but nothing registered as connected in the external ports:

Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 0000:0000  

However, the integral usb shows up okay:
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 054c:019e Sony Corp. 
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 0000:0000

Any ideas how to proceed? With Feisty and a Gigabyte P4, this is not a problem

---

### Post by kafkaian on 2007-11-05
Hmm, dry joint on the motherboard underneath the Wake-ON USB jumper connector. I can just see the solder trail flick out the side of the m/board

How do I mark this as 'solved'?

---

