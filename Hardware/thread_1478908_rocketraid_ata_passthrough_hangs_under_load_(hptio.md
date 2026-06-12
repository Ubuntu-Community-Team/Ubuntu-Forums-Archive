---
title: "rocketraid ata passthrough hangs under load (hptiop)"
date: 2010-05-10
forum: Hardware
---

### Post by donbowman on 2010-05-10
I have a rocketraid 3540 controller card. It is configured in ATA passthrough (e.g. non-raid mode). 

under load of multiple drives, the controller locks up.

e.g. if i do:
for i in /dev/sd*
do
 dd if=$i of=/dev/null bs=20k count=100000 &
done

the controller will lock up and this will appear:

hptiop_reset(0/0/2) scp=ffff88023535aa00
scsi0: reset failed

if i access one drive at a time it is perfectly stable. 

THis happened after I added drives (it was fine with 8 drives, but i added 7 more and now its unstable).

DOes anyone have any insight into this driver? I have opened a case with their support. It appears to be the firmware on the card that locks up.

---

### Post by hvoordes on 2010-05-31
Hello,
 
Same problem over here. I just installed Ubuntu 10 (install went ok), but trying to update the system lock's the system and gives messages: scsi offline...
 
Do you have a solution yet?
 
Regards,
 
Herbert

---

