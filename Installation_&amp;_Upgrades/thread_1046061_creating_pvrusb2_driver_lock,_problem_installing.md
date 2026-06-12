---
title: "creating pvrusb2 driver lock, problem installing"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by TSellers on 2009-01-21
I'm trying to follow Mike Isley's directions to apply the fix for plugging a WinTV PVR unit he describes here:

[http://www.isely.net/pipermail/pvrusb2/2008-October/001918.html]("pvrusb2 driver lock")

THis is where I'm having the problem:
> Alternatively, putting the following into a file anywhere under 
/etc/modprobe.d/ should work even better:

  options pvrusb2 initusbreset=0


I found a file in that folder called 'options' so I tried to add the line in there, but I did not have permissions. So I created a new file on my desktop called 'modprobe' and tried to move it into that folder, same problem again. If anyone could direct me as to the proper way to implement that fix into that folder it would be greatly appreciated.

Regards, Tom

---

