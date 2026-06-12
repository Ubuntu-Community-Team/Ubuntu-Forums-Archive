---
title: "enable FATX support in the kernel?"
date: 2008-09-14
forum: General Help
---

### Post by rajb245 on 2008-09-14
I want to be able to mount FATX drives and partitions on Ubuntu 8.10 (original XBOX's file system).  There are a few threads on this forum asking this question but no one has answered, and they are now read only and archived.

There are some kernel patches I found here:

[http://sourceforge.net/project/showfiles.php?group_id=54192&package_id=147485](http://sourceforge.net/project/showfiles.php?group_id=54192&package_id=147485)

I'm no guru, but I think that it goes something like this:
I would have to download the kernel sources in one of the versions matching the patches I found, patch the kernel, build/compile it, put the new kernel in the right place and do some grub configuration editing to get a system that can boot with a patched kernel.

Does anyone here know if this process would work?  The latest kernel patch I found in the link above targets 2.6.16, would this pose a problem since Ubuntu 8.10 runs on kernel 2.6.24.

---

### Post by Neo_The_User on 2008-09-14
Install kernelcheck 

[http://downloads.sourceforge.net/kcheck/kernelcheck_1.1.4-2_all.deb?modtime=1214853750&big_mirror=0](http://downloads.sourceforge.net/kcheck/kernelcheck_1.1.4-2_all.deb?modtime=1214853750&big_mirror=0)

Launch kernelcheck from applications menu on toolbar.

Click the arrow next to where it says "New Kernel Patch Options"

Click "Custom Patch"

Look at the top left corner of the window can click Program > Build new Kernel

download the patch of your choice or whatever works from the link you posted:

[http://sourceforge.net/project/showfiles.php?group_id=54192&package_id=147485](http://sourceforge.net/project/showfiles.php?group_id=54192&package_id=147485)

Tell kernelcheck to compile that patch you chose to the kernel.

Hope that helps.

---

### Post by rajb245 on 2008-09-14
Any tips on actually booting this kernel using grub? That is, what files are generated in the build process, where do I put them, and how do I update my grub configuration to alternately boot the new kernel?

---

### Post by Killtodie on 2008-10-25
will there be support for this in 8.10

---

### Post by icehouse on 2008-11-18
i hope... that would be awsome, support in 8.10

---

### Post by Yellow Pasque on 2008-11-18
> **Killtodie said:**
> will there be support for this in 8.10
I doubt it. Someone made a Launchpad bug for Ubuntu 8.04 and the developer responded that newer kernels won't support it (and marked the bug "Will Not Fix").

---

### Post by mtn on 2009-03-09
> **Neo_The_User said:**
> Install kernelcheck 

[http://downloads.sourceforge.net/kcheck/kernelcheck_1.1.4-2_all.deb?modtime=1214853750&big_mirror=0](http://downloads.sourceforge.net/kcheck/kernelcheck_1.1.4-2_all.deb?modtime=1214853750&big_mirror=0)

Launch kernelcheck from applications menu on toolbar.

Click the arrow next to where it says "New Kernel Patch Options"

Click "Custom Patch"

Look at the top left corner of the window can click Program > Build new Kernel

download the patch of your choice or whatever works from the link you posted:

[http://sourceforge.net/project/showfiles.php?group_id=54192&package_id=147485](http://sourceforge.net/project/showfiles.php?group_id=54192&package_id=147485)

Tell kernelcheck to compile that patch you chose to the kernel.

Hope that helps.

I would like to access an XBOX hard drive that I have plugged into my desktop pc. I followed the instructions above to the point where a second terminal window opens... I closed it down and then another window opened that displayed a tree view with tick-able boxes of things that could be added or left out of the kernel. At this point I was not able to add the downloaded Fatx patch. Any help with getting Fatx support going would be much appreciated.

---

### Post by www.rzr.online.fr on 2009-12-31
> **Temüjin said:**
> I doubt it. Someone made a Launchpad bug for Ubuntu 8.04 and the developer responded that newer kernels won't support it (and marked the bug "Will Not Fix").

do you have the link to the LP entry ?

-- 
[http://rzr.online.fr/q/xbox](http://rzr.online.fr/q/xbox)

---

