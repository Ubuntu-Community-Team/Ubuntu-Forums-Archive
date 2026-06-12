---
title: "RAID1: mdadm auto-assemble with condition..."
date: 2016-12-08
forum: Hardware
---

### Post by Valter Fukuoka on 2016-12-08
**Software Environment:**
--------------------
I am using Ubuntu 16.04, 16.10 Debian 8 Jessie


**Problem:**
-------
(Linux soft) RAID1 array on 2 USB drives.
When only ONE drive is connected with ANY system (where mdadm is running),
the array is AUTO-ASSEMBLED and becomes a "degraded array"...


**Desirable:**
---------
Since there are more partitions on those drives that are not part of the
array, I like to know if there are any mechanism to "mark" an array
so that it is ONLY AUTO-ASSEMBLED when running from a specific system
(using some UUID to identify the host system).
So, it will auto-assemble when the host is the 'target' system,
but it will NOT auto-assemble when the drive is connected to
ANY other system where the mdadm is installed and running,
but the UUID 'mark' does not match...


**Perhaps something like:**
-----------------------
```
mdadm --create --target-host-id=/boot/mdadm/target-host-id
```

so that, the array itself have (internally) a copy of the target-UUID
declared and when this ID is present, it will be check if match
with a text copy inside a declared location (/boot/mdadm as in the example), 
and, if it does match, the array will auto-assemble, else, if the ID does not
match, there will be no action on the part of the mdadm code, preventing
the array to go online as "degraded"...

[B]
Re-add OK:[/B]
---------
By using the --bitmap=internal I was able to solve the degrade problem
by re-adding the removed disk, so that the array becomes CLEAN again,
but I like to know if there any way to prevent the auto-assemble
when the drive is connected with any other host that is not the intended host...


**Auto Assemble feature is needed:**
-------------------------------
Since the (my) main-target system need the array at boot time,
because its filesystem is inside the array itself,
the auto-assemble is a desired/necessary function, so this mechanism
is a feature that need to be working...
What I need is to prevent ANY other host system to auto-assemble and
mark the status of the array as "degraded"...

[B]
Question:[/B]
--------
Any of the current mdadm features (2016/Dec),
allows me to accomplish the desired result?

Thanks all,
Valter Fukuoka

PS: Also, what is the place (list, website) where I can ask the
mdadm developers about this question, or ask/suggest for a feature?

PS2: Not sure if my topic is in correct forum...

---

