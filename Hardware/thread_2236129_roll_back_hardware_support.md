---
title: "roll back hardware support"
date: 2014-07-24
forum: Hardware
---

### Post by ac98521 on 2014-07-24
Hi, I've clicked an install button in the top right corner of the update manager. It's effect sucks. I want to roll back. How can we revert the changes??? This is ubuntu 12.04

---

### Post by bapoumba on 2014-07-25
Is this what you are talking about : [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1328264](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1328264) ?

---

### Post by ac98521 on 2014-07-25
what is that trusty thing please?

---

### Post by bapoumba on 2014-07-25
A wild guess from me trying to understand what you were talking about, what you did upgrade, what does "suck" mean. Most of the time, a software upgrade cannot be reversed because the package managers do not do that. So if you are not talking about the hardware enablement stack that is currently causing many issues to many people, what did you upgrade and what are the precise symptoms you are experimenting ?

---

### Post by ac98521 on 2014-07-25
well an install button appeared here..... on the upper right corner. It said it had to do with the hardware support or something. I thought it would help since it said it was an "upgrade" but all it did was slow down the startup and weaken the volume of my computer (ASUS K40IJ)
[ATTACH=CONFIG]255032[/ATTACH]

---

### Post by bapoumba on 2014-07-26
Here are a few links to read :
[http://ubuntuforums.org/showthread.php?t=2236096&page=2&p=13082770#post13082770](http://ubuntuforums.org/showthread.php?t=2236096&page=2&p=13082770#post13082770)
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964)
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

Your options are : keep running Precise, but reinstall the 12.04.1 image not to get the HWE current bug, or install Trusty (also a LTS), or try to see where your current problems are, but it may not be easily fixable. If I understand correctly, your machine does boot (no video problems ?), but slowly and your sound is weak. When I search with your model, all I get are older info for older releases. You may have to file new bugs about these.

---

