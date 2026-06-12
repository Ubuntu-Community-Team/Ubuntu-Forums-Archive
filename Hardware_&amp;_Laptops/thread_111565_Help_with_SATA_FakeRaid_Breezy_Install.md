---
title: "Help with SATA FakeRaid Breezy Install"
date: 2006-01-02
forum: Hardware &amp; Laptops
---

### Post by kyri on 2006-01-02
I think I'm pretty close. I was able to get partitions setup and ubuntu installed. Grub is configured and dual boots XP and Ubuntu. During the ubuntu boot, my kernel loads, and the initrd script local-top starts. Device Mapper appears to load fine. I get the the initialised message.

Then I get a Kernel panic Circular dependency. On what I assume is the dmraid -ay command.

any suggestions?

I wonder if it's my kernel I'm using amd64-k8-smp perhaps during livecd install the dmraid apt-get slurped up isn't compatible with that kernel?

-kyri

---

### Post by realriot on 2006-01-04
Having the same problem. Searched everywhere but didn't find any answers :(

---

### Post by realriot on 2006-01-06
I've located the problem. There were some failures within the "initramfs-tools"-scripts...

I just have updated the FakeRaidHowto-wiki...

best wishes
Sascha

---

### Post by BoneKracker on 2006-01-23
Thanks for leaving a trail of bread-crumbs.  I'm having the exact same problem and had it narrowed down to a problem in that script but wasn't sure what to do next.

---

### Post by BoneKracker on 2006-01-30
I think one of the things that enabled me to make this work was adding the following to the /etc/mkinitramfs/modules file:

dm-mod

---

