---
title: "Broken Kernel Update packages stilling floating around"
date: 2008-09-03
forum: General Help
---

### Post by SpaceMaster on 2008-09-03
So, after I'd already installed 2.6.24-21, my system again tried to download it and install it through the Update Manager.  The packages downloaded, and began the typical kernel-update process... and stopped.  

Now there are broken kernel packages sitting on my HDD.  Every time I install or remove software, or update, these broken packages try to install, and fail where they always do.

I tried ```
$ sudo dpkg --configure -a
```But it fails just the same.

The first time I tired ```
$ sudo apt-get autoclean
```It looked like it removed the messy packages.  But they're actually still there, and now this command does nothing with them.

I suppose I could try gnome-search-tool and pick out all the little pieces, but I'm afraid I'll damage the properly installed components of the 2.6.24-21 kernel which I currently run.

Can anyone offer some advice as how best to remove these shards of broken kernel intalation?

---

### Post by fooman on 2008-09-03
theres a pretty nice guide to cleaning up partially installed packages and other odds and ends over in the tutorials and tips section.  following those steps may help you clean that up....here it is:

[http://ubuntuforums.org/showthread.php?t=140920&highlight=cleanup](http://ubuntuforums.org/showthread.php?t=140920&highlight=cleanup)

---

### Post by kostkon on 2008-09-03
I would like to add that it seems that you have the *Proposed* repository enabled and so you have installed a testing/unstable kernel. The *Proposed* repository is only for people who want to test packages before they are officially deployed as an update and in some cases these packages cause problems.

The current kernel version for 8.04 is *2.6.24-19.41* and not *2.6.24-21.x*.

Thus, if you don't want this to happen again, you should disable this repository (from *System -> Administration -> Software Sources*, in the *Updates* tab).

---

### Post by SpaceMaster on 2008-09-04
The issue, however, was not a malfunctioning sofware component, nor the repository from which I downloaded it.  Instead, the issue was that after the initial successful install, the kernel still appeared on updates.  I mistakenly overlooked this when installing, and the install broke *because 2.6.24-21 was already there*.

---

