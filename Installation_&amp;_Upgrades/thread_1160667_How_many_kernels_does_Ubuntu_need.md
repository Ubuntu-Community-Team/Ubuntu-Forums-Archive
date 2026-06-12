---
title: "How many kernels does Ubuntu need?"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by ManyBeers on 2009-05-15
Running Ubuntu 8.04 on my laptop and i noticed there is a new kernel in software updates. I already have 2 on my boot menu 2.6.24-19 and 2.6.24-23 and this new one 2.6.24-24 which I havn't installed is recommended. Am I supposed to install all these kernels everytime an update presents itself? I don't want a whole bunch of them stacked up like cordwood taking up space for no reason. How many should I keep andd how do i get rid of the one's i don't want.

---

### Post by Kareeser on 2009-05-15
Updating to new kernels opens up new features for your computer, should you choose to install them. However, they are completely optional.

To remove old kernels, simple open synaptic and mark the old kernels for removal. They will remove themselves from the menu list automatically.

---

### Post by Dngrsone on 2009-05-15
You only need one kernel, but it's nice to have the last version available in case something's changed in the most recent one that affects on or more of your programs.  It doesn't happen often, but it does.

Generally, kernel updates solve security issues (holes or vulnerabilities) and improve the operation of the whole system, so I'd update.

Oh, removing old ones, apparently, are done by removing the kernel (linux-image-2.6.xx-xx-xxx) from synaptic and then running ```
sudo update-grub
```

---

### Post by ManyBeers on 2009-05-15
> **Dngrsone said:**
> You only need one kernel, but it's nice to have the last version available in case something's changed in the most recent one that affects on or more of your programs.  It doesn't happen often, but it does.

Generally, kernel updates solve security issues (holes or vulnerabilities) and improve the operation of the whole system, so I'd update.

Oh, removing old ones, apparently, are done by removing the kernel (linux-image-2.6.xx-xx-xxx) from synaptic and then running ```
sudo update-grub
```

Tha to both of you for the quick replies, and I think I will keep one kernel as a backup and dump the rest.

---

