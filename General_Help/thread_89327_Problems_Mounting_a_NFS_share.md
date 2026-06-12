---
title: "Problems Mounting a NFS share"
date: 2005-11-12
forum: General Help
---

### Post by Bastler007 on 2005-11-12
Hello,

every time I try to mount a nfs share there appeare an error in /var/log/messages says :  "nfs warning: mount version older than kernel" the mounted data makes some problems. This happens unter both ubuntu and kubuntu.
The Server runs well, I'm able to mount under SuSE, PCBSD or debian. Only (K)ubuntu makes the problems
I've installed ubuntu three times but the problems stay.
Can somebody help me get a new version of "mount" ?

Ciao
Werner

---

### Post by njwetsu on 2005-11-30
Has anyone given you a solution to your problem yet?  If so, can you please share it with me.  I am having the same problem.   I have other Linux Distro's that are working fine, but Ubuntu breezy keeps giving me the errors.

---

### Post by bartenst on 2005-12-14
I am having the same problem. I cannot mount an NFS share :(

---

### Post by schilcha on 2005-12-14
I do get the same messages in /var/log/messages. Nevertheless, I can perfectly work with the nfs-filesystems -- I didn't even notice these messages before I took a closer look.

So, do you get additional messages, giving a reason, why mounting failed?

BTW:
I have tested with one NFS-server running SuSE 8.0 (very old at least) and one running Hoary.

---

