---
title: "How to get back to kernel 2.6.17?"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by wisdomseeker2 on 2009-02-27
I've got two computers running with Ubuntu here: one is an eeePC 701, and the other one is a VIA C7. And I've installed Ubuntu 8.04 on both of them. I particularly like to C7 because it is silent and has no mechanically moving parts.

For quite a while, both of them have become annoyingly slow. Especially with increasing memory load, the system performance has become totally unacceptable, especially the latency for interactive use. (No, and I don't want to upgrade to a Quadcore 64GB main memory machine.)

This problem has been identified a couple of month ago, already, and has been described at various places. E.g. [http://it.slashdot.org/article.pl?sid=09/01/15/049201](http://it.slashdot.org/article.pl?sid=09/01/15/049201), [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131094](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131094), [http://bugzilla.kernel.org/show_bug.cgi?id=12309](http://bugzilla.kernel.org/show_bug.cgi?id=12309), [http://bugzilla.kernel.org/show_bug.cgi?id=7372](http://bugzilla.kernel.org/show_bug.cgi?id=7372). This is going on for a couple of months now, and it doesn't seem to be resolved quickly. Apparently, the problem was introduced by kernel version 2.6.18.

So, I'd like to get back to kernel 2.6.17. Is there a way to do this with either Synaptic or apt-get? Synaptic only shows me packets like "linux-image-2.6.24-etc...". The menu option Package->Force Version if grayed out. Has anybody successfully switched back to the working kernel?

Thanks for your help in advance.

---

### Post by regala on 2009-02-27
> **wisdomseeker2 said:**
> 

...

So, I'd like to get back to kernel 2.6.17. Is there a way to do this with either Synaptic or apt-get? Synaptic only shows me packets like "linux-image-2.6.24-etc...". The menu option Package->Force Version if grayed out. Has anybody successfully switched back to the working kernel?

Thanks for your help in advance.

Well, these kernels are not available in Intrepid nor Hardy. You can try and edit your /etc/apt/sources.list file to add the apt line for Gutsy to make them available. Yet, some services (like udevd) might not work well with a <2.6.18 kernels (frankly I don't know whether or not). In that case, you may have to downgrade to Gutsy.

---

### Post by stchman on 2009-02-27
If memory serves me correct, 2.6.17 was the kernel Edgy used.

---

### Post by regala on 2009-02-27
> **stchman said:**
> If memory serves me correct, 2.6.17 was the kernel Edgy used.

ouch ! thanks for the check. :)

---

### Post by tbastian on 2009-02-27
If you really don't want to downgrade distributions, you could always try downloading and compiling your own kernel. It can be difficult, but the bonus is if you screw it up, you can just boot the latest working kernel.

if you're interested you can download it by looking in the kernel.org archives and there are quite a few tutorials on the web about compiling them.

The only disclaimer is: I'm not 100% sure about how well running a newer distro on a dated kernel would work.

---

### Post by regala on 2009-02-27
> **tbastian said:**
> If you really don't want to downgrade distributions, you could always try downloading and compiling your own kernel. It can be difficult, but the bonus is if you screw it up, you can just boot the latest working kernel.

if you're interested you can download it by looking in the kernel.org archives and there are quite a few tutorials on the web about compiling them.

The only disclaimer is: I'm not 100% sure about how well running a newer distro on a dated kernel would work.

well, if he HAS to downgrade due to incompatibilities/inconsistencies between udevd/kernel/sysfs, he can see it by installing the Edgy kernel and booting it. If it's poorly compatable, he will have to use the whole Edgy release anyway. :)
Nothing is easier than installing the edgy kernel
1) Edit /etc/apt/sources.list or use the Software Sources Utilities in the System panel tab to add the Edgy sources.
2) Update with aptitude update if you edited by hand your sources.list file.
3) With any package manager install the package you need, which will not depend on anything in Edgy (it would be absurd otherwise)
4) Boot it.

The presence of the Edgy sources will never force a downgrade to Edgy, by the way, you must edit /etc/apt/preferences to set the correct priority/pin values (see man apt_preferences for information on how to do it)

---

