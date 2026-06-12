---
title: "How to upgrade to GRUB 1.97 released version"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by rajesh_shenoy on 2009-11-06
Hello:

I have GRUB 1.97~beta4 installed in my Ubuntu 9.10 Karmic Koala. How can I upgrade this to GRUB 1.97 released version? I have downloaded the source code tarball, but don't know the next steps. Any automatic way of updating it (i.e., without having to compile it, make it, etc.)?

Thanks in advance!

- Rajesh

---

### Post by rajesh_shenoy on 2009-11-10
OK. I did this myself. Steps:
1. Download the GRUB 1.97 released version tarball.
2. Extract.
3. Follow instructions in the file INSTALL. You'll need to install a bunch of make utilities.
4. Follow instructions here to install the new GRUB to MBR (basically "sudo grub-install /dev/sdX"): [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
5. The "update-grub" and "update-grub2" commands given in the site don't work. That's basically because they expect the file holding the user-modifiable GRUB configurations, "grub", to be in the folder "/usr/local/etc/default", whereas GRUB puts it in "/etc/default/". Hence you'll need to copy over the file to the former.
6. Run "update-grub".

Cheers!

---

