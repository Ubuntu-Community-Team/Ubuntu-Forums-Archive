---
title: "tzdata shows up in &quot;Installed (local or obsolete)&quot;"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by Spectre5 on 2009-11-11
Hello all.  I just finished the "upgrade" to 9.10 (quotes because startup is, for now, much slower for me).  Anyways, I noticed that synaptic now lists most of my files under the "Installed (manual)" category and I'm not sure why.  I didn't install most of these, an most of them are in fact system programs.

However, more importantly, it lists a number of packages in the "Installed (local or obsolete)" category.  One of the packages listed in this local or obsolete category is tzdata.  If I select to remove tzdata, it selects nearly everything on my entire system (including things like xorg, acpi-support, alsa-base, etc).  I'm sure this is wrong that thus I have not un-installed this.  But why does ubuntu put tzdata in local or obsolete packages when so many other packages depend on it?

Thanks,
Scott

EDIT: [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/464820]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/464820")

---

### Post by Spectre5 on 2009-11-11
Bump - any ideas?

---

### Post by conchyliferous on 2009-11-12
I would like an answer to that as well.

---

### Post by Spectre5 on 2009-11-13
> **conchyliferous said:**
> I would like an answer to that as well.

An update today corrected the tzdata package for me.  Did it solve the problem for you?

I still have nearly every installed package in the (manual) folder though!

---

### Post by falconindy on 2009-11-13
I think it's pretty clear that Synaptic is broken as far as being able to property categorize packages.

---

