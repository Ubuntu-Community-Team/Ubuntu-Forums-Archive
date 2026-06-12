---
title: "Sytem clock run too fast"
date: 2005-11-13
forum: Hardware &amp; Laptops
---

### Post by brick on 2005-11-13
Hi.

I'm using Breezy/AMD64 on an  AMD64 X2 4400+ (dual core). I find that the system clock runs several seconds per minute fast. Using the ntp daemon does not seem to make a difference. I am using the powernow feature (without powernowd, I just set   /sys/devices/system/cpu/cpu[01]/cpufreq/scaling_governor to "ondemand". I mention this, because every now and then the time runs about 3 times faster when the CPU speed scales up.

More specs:

kernel: 2.6.12-9-amd64-k8-smp
Motherboard: MSI K8N-Neo4-F
What else would be useful?

Thanks
Neilen

---

### Post by tseliot on 2005-11-13
Try this guide: [http://ubuntuforums.org/showthread.php?t=53094]("http://ubuntuforums.org/showthread.php?t=53094")

---

### Post by brick on 2005-11-14
[QUOTE=tseliot]Try this guide: [http://ubuntuforums.org/showthread.php?t=53094]("http://ubuntuforums.org/showthread.php?t=53094")[/QUOTE]

Well, using the test recommended in the HOWTO, I don't seem to have the problem.  One caveat though, just adding 'no_timer_check' caused my kernel to panic on boot. It helpfully suggested that I add 'noapic' as well, which got me booting again.

Now, as long as my CPU speed stays constant, the clock is fairly accurate (gains about 0.01 seconds in 3 minutes). However, if the CPU speed starts changing, weird things happen, like these syslog entries: 

Nov 14 11:36:15 genugtig kernel: [  699.037590] Losing some ticks... checking if CPU frequency changed.
Nov 14 11:36:58 genugtig kernel: [  738.348657] warning: many lost ticks.
Nov 14 11:36:58 genugtig kernel: [  738.348660] Your time source seems to be instable or some driver is hogging interupts

and the clock gains about 7 seconds in three minutes. Hmm, and it does not seem to recover once the CPU speed stays the same again. I.O.W. once the clock goes mad, it stays mad...

---

### Post by stimpie on 2005-11-28
There is a bug (5105) for this at kernel.org 

Booting with "notsc" should solve this.

There is also a patch.
[http://bugzilla.kernel.org/attachment.cgi?id=5993&action=view](http://bugzilla.kernel.org/attachment.cgi?id=5993&action=view)

---

