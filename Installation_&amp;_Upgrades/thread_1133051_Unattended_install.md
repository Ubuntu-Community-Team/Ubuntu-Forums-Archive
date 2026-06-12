---
title: "Unattended install"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by cbox on 2009-04-22
Hi,

I have made some small changes to the isolinux.cfg which automates the installation of the servers with a kickstart file, but i would like to automate the installation of my application as well.

My thougth is to use the %post part of the kickstart, but i'm not sure about the file system at this point.

In the %post section i have some apt-get install's but would like to copy my application files into the file system.

After the reboot i would like the application installer to be initialized.

Can anybody point me in the right direction of doing this? :)

---

