---
title: "Control of hdd led?"
date: 2008-11-02
forum: Hardware
---

### Post by danh48176 on 2008-11-02
I have a 4 drive software raid array in one of those cool SATA backplanes (5 3.5" drive bays in 3 5.25" drive bays) and I have yet to find a way to identify a failed drive.  The enclosure has an activity LED for each drive that changes from green to orange with drive activity.  

My questions is this: Is there a way to control the activity LED in software to help identify a failed drive?

Here are some of the other options I have considered but found less than ideal:

[LIST=1]
[*]Label drives by serial number on the outside of the box, then use smartctl to match failed drive to SN.  The problem is that I would need to power down the server to do this.  Not a huge deal but I'm hoping for something that maintains uptime.

[*]Write a script that causes drive activity at a certain frequency.  This would be something like 
```
while [ 1 ]
do
  dd if=/dev/${FAILED_DRIVE} of=/dev/null count=${ABOUT_1_SECOND}
  sleep 1000
done

```
This seems pretty hacky and wouldn't work if the drive is no longer talking on the bus (it happens).
[/LIST]

What I really want is something like this:
```
while [ 1 ]
do
  turnhddledon /dev/${FAILED_DRIVE}
  sleep 1000
  turnhddledoff /dev/$FAILED_DRIVE}
  sleep 1000
done

```

Any suggestions?

How have others dealt with identifying drives in arrays?

---

