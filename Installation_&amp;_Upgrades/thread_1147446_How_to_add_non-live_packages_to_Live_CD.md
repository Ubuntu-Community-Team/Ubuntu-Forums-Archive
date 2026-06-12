---
title: "How to add non-live packages to Live CD?"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by loumz on 2009-05-03
Hi, I'm trying to customize the 8.10 live CD. I read about ubiquity and figured out that if I wanted upgraded packages I should upgrade the packages inside the squashfs filesystem. So far so good. Now, how do I add packages that should be installed, but should not be run inside the livecd? Do I add them to the pool directory? How would I install them later? In the preseeding docs it is said that to add packages, do this:

# Individual additional packages to install
#d-i pkgsel/include string openssh-server build-essential

but in the [https://wiki.ubuntu.com/UbiquityAutomation](https://wiki.ubuntu.com/UbiquityAutomation) page it is said that pkgsel won't work with ubiquity?

Any thoughts?

---

### Post by upchucky on 2009-05-03
you may want to check out UCK, (Ubuntu Customization Kit) it lets you create your own ubuntu iso.

---

### Post by loumz on 2009-05-03
I looked at that. Only seems to add packages to the live image. I don't really want these packages to be running in the live image but if there's no other way I suppose it will do.

---

