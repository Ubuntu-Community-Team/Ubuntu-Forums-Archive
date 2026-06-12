---
title: "Touchpad and Keyboard not responding"
date: 2011-04-07
forum: Hardware
---

### Post by gr34t3st on 2011-04-07
I'm running 11.04 on a Sony VAIO CW laptop. I've been runing 11.04 for a while now with no problems ... until this morning. I ran sudo apt-get update && sudo apt-get dist-upgrade like I normally do every morning to get the updates. This morning, it returned an error. I didn't look too far into it, thinking it was just a failed download. I was late to classes so I shutdown my computer and left. When I came back, I turned on my laptop to find that my keyboard, touchpad, and external mouse were not responding. The graphics also seemed fuzzier than normal. If it helps, the LED lights that signify caps lock, num lock, etc. were not lighting up when I pushed those keys.
 
When I boot into recover mode I get this error message
 
```
FATAL: Error inserting vesafb (/lib/modules/2.6.38-8-generic/initrd/vesafb.ko):
No Such Device
_
```
 
I get the same error when I try to boot into previous linux versions as well. Is there anything I can do? I'm not sure why an update would make my system react this badly. Also, I understand this is 11.04 and that it's in its beta stage. I'm not asking for your sympathy. I would just like some solutions.
 
Thanks

---

### Post by nashibuntu on 2011-05-13
I've just upgraded to 11.04 (Ubuntu server version). I am getting the messages

mountall: Plymouth command failed
mountall: Disconnected from Plymouth

on boot. I tried updating by grub to specify nosplash to see if that would help and now I get the message you reported when booting too. No idea how to get rid of it (other than putting the splash back on). Did a search around but I can only find reports of this message - no solutions.

---

### Post by u007 on 2011-06-06
im having the same problem!
help! i cant boot any more, even in recovery mode!

---

