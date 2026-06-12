---
title: "ATI Radeon Installation Issues in Ubuntu?"
date: 2012-05-16
forum: Hardware
---

### Post by vj41 on 2012-05-16
I am trying to install driver for my ATI Radeon 5650 graphics card on my  Ubuntu 12.04 LTS OS. However, i am always facing the same problem,i  execute the following command: sudo sh -f  amd-driver-installer-12-4-x86.x86_64.run --buildpkg Ubuntu/precise It  gives the following error: Created directory fglrx-install.8TgIUg  Verifying archive integrity...Error in MD5 checksums:  5e64eb7059c9a93a48f9e038cbad61a2 is different from  57a5ec86eb8a00e0ec4710e570c1531c What should i do... Please help me  out....

---

### Post by steeldriver on 2012-05-16
have you tried just downloading a fresh copy of the file?

---

### Post by vj41 on 2012-05-16
Yeah... Twice... I have checked all the questions related to this in the forum but none is working for me...

---

### Post by vj41 on 2012-05-17
I was able to resolve this issue by System->Additional Hardware and installing the driver from there. This driver was the post release driver which doesn't have support for kernal 3.2. The error may be because of that. I am not sure though.... :)
Thanks for your help...

---

### Post by typhoon_tip on 2012-05-17
Got the same problem several times while attempting to download with Chrome or an accelerator.

Use WGET to download again, and it will work !

---

