---
title: "Help! Removed Ubuntu but something went wrong with my partitions"
date: 2008-10-02
forum: General Help
---

### Post by Luci4 on 2008-10-02
Hi,

I just followed a How to ([http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)) to delete my ubuntu from a dual boot pc: I used the fixmbr program (checked that my device was indeed 0) then put the ubuntu live cd in, and started up gparted. I deleted the non windows partitions and resized them to my d: (I had c: which was 15gb and d: which was 25gb. I added my deleted ubuntu partitions to d:, so it should be about 45gb).
Everything went ok, I started up my windows, but then when I  checked, it said my d drive only had 25gb, not 45. But when I open partition magic, which is like gparted, it says D: is 45gb big. I restarted and checked again, but my computer is still convinced D: is only 25gb.
???? Ever so slightly confused! what can I do?
Thanks for the help!

---

### Post by danking12 on 2008-10-02
I would suggest two options:

One try running Chkdsk.exe, [http://support.microsoft.com/kb/315265](http://support.microsoft.com/kb/315265)

If that doesn't help then maybe try deleting the partition, creating it again with the full size and formatting it. If you have data on it you would have to back it up somehow.

I know I have run into a few issues with resizing partitions in Windows.

---

### Post by Luci4 on 2008-10-03
checking the disk just showed me I had 25gb (instead of 40) on it and no errors or anything.
I'll look around if anybody knows that actually deleting the partition and recreating it will do the job.. All my programs are on D: so I don't know how that works with backing up...
And if anybody knows another solution, please!

---

