---
title: "Rogue dd and klog processes"
date: 2008-11-19
forum: General Help
---

### Post by fongandrew on 2008-11-19
CPU usage occasionally spikes to 100% and hovers there, even after I close everything. Top reveals that the dd and klog processes are responsible for most of the CPU usage.

I usually have Firefox and Gedit open, with Apache running in the background, when this happens. I haven't been able to establish any link between these and dd/klog though.

Using Ubuntu 8.10 x64 on a Lenovo T400.

Any ideas?

---

### Post by iponeverything on 2008-11-19
> **fongandrew said:**
> CPU usage occasionally spikes to 100% and hovers there, even after I close everything. Top reveals that the dd and klog processes are responsible for most of the CPU usage.

I usually have Firefox and Gedit open, with Apache running in the background, when this happens. I haven't been able to establish any link between these and dd/klog though.

Using Ubuntu 8.10 x64 on a Lenovo T400.

Any ideas?

```
pstree -up 
```

Might show who the parent is.

---

### Post by fongandrew on 2008-11-22
No luck with that. The dd and klog processes were started by init. So it looks like they were running in the background when something triggered them.

---

### Post by uber_nerd11 on 2008-11-22
I too am having the same issue with ubuntu 8.10 x64.  Both cores at a full 100% utilization.  Any help would be appreciated.  Thanks!

---

### Post by colsandurz on 2008-12-21
This is so weird.  I am having the problem on my dual core lenovo X61...

---

