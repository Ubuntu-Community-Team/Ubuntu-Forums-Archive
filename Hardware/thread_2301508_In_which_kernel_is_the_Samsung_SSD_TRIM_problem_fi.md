---
title: "In which kernel is the Samsung SSD TRIM problem fixed?"
date: 2015-11-02
forum: Hardware
---

### Post by Luke Loughead on 2015-11-02
I have a Samsung 800-series SSD and a software RAID next to it. I had to disable fstrim because it fried my installation (affected SSDs plus md RAID exposes the bug). I understand that disabling TRIM is going to really slow down my SSD over time, so I want to re-enable it as soon as possible.

I also understand that Samsung submitted a kernel patch a few months ago to solve this problem (and they fixed it for a bunch of other affected, non-Samsung drives, as well, which is awesome). So, which kernel version has/will have the patch? I want to keep watching for it so I can re-enable fstrim as soon as my current kernel has the fix.

So, anyone know which kernel version has it? Sorry, I've Googled everything and I can't find what I'm looking for (and I'm not sure how to scour the kernel changelogs for the answer, either).

---

### Post by Luke Loughead on 2015-11-02
(Incidentally, I actually bought this Samsung SSD *because* Samsung did such an awesome thing by patching the kernel to solve the problem. I wanted to reward them for making Linux better, but it looks like I was a bit early. I don't think the patch is in the latest kernels in the Ubuntu repos yet. Go figure my setup, SSD plus md software RAID, is exactly what triggers the bug, so I came home to a nice data corruption and a night of reinstalling. D'oh!)

---

### Post by Benjamin_Goering on 2016-01-16
I think it is this commit that first showed up in 4.2
[https://github.com/torvalds/linux/commit/f3f5da624e0a891c34d8cd513c57f1d9b0c7dadc](https://github.com/torvalds/linux/commit/f3f5da624e0a891c34d8cd513c57f1d9b0c7dadc)

---

