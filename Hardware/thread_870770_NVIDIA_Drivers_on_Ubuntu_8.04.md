---
title: "NVIDIA Drivers on Ubuntu 8.04"
date: 2008-07-26
forum: Hardware
---

### Post by null byte on 2008-07-26
Okay, so I installed Ubuntu 8.04 [Desktop] from the official Ubuntu CD.   I tried to install NVIDIA drivers, and I get:

> 
-> Kernel module compilation complete.
[B]ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s).
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.[/B]


Any help? I am trying to fix this for 2 hours, and nothing... what's wrong?

```
uname -r
```
```
2.6.24-19-generic
```

System is updated with the latest stuff.


Help me please :)

---

### Post by TenPlus1 on 2008-07-26
[http://ubuntuforums.org/showthread.php?t=733316](http://ubuntuforums.org/showthread.php?t=733316)

---

### Post by null byte on 2008-07-26
I'll check that.. hope it works.. I tried another stuff from here and none worked. I'll come back with a reply :)

---

### Post by null byte on 2008-07-26
Nope, same damn error. Please help, I'm getting mad.

**EDIT**: [http://ubuntuforums.org/showpost.php?p=3654614&postcount=11](http://ubuntuforums.org/showpost.php?p=3654614&postcount=11) worked! I tried for the 2nd time and it worked!

Can be closed :D Everyone having this problem, listen to that guy, he knows what says.

---

