---
title: "Clarification on Ubuntu LTS Kernel Upgrades"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by degel3030 on 2009-04-27
Am I correct in thinking that Ubuntu LTS will not upgrade the kernel by doing the standard apt-get update apt-get upgrade (or aptitude update aptitude upgrade)? I have been running LTS for some time and now I am looking to possibly implementing this into a Corp environment and we can not have the kernel upgrading unless we do it manually. It seems I remember any kernel upgrade that was done on my personal boxes had to be done manually (unlike Ubuntu Desktop)

---

### Post by cariboo on 2009-04-27
The only time the LTS version will do a kernel upgrade is if it is a security update. You don't have to do a kernel upgrade, even if it is available. My server typically was 2-3 kernel updates behind as I didn't feel the need to reboot.

---

