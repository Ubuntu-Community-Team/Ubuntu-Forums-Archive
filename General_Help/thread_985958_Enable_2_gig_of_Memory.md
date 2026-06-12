---
title: "Enable 2 gig of Memory"
date: 2008-11-18
forum: General Help
---

### Post by darkblade25 on 2008-11-18
I just installed ubuntu 8.10. I am pretty impressed so far. 

There is a problem though, with my memory. I have 2 gigs of ram but ubuntu only see 1 gig. 

Here the output for  sudo lshw -C memory

```
  *-memory
       description: System Memory
       physical id: a
       slot: System board or motherboard
       size: 1GiB
       capacity: 2GiB

```
Any ideas?

---

### Post by Elfy on 2008-11-18
I'd check that it's seated properly and recognised by BIOS - then run memtest from the livecd to make sure it was there first.

---

