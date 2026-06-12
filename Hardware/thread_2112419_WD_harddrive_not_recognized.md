---
title: "WD harddrive not recognized"
date: 2013-02-04
forum: Hardware
---

### Post by NixForFree on 2013-02-04
Motherboard: MSI PT880 Neo, Ms 7008
with VIA VT 6420 SATA Raid Controller (recognized by palimpsest!)

Just bought two 1TB Western Digital Caviar SATA Harddrives, but they are not recognized by Ubuntu 12.04 Setup nor by palimpsest nor gparted.
How come? :confused:

Anyone got a hint or a solution for this problem?

---

### Post by Cheesemill on 2013-02-04
Are they recognised by the BIOS?

If they are plugged into the RAID card have you tried them in directly into the motherboard instead (or vice versa)?

Check the power and data cables to make sure they are properly seated.

---

### Post by Yellow Pasque on 2013-02-04
The VT6420, and the VT8237 southbridge were notorious for not recognizing drives unless they were jumpered to force SATA150 mode, so that's something to keep in mind if the BIOS doesn't recognize them..

Ah, here we go. Linky: [http://wdc.custhelp.com/app/answers/detail/a_id/1337/](http://wdc.custhelp.com/app/answers/detail/a_id/1337/)
I'm not sure if it will work on newer SATA 6.0Gb/s drives since they don't have a jumper setting to force SATA150. :\
[http://wdc.custhelp.com/app/answers/detail/search/1/a_id/5387#jumper](http://wdc.custhelp.com/app/answers/detail/search/1/a_id/5387#jumper)

---

### Post by NixForFree on 2013-02-11
Thanks for the answers. As Cheesemill assumed, the BIOS did not recognize the drives. 

Because of other stability issues during the following days I decided to replace the mainboard and not fiddle around further on with it.

---

