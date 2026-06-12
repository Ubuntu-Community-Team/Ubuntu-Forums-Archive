---
title: "Recent updates for 9.10"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by kennethtb on 2009-11-12
Hi we have had quite a few updates recently for 9.10 both recommended and priority ...
today for instance I received updates for Firefox amongt others so do any of these updates fix any of the problems shown in this forum? and can anyone tell me where to find installed updates within my system.

---

### Post by jerrrys on 2009-11-12
this what your looking for?

[http://ubuntuforums.org/showthread.php?t=1190143](http://ubuntuforums.org/showthread.php?t=1190143)

---

### Post by fbugnon on 2009-11-12
Hi,

As updates usually fix problems, chances are the recent updates are somehow related to problems discussed in this Forum.

If you want to know exactly what a specific update brings to you, you can check it on the package description.  Either in the Update Manager (or with Synaptic if you rather use it) you can verify a brief description of the update you are about to install and it will tell you what changes are made (improvements, fixes, new features) from the previous version.

For installed updates, either check the Synaptic History, as explained in the link provided in the post above, or check for the file ```
var/log/apt/term.log
``` using gedit, nano or any other text editor of your choice.

---

### Post by markbuntu on 2009-11-12
There is always a very large number of updates soon after release as the system gets installed on a wider range of hardware than provided by the many alpha and beta testers. 

I see lots of problems reported in the forums and no bug reports on them at launchpad. The devs do not hang out on the forums so the only way they know about problems is through bug reporting at launchpad.

---

