---
title: "Weird hard-drive problem after update to 10.04.1"
date: 2010-08-27
forum: Hardware
---

### Post by chrisf1874 on 2010-08-27
My son 'updated' his 10.04 installation on his Acer Aspire One to 10.04.1 a couple of days ago not realising that this was unnecessary. Oh, how I wish we'd left well alone because he's been using 9.10 then 10.04 for the last six months with no problems at all.

The installation went without problems. It restarted fine but within a couple of minutes had locked up. It does this within a minute or so of any activity. Researching 10.04 lock-ups, I decided to roll back to 9.10 but could not reformat the hard-drive. You delete the partitions and apply, wait a second and the partitions are there again. Using fdisk gives the same result, no errors but no change to the partitions.

I think I've established that I can't write the hard-drive but I don't see any errors. If I use a text editor to create a file, I can read it back ok but if I restart, it's not there. I guess during the session I'm seeing a cached copy.

The behaviour feels like a hardware fault but there are no complaints that I can see (nothing in dmesg). Is it simply coincidence that the HD failed shortly *after* installing 10.04.1?

Can anyone suggest anything else I might look into?

Thanks in advance,
Chris

---

### Post by quixote on 2010-08-30
Erm, what *is* 10.04.1?  Do you mean one of the kernel updates?  Or do you mean he went and installed 10.10 (Maverick Meerkat)?  It's strange that the HD won't work and yet there are no errors reported.  I believe there's a hardware checking routine somewhere on the liveCD, but I don't have one available right now.  Alternatively, (I don't know if this would be feasible) if you could remove the HD and attach to a Windows machine, you could use their disk checking routines to see whether it really is a hardware fault.

---

