---
title: "Ubuntu Install to Intel ICH10R RAID Guide?"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by BraedenNaylor on 2009-10-13
I am currently running Ubuntu 9.10 Beta. I need to know how to install Ubuntu onto hard drives using RAID 0, Intel ICH10R. They show up under Ubuntu as a whole bunch of different names, I tried installing it once and it completely failed and wouldn't boot. Any guides to this?

Thank you

-Braeden

---

### Post by tosk on 2009-10-13
As far as I know, Linux doesn't support RAID with ICH10R. Only AHCI. That's why even though your array is defined in the RAID BIOS, Linux still sees each disk individually.

---

### Post by BraedenNaylor on 2009-10-13
Guide to use software RAID with ubuntu then? I guess google would be alot faster. any incompatibility with ubuntu and software RAID?

---

