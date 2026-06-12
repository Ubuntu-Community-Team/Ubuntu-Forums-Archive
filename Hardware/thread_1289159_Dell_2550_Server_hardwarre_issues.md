---
title: "Dell 2550 Server hardwarre issues"
date: 2009-10-12
forum: Hardware
---

### Post by mel_phil@flashmail.com on 2009-10-12
Hi,

Have a 2550 PE server.  I Cannot install any pci cards. Get Plug & play errors & the scsi bios will not load when card is inserted

Used Dell Diagnostics NO errors were found. tried to clear nvram Put jumper on  inv-clr booted got message it was on. then removed and booted to bios to make sure correct - no change

Bios is A09. Embedded Server Management Firmware 5.50. Primary system backplane controller firmware revision 1.30. Adaptec AIC-7899 scsi bios build 25309

2 X 933mhz P3 CPU's, 2 X 33G scsi HDD in each in RAID 0, 512 meg RAM

System works fine otherwise. All green lights on the front panel


Any help appreciated

Cheers :)

---

### Post by viper250 on 2009-10-12
If I remember correctly the scsi bios does not load on card insertion but will load when you press ctrl-m during boot process. this is standard for a lot of server hardware.
you should go into setup and make sure the pci configuration is enabled.
Im running dell 2800 dual 3.4 processors, 8 hdd, 6 gig ram, ubuntu server
have run server for a few years so I hope this helps
I would also check dell hardware support about the plug and play errors

---

### Post by mel_phil@flashmail.com on 2009-10-13
Thanks for the reply. My scsi card does not have raid. My bad in the OP saying raid 0. I have ctrl a key process (sorry) but it does not me do that either. I actually registered for the Dell community forum (and even installed dreaded Win as well) & thats where I got the idea to try inv-clr jumper. Thanks anyway:):)

---

