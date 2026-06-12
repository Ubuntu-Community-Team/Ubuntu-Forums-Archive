---
title: "How to install kernel 2.6.28?"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by mikhmv on 2008-12-17
Hi, 
How can I find latest version of intrepid kernel?
and How can I install it by apt-get?

Thanks

---

### Post by taurus on 2008-12-17
System -> Administration -> Synaptic Package Manager -> Quick Search and type in **linux-kernel**.  It would show you all the kernels that are available from the repos.

---

### Post by mikhmv on 2008-12-17
> System -> Administration -> Synaptic Package Manager -> Quick Search and type in linux-kernel 
Found nothing.
How can i add intrepid kernel repository?

---

### Post by taurus on 2008-12-17
What kernel repo?

If you want to add a repo to your machine, you need to add it to the end of /etc/apt/sources.list.  _However_, adding a third party repo that you are not sure about could cause trouble for your machine so better be real careful with that.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by snowpine on 2008-12-17
Intrepid uses 2.26.27 and always will. It will never upgrade to 2.26.28 through Synaptic or Update Manager, unless (as taurus pointed out) you add some sort of third-party repo to your sources, which you should be very careful doing. :)

Can I ask why you need 2.6.28? Maybe there is a different way to accomplish that which you seek, without installing an unsupported kernel...

---

### Post by mikhmv on 2008-12-17
I want to install 2.6.28 because my wifi card (intell 5350) doesn't work under 2.6.27. 
[Thread on it]("http://ubuntuforums.org/showthread.php?t=1012839")

---

### Post by xebian on 2008-12-17
> **mikhmv said:**
> I want to install 2.6.28 because my wifi card (intell 5350) doesn't work under 2.6.27. 
[Thread on it]("http://ubuntuforums.org/showthread.php?t=1012839")

You can download it from the ubuntu package archives for jaunty, and then install using dpkg.  **[COLOR="Red"]However, it might complain of dependencies.  If you really must, I suggest upgrade to jaunty.[/COLOR]**

The kernel package name is **linux-image-2.6.xx-x-generic** not linux-kernel.

[COLOR="Red"]Don't forget I warned you of breakage.  Have fun.[/COLOR]

---

### Post by mikhmv on 2008-12-21
xebian
Thanks. I installed 9.04. and wifi now work.

---

### Post by davewantsmoore on 2009-01-04
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

---

