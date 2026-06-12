---
title: "Lock-ups on Lenovo T60"
date: 2012-06-18
forum: Hardware
---

### Post by graxspoo on 2012-06-18
I just installed 12.04 on an old Lenovo T60 Thinkpad. I'm mostly really liking it, except several times in the last two days I've gotten into a state where all user input is rejected. The mouse moves (both from the touchpoint and touchpad) but I can't click on anything. Key presses are also ignored. All I can do is reboot. Being a Linux newbie, I have no idea of what debugging strategy I might use to try to figure out what's going on. Pretty much all ll I'm running is firefox, and this is a vanilla clean install. The lock-ups seem fairly random. One time it definitely happened when I was trying to drag a firefox window between workspaces.

---

### Post by dyous87 on 2012-06-18
I had a similar problem with several old Thinkpads.Try removing the battery. It seems that a dead battery (no longer holding charge) can cause this issue under Linux on the thinkpad.

---

### Post by graxspoo on 2012-06-18
Hey, thanks for the input. The battery seems OK. I can run on battery power for five or six hours of moderate use including wireless networking. 

> **dyous87 said:**
> I had a similar problem with several old Thinkpads.Try removing the battery. It seems that a dead battery (no longer holding charge) can cause this issue under Linux on the thinkpad.

---

### Post by graxspoo on 2012-06-18
One other data point: I can boot into Windows XP on the same system, and I don't run into this behavior.

---

### Post by dyous87 on 2012-06-18
Just out of curiosity, if you boot into an Ubuntu Live CD do you have the same issue?

---

### Post by graxspoo on 2012-06-18
Dunno. I'll give it a shot and report back. That's a mode the original install CD I made can run in, right? I seem to remember a "try ubuntu without installing" option.

---

### Post by dyous87 on 2012-06-18
Yes "Try without installing" will boot into a live system that runs right off the cd/dvd.

---

### Post by graxspoo on 2012-06-19
I played around with the live CD for about a half hour last night. I didn't get the lock-up, but I'm not sure it's a great test, because its too slow to really use, and the timing is completely different because it keeps hitting the CD.

---

### Post by graxspoo on 2012-06-20
More testing with the live CD last night did not turn up any freezes. Someone in another thread mentioned this might be related to X windows. This is possible, since I installed Gimp.

---

