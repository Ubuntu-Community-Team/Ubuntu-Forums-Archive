---
title: "Ubuntu upgrade failed."
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by adi.cricket on 2009-11-07
I made a mistake by not reading the upgrade guide and went for the upgrade w/o updating 9.04. During upgrading some errors were shown but system completed upgrade and I could see the changes. But the next time i started the computer, following errors were shown:

```
init:mountall-shell main process(750) terminated with status 127 
mountall start/starting

/:waiting for /dev/disk/by-uuid/09e...
/tmp:waiting for null
swap: waiting for UUID=43....
```

i checked /etc/fstab and tried mounting but failed
Please help

---

### Post by wilee-nilee on 2009-11-07
What is your goal here, do you want to pull off the stuff you want to save and do a fresh install? If you want to fix it, specific questions will get you answers. I suggest the save packages and do a fresh install so you get the ext4 upgrade and grub2. You can get daily builds of Karmic for the fresh install so you will have very little to update. Others may be able to help you fix it maybe but a fresh install of this release has been the general consensus.

---

### Post by adi.cricket on 2009-11-16
Thanks

---

