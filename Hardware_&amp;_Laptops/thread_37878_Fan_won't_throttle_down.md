---
title: "Fan won't throttle down"
date: 2005-05-29
forum: Hardware &amp; Laptops
---

### Post by kancept on 2005-05-29
When I boot the machine, the fan goes high as expected.  But with all other OSes I've run on this machine (OS/2, DOS, BeOS, Windows, QNX) the fan kicks down to a lower speed once the OS gets to loading, then back up when the proc gets hot.  I thought this was controlled by hardware- I mean, c'mon, OS/2, DOS, and BeOS don't have great power control (APM or ACPI).

I found this thread: [http://ubuntuforums.org/showthread.php?t=32422](http://ubuntuforums.org/showthread.php?t=32422) and ran that 'temperature' command I found in the first post, and the fan immediately kicked down, but it hasn't kicked back up yet.  

I'd like to know a few things:

What does that 'temperature' command do other than give me my temp (was 35 C when I ran it)?  

How can I go about getting my fan to only throttle up when needed, or initialise or however Ubuntu wants to handle it?


Machine specs:

IBM NetVista X41 (all in one)
P4 1.8 Ghz
17" FP (built in) @ 1280x1024
ATI Rage 128 Pro Ultra
120 Gb IBM HDD
1 GB RAM
Yamaha F1 CDRW
Firewire PCI card
Ubuntu Hoary Hedgehog, fresh install, with updates from the little red icon :-)

Ubuntu is the only thing on this machine now.  i spent the day moving partitions to other computers, so Ubuntu is all this machine knows atm.


Thanks,

Adam

---

### Post by pestilence4hr on 2005-06-22
[QUOTE=kancept]
I found this thread: [http://ubuntuforums.org/showthread.php?t=32422](http://ubuntuforums.org/showthread.php?t=32422) and ran that 'temperature' command I found in the first post, and the fan immediately kicked down, but it hasn't kicked back up yet.  

I'd like to know a few things:

What does that 'temperature' command do other than give me my temp (was 35 C when I ran it)?  

How can I go about getting my fan to only throttle up when needed, or initialise or however Ubuntu wants to handle it?
[/QUOTE]

One thing to check is that temperature polling is enabled.  If it is not enabled, you could get the behavior you have described (checking the temperature kicks the fan off or down).  See my post in [this thread](http://ubuntuforums.org/showthread.php?t=41927) and see if it works for you.

---

