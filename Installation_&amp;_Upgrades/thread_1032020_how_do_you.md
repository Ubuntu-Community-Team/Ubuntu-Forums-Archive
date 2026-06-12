---
title: "how do you"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by banter25 on 2009-01-05
dump a security update from the update manager?  I keep getting the same error,

 E: /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_amd64.deb: subprocess pre-installation script returned error exit status 1

when i try to install it on Hardy Heron and someone told me that it is only for intrepid.  It is linux-image-2.6.27-7-generic (sure you could tell that by the string) so I just want it to go away, but it keeps coming back like a perfectly thrown boomerang....lol.

---

### Post by cariboo on 2009-01-06
You can go to System--Administration-->Synaptic-->Edit-->Fix Broken Packages, and completely remove the package. Once you have done that, in a terminal type:

```
sudo apt-get autoremove
```

This will remove no longer needed dependencies and also clean out the archived packages in /var/cache/apt/archives.

just to be sure I would also run in a terminal:

```
sudo apt-get clean
```

Jim

---

