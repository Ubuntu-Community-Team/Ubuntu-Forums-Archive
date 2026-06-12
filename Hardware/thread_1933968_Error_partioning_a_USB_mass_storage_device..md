---
title: "Error partioning a USB mass storage device."
date: 2012-03-01
forum: Hardware
---

### Post by Varys'littlebird on 2012-03-01
I'm trying to get a USB mass storage device working. According to the disk utility in Ubuntu it isn't partitioned and the capacity is at 0.0 kb. If I attempt to format it I get this: [I]Error creating partition table: helper exited with exit code 1: In part_create_partition_table: device_file=/dev/sdc, scheme=0
ped_device_get() failed[/I] . Is the device broken beyond repair, or is there some linux voodoo ritual that might fix this? 

Thanks for any help in advance! :)

P.S: It doesn't work in Windows either so the problem isn't Ubuntu specific.

---

### Post by Dngrsone on 2012-03-01
Either the device is broken, or there is a read-only lock on it.

---

### Post by Varys'littlebird on 2012-03-01
Hmm. Is there a way I can figure out which one it is?

---

### Post by Dngrsone on 2012-03-01
If there is a little tab or slide-thingy on the side, then move it to the other position and try again.

If not, then it's broken.

---

### Post by Varys'littlebird on 2012-03-01
Probably broke then. Thanks for your help :)

---

