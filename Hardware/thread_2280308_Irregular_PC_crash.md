---
title: "Irregular PC crash"
date: 2015-05-29
forum: Hardware
---

### Post by hans12345 on 2015-05-29
I have HW problems on my desktop PD, Ubuntu 14.04 LTS. It is a well established PC with no significant HW or SW changes recently.

Sometimes on Boot, I get either a black screen or a normal display but with no working KB nor mouse.
During GRUB phase, screen and KB work, the failure happens later, either just before the 'purple' start screen or just after.
Very occasionally this happens when I leave the PC running.
I just reboot, and usually this fixes the problem.

So, I assume a memory, HD, power, overheating or CPU/MB problem. Plenty of choice.

I tested the memory (memtest), HDs (fsck) and both seem OK.

There must be some logs/diagnostics I could look at.

Can anyone suggest where I should look?

Is using the linux crashdump the best way to go?

Thanks for your help.

---

### Post by weatherman2 on 2015-05-29
fsck doesn't test the hard drive - it tests only the file system.  Check S.M.A.R.T. Attributes, and run S.M.A.R.T. tests using GSmartControl to be sure the hard drive is OK.

Logs/diagnostic files will help you with software problems but often not with hardware problems.  But you can check various files in /var/log like syslog.

 You can use lm-sensors to monitor CPU temperatures, if your motherboard's sensors can be correctly detected, to see if you are overheating.

---

### Post by hans12345 on 2015-05-30
> **weatherman2 said:**
> fsck doesn't test the hard drive - it tests only the file system.  Check S.M.A.R.T. Attributes, and run S.M.A.R.T. tests using GSmartControl to be sure the hard drive is OK.

Logs/diagnostic files will help you with software problems but often not with hardware problems.  But you can check various files in /var/log like syslog.

 You can use lm-sensors to monitor CPU temperatures, if your motherboard's sensors can be correctly detected, to see if you are overheating.

Thanks Weatherman.

Gsmartcontrol installed. Short tests OK on both drives. Will run long tests when not needing PC.

lm-sensor not found in Ubuntu store. Tried Psensor instead. Only 2 temperatures tracked, both seem OK.

Any comments on the value of linux crashdump?

More to come.

---

### Post by hans12345 on 2015-05-30
Gsmartcontrol long tests OK on both drives. 

Now, I assume a  power, overheating (unlikely) or CPU/MB problem.

Advice anyone?

---

### Post by hans12345 on 2015-05-30
Gsmartcontrol long tests OK on both drives. 

Now, I assume a  power, overheating (unlikely) or CPU/MB problem.

Advice anyone?

---

### Post by tgalati4 on 2015-05-31
Check your voltages with a meter or in BIOS, otherwise, find another PSU to test with.  If you don't have a spare PSU, then pull out stuff in your current computer to get to a minimum condition:  Minimum RAM, one hard disk, on-board graphics, etc.  Clean out the motherboard with compressed air.  Inspect for leaky or bulging capacitors.  How old is the machine?

In general, linux log files are not helpful in this situation, because linux assumes perfect hardware.  When you have hardware problems, the software errors that are generated are often misleading.

---

### Post by Yellow Pasque on 2015-05-31
It kind of sounds like a "race condition" with the init system to me, but that doesn't explain why it happens when running.
I don't think overheating would be the culprit if it happens on boot, unless the southbridge is not properly cooled.

Can we see the smarctl output?
```
sudo smartctl -a /dev/sda/ -q noserial
```

Also, check BIOS version:
```
sudo dmidecode -t 0
```

---

### Post by hans12345 on 2015-06-01
Thanks all,

Things are busy ATM, but I will get back to you shortly.

---

### Post by hans12345 on 2015-11-12
I am closing this tread.

It is clearly some sort of contact problem, probably MB.

It always crashes when starting from cold. The crash is always different. Sometimes the 2nd or 3rd boot fails as well. I find that if I switch it on and ignore the PC for 30 mins and then reboot, it will usually work fine.

Once started, it does not fail at all even if left for 24 hours.

Time for a new MB.

Thanks everyone.

---

