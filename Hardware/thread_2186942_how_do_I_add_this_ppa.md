---
title: "how do I add this ppa?"
date: 2013-11-10
forum: Hardware
---

### Post by necbot on 2013-11-10
I'm trying to troubleshoot a bug between xserver and my TV and I was told try using the latest kernels and that Ubuntu has a drm-intel-experimental ppa with the latest code from drm-intel-nightly.  Where is this ppa?  I found this...

[http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/)

But usually when I add a ppa it is from launchpad and I add it by typing sudo apt-add-repository <ppa link here>.  How do I add this repository?  Do I put it in my /etc/apt/sources.list?

---

### Post by sanderj on 2013-11-10
Based on [https://wiki.ubuntu.com/Kernel/MainlineBuilds#Installing_Mainline_Kernels](https://wiki.ubuntu.com/Kernel/MainlineBuilds#Installing_Mainline_Kernels) I would conclude you have to install it manually. So no automagic like with a (real) PPA.

Pity. Based on the word "PPA" I had expect you could just add an URL, like described here:
[https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab) ?  

Oh, wait: am I confusing "mainline" and "PPA"?

Found this too: [https://github.com/medigeek/kmp-downloader](https://github.com/medigeek/kmp-downloader)

PS: this looks very abandoned: [https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)

---

### Post by necbot on 2013-11-10
Yeah, I think it was meant to be installed manually.  I found that same link you posted, the one pointing to wiki.ubuntu.com and followed those instructions.  All I really wanted to do was try the latest drm-intel-nightly kernel so I downloaded the three packages from here...

[http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/)

I installed them and the new kernel appeared in the GRUB menu and booted just fine.  It threw me because I'm used to adding a ppa using the method I descibed in my OP.

---

