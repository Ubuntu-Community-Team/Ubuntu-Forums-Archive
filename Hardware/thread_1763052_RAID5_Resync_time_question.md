---
title: "RAID5 Resync time question"
date: 2011-05-19
forum: Hardware
---

### Post by GuiGuy on 2011-05-19
Hi all,
I'm setting up a RAID5 using 4 X 2T brand new WD EARS drives, AMD ATHLON II X2 Dual Core 265 CPU CPU, ASUS mobo, 2G RAM. 

Drives are formatted ext4. The OS is on a separate drive, i.e. the array will be for storage only. 

I started building the array 4 days ago (mdadm). It is now only 50% complete. I'm starting to think life's too short, especially when I my piddling NAS atom based NAS box built a 4 X 1T RAID5 in a day. 

Or is that the way it is?

**UPDATE**: Looks like it's going a little quicker; cat /proc/mdstat now tells me there's 48 hours to go. Six days seem like a long time, though. 


Thanks

---

### Post by GuiGuy on 2011-05-26
> **GuiGuy said:**
> Hi all,
I'm setting up a RAID5 using 4 X 2T brand new WD EARS drives, AMD ATHLON II X2 Dual Core 265 CPU CPU, ASUS mobo, 2G RAM. 

**UPDATE**: Looks like it's going a little quicker; cat /proc/mdstat now tells me there's 48 hours to go. Six days seem like a long time, though. 


Since no one seemed interested in my waffle I'll continue to bore you :twisted:

The build took five and half days!!

I then decided to test it. I copied 1T of data onto the array from an externally mounted eSATA drive. Transfer speeds were quite good (IMO) at between 45MBs and 65MBs indicated. Or should it be better?

I took out one of the 2T WD drives and replaced it with a 2T Seagate to see what would happen. I used the Disk Utility, which told me the /dev/md0 couldn't be mounted.I click the CHeck Array button. The "repair" took about 18 hours. 

Cheers

---

