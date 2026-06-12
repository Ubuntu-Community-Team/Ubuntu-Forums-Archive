---
title: "Process for dealing with a bad disk in a RAID1"
date: 2008-09-24
forum: General Help
---

### Post by antun on 2008-09-24
My Ubuntu 6.06 server has two hard drives set up with software RAID1 (mirrored). Recently it's been crashing, and it looks like the first drive (0) is bad. I've run the manufacturer's diagnostics on the drives.

Has anyone got any tips  for navigating me through the process of replacing it? Any other tests I should be doing, or things I can run to see if these errors can be corrected in any way?

Is it pretty foolproof? i.e. Do I simply plug a replacement in there, and reboot? Or do I have to move the drives around. 

From what I remember about setting this up last year, I'm not sure if drive 1 is set up to boot correctly. It was a Windows-formatted drive originally. Then I bought an identical, new drive to match it, and formatted both. That new drive became drive 0, because I had some issues getting the formerly-Windows drive to boot in the 0 space. 

I'm not sure if this will be a problem, if there's a way I can boot off a CD to install the new drive.

Thanks,

Antun

---

### Post by Titan8990 on 2008-09-24
Is this softRAID, fakeRAID, or a discrete RAID controller?

---

### Post by antun on 2008-09-24
It's definitely software raid. I used mdadm to set it up. Does that tell you which it is?

-Antun

> **Titan8990 said:**
> Is this softRAID, fakeRAID, or a discrete RAID controller?

---

