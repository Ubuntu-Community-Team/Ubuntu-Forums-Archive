---
title: "Hard Drive Assessment and hdd occassion freeze"
date: 2012-11-06
forum: Hardware
---

### Post by linux-wannabe on 2012-11-06
Not ubuntu specific, but here anyway to get help. 

problem: 
a) The hard drive indicator stop blinking or completely goes dead and computer freezes. At this point I have to do HARD REBOOT, as keyboard/mouse do not respond. neither do the special commands, ctrl-alt-(function keys) f7/f1/f3/f12 respond.
 
b) When I do hard reboot, there is no guarantee the computer will boot again. Usually when this happens I've noticed that hard drive light never comes up on boot. At that point I usually wait for 10 mins or more and pray and forsure it boots later, but may freeze again. 


tried and concluded:
TR1: Problem not related to software: Tried fresh installs of all system (win 7, xp, ubuntu), i always have the problem.

hardware spec: 
t61 lenovo, with nvidia 140m, hitatchi 100gb drive, 2gb ram. machine is more than 5 yrs old, I've replaced the fan on it already once.

I am attaching hard disk results from smartmontools.

Request:
a) Can you please advise how to read this result? If this was your hard drive what would you do? Does the hard drive need replacement?
b) Is there a way to rule out mobo / graphics card issues? 

Thanks in advance

---

### Post by ahallubuntu on 2012-11-06
You've got one pending sector, which is more than enough to cause the kind of problems you have been describing.  That sector can't be read; if the operating system tries to read a file that contains that sector and cannot, then it could easily freeze up.

What I usually do in a case like this is to zero out the drive completely (which will erase everything) and hope that clears the pending sector.  If it doesn't, you will need to replace the drive.

Obviously, backup everything you care about on that drive before zeroing it out.  Once you've done that, you can use DBAN to wipe the drive overnight, then check S.M.A.R.T. again using a live CD like Parted Magic.

If you want to try to preserve your existing operating system partitions before wiping, you could try copying the partitions to, say, an external drive, first, with tools like partimage or even dd.  If that one sector is in an important file, you may get an error in copying, though.  If you are lucky enough to find out which file (e2fsck may tell you), you could potentially replace it to fix the OS.  or maybe it isn't in an important file and it will be OK after you wipe.

Cloning the drive to a new one would do it, too, and be easier if you happen to have one.

---

### Post by linux-wannabe on 2012-11-06
a) Everything is backed up, so no worries there.

b) does zero out means format the drive? if yes, then I've done that few times as trying to install OS. ironical is that many times during the install of OS also my computer has frozen, so I am getting tired.

c) DBAN the drive - I tried this option, but i get this error on autonuke/and in interactive mode:
Error 8000 reading sector 2551
.EDD: Error 8000 reading sector 2615
.EDD: Error 8000 reading sector 2137
.EDD: Error 8000 reading sector 3639
.EDD: Error 8000 reading sector 4151
.EDD: Error 8000 reading sector 4663 

finally i am wondering if there is a way to quarantine the broken sector of my hard drive from read/write. if i can do that'd be the sweetest when i install the new OS, ill pick the good sector.

---

### Post by ahallubuntu on 2012-11-07
No, formatting and zeroing out the drive aren't the same thing.  Formatting only re-arranges the sectors into a new file structure but doesn't write to all of them.  You want to write zeros to every sector (DBAN can do this on numerous passes).

Modern hard drives can automatically "quarantine" bad sectors and even replace them with spares; that's what the "reallocated sector" line means in the S.M.A.R.T. status.  If you had say four reallocated sectors, that means four sectors had failed and been marked "do not use" by the drive firmware.  If the drive is unable to do that, an operating system wouldn't be able to, either.

If DBAN has severe errors just trying to write to the drive, it is probably junk. Hard drives fail all the time and it is very common, so you shouldn't be that surprised.

---

