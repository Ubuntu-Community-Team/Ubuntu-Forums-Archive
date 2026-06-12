---
title: "kernel and multimedia keys"
date: 2009-01-31
forum: Hardware
---

### Post by terry_gardener on 2009-01-31
i have recently upgraded to intrepid and my Microsoft wireless keyboard 3000 multimedia keys didn't work at all. 

after checking the following site i downloaded and installed the patch kernel. 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/281993](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/281993)
it now works. 

when ever i start the pc it is asking to upgrade the kernel, if i do this will it break the multimedia keys again, if it will break it again how do i stop it for searching for kernel upgrades. 

Thanks

---

### Post by dodongo on 2009-04-18
> **terry_gardener said:**
> i have recently upgraded to intrepid and my Microsoft wireless keyboard 3000 multimedia keys didn't work at all. 

after checking the following site i downloaded and installed the patch kernel. 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/281993](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/281993)
it now works. 

when ever i start the pc it is asking to upgrade the kernel, if i do this will it break the multimedia keys again, if it will break it again how do i stop it for searching for kernel upgrades. 

Thanks

Hi Terry -- I believe your multimedia keys should be working now.  I experienced the same issues, but for Intrepid and Jaunty a fix has been committed.  My keys now work properly!  If yours don't yet, I'd run a package update in Syaptic and see if that doesn't help.

---

