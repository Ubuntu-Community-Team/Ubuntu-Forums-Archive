---
title: "Nvidia + 18.04 Driver"
date: 2018-10-01
forum: Hardware
---

### Post by nshiell on 2018-10-01
**[SIZE=5]<<<Important Read this whole post, don't just paste commands into terminal!!!!!>>>[/SIZE]**

I just did a dist upgrade to move upto 18.04 (actually I am running KDE Neon but as it's based on Ubuntu I'm posting here for anyone that has the same problems).

After I did the update my Nvidia card didn't work
I had some output on one monitor only, with extremely slow performance.
I tried running

sudo ubuntu-drivers autoinstall

It didn't work, I think the specific driver version it installed was incomparable with 18.04.

I went and downloaded the driver version 390.87 from [https://www.nvidia.com/Download/driverResults.aspx/137276/en-us](https://www.nvidia.com/Download/driverResults.aspx/137276/en-us)
I elected not to build a DKMS module for it (not sure if that helped) but that worked.

So it seems for me like driver version 390 is the ONLY version that works on my combination of hardware and Ubuntu.

It seems like Nvidia drivers with 018.04 LTS support is a bit flaky.

---

### Post by Autodave on 2018-10-01
Glad that you got it working, but your problem may have been the way that you installed the Nvidia driver back in 16.04 or whatever you were running before 18.04.  If you install a driver other than those available in the repositories, they will never update themselves.  Installing from the repositories means that the driver will update normally.  Also, MANY problems can arise when upgrading from one release to another.  I have always found it quicker and easier to just backup everything (which you should routinely be doing anyway) and do a clean install.  I also only use the LTS releases.

---

