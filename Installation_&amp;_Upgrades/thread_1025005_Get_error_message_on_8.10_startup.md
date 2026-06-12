---
title: "Get error message on 8.10 startup"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by Taidgh on 2008-12-29
I just installed 8.10 on my laptop from a live disc. When I restarted, I got this: 
```
Boot from (hd0,0) ext3   359c0d4d-5e95-4cc7-b93c-f97aeb39fcd2
Starting up...
[     0.410870] ACPI: Aborted because junk in gzipped archive.
[     2.591220] Kernel panic - not syncing: VFS: Unable to mount (goes off screen)
root fs on unknown
wn-block(0,0)
```
What to do?

---

### Post by waltkerr on 2008-12-29
Did you install from the live CD? If so, did you verify Checksums before the install? I'm thinking you might have used a corrupt install file. One idea would be to get a fresh ISO file and re-do the install.

---

### Post by Taidgh on 2008-12-29
I do not know how to verify checksums. Should I go ahead and get a fresh ISO?

---

### Post by Taidgh on 2008-12-29
I booted from the disc, and went to check integrity. It said there were no errors. Does this mean that the disc wasn't the problem?

---

