---
title: "USB2 / USB3 problems? External HD stopping to work"
date: 2022-04-26
forum: Hardware
---

### Post by dieter-erich on 2022-04-26
I connect four external USB Toshiba HDs (5 TB) formatted with xfs to my workstation running Mate 20.04. Upon mounting them I can perfectly access them w/r. However when scp-ing substantial amounts of data to another storage device all of a sudden I receive an I/O error message, the HDs become inaccessible and do not even show up in lsblk. They are not detectable any more. 

I tried changing the USB port or connecting and connecting only one of the HDs but the behavior is the same: after between minutes and hours the disk disconnects. I have to mention that I have a case with a 16 TB HD that is also connected via USB which runs perfectly well since many days. So what can be wrong?I suspect that the USB3 ports of the workstation are too quick for the (I presume) USB2 of the disks. What can I do? Thanks for hints, D-E

---

### Post by Autodave on 2022-04-26
Check your 5 volt output from the power supply.......it might be going too low.

---

### Post by dieter-erich on 2022-04-28
Thanks, shall do! In the meantime I checked with 'sudo hardinfo'. It gives me the following output: 
USB Devices
can't get debug descriptor: Resource temporarily unavailable
can't get device qualifier: Resource temporarily unavailable
can't get debug descriptor: Resource temporarily unavailable
can't get debug descriptor: Resource temporarily unavailable
can't get debug descriptor: Resource temporarily unavailable
can't get debug descriptor: Resource temporarily unavailable
can't get debug descriptor: Resource temporarily unavailable
can't get debug descriptor: Resource temporarily unavailable
can't get debug descriptor: Resource temporarily unavailable
can't get debug descriptor: Resource temporarily unavailable
can't get device qualifier: Resource temporarily unavailable
can't get debug descriptor: Resource temporarily unavailable
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
can't get debug descriptor: Resource temporarily unavailable
can't get device qualifier: Resource temporarily unavailable
can't get debug descriptor: Resource temporarily unavailable
can't get debug descriptor: Resource temporarily unavailable
can't get device qualifier: Resource temporarily unavailable
can't get debug descriptor: Resource temporarily unavailable

---

