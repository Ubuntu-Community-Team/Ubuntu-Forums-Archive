---
title: "PB with icc on ubuntu7.10"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by drodney on 2009-02-13
Hi everyone,

I was trying to install icc10.1.008 on a 64-bit machine with ubuntu7.10.

Here is what happened:
After installation, the test sequence said that it could not find the librarie libstdc++.so.5.

From the webpage
([http://software.intel.com/en-us/articles/performance-tools-for-software-dev](http://software.intel.com/en-us/articles/performance-tools-for-software-dev)
elopers-installing-and-using-intel-compilers-for-linux-on-ubuntu-linux/)
I read that for ubuntu7, one need two libraries libc6-dev-i386 and
g++~multilib. I checked on the computer that neither were installed. I then went to the following page ([http://packages.ubuntu.com/dapper/libc6-dev-i386](http://packages.ubuntu.com/dapper/libc6-dev-i386)) to download the first library. I used a repository site
(ubuntu.cs.utah.edu/ubuntu) to obtain the package that was opened by a package manager called by the web browser. It said that it had dependencies on gcc-4.2 and cpp-4.2 and gcc-4.2-base. I tried  to install them successively and at some point, the package manager said that it could not install the library because dependencies were broken and that I should use 'apt-get install -f' instead. I did so and
obtained a long list of packages to be removed and the message that I
should not do so unless I knew exactly what I am doing, which is clearly not my case.

Can someone help me clean that mess?

Thanks,

---

### Post by lemming465 on 2009-02-14
Does *apt-get update; apt-get install build-essentials; apt-get upgrade --fix-broken* improve things any?

---

