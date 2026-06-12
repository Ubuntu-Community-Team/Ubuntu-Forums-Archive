---
title: "External hardrive failed READ"
date: 2011-09-13
forum: Hardware
---

### Post by faustusin on 2011-09-13
Hi. M a bit new to ubuntu. Running it from the live disc.

My seagate external hard drive is not showing up in my computer and the disk utility shows an error as seen in the attachment.

Kindly help in recovery of data or even better recovery of hard drive.

Despondent 
Faustus  :confused:

---

### Post by varunendra on 2011-09-14
First of all, STOP USING THAT DRIVE!!
The more you use it, the worse it gets if it is failing.

Next, I'm not sure but I think a USB drive can only show up in nautilus if it is mounted successfully. But I may be wrong on this.

Assuming it is a 2.5" portable hard drive, are you using the original USB cable provided with the hard drive or is it some other one? I've seen detection/read failures occurring in case of weak or lengthy cables. The reason is leakage/weakening of signals or voltage across the cable. As such, a weak USB port which can not provide sufficient power may also cause the same problem.

However, even if it is a 3.5" drive with external power adapter, the signal weakening factor may still apply in case of a non standard USB cable.

How old the drive is. Since the picture shows 141 bad sectors on it, I assume it is quite an old one and may be failing due to normal wear & tear. If this is the case, you may have luck (but no guaranty) with some professional data recovery tool. I once had a failed hard drive with a lot of important data on it. Any computer to which I attached it used to just hang during boot-up. I managed to recover the data using network edition of RTools (not free!). Its way of working was:

[LIST=1]
[*]attach the hard drive to a computer connected to another computer via network cable,
[*]install 'RTools agent' on the other computer (I used windows XP at that time, although I think its linux version also exists)
[*]boot the computer with the 'failing' hard drive with 'RTools Emergency' CD. In my case, the computer initially seemed hung as the live cd was trying to probe the hard drive, then it gave up and booted without probing the drive.
[*]Establish communication between the 'agent' and the other computer. I don't exactly remember how, but it was quite trivial.
[*]At this stage, using the agent interface, you may either create a hard drive image of the failing drive to work upon (to avoid further damaging the drive wile working on it) or can try to recover data working directly on the drive.
[/LIST]
You may try some other similar tool, maybe a free one. The only advantage I had in using the 'RTools emergency disc' was that it was self bootable and thus didn't require an installed OS to 'probe' the hard drive in order to work on it.

---

