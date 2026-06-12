---
title: "Does anyone know of a workaround for the Xsane scanner bug until it gets fixed?"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by fsando on 2007-04-21
Hi
I'm hit by the Xsane scanner bug, like [so many others]("https://bugs.launchpad.net/ubuntu/+source/sane-backends/")
Does anyone know of a possible workaround (other than booting into windows) until it gets fixed?

---

### Post by Argos_Bling on 2007-04-21
[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488)

This particular version of the bug contains 2 workarounds - using scanimage from the commandline or a shell script that "prods" the scanner to keep it awake whilst scanning happens. It also contains an explanation from the kernel team why they broke scanning for so many people so close to release. Unfortunately the kernel team have marked the priority as "low" (which as it is not a security issue I think means no fix until Gutsy) and the sane-backends part of the problem hasn't even been assigned to anyone to fix.

As far as I can see the upstream kernel developers marked USB_SUSPEND as "experimental", so the upstream SANE devs may hold off implementing changes from their side, in the hope that (maybe) a blacklist will be added to the USB_SUSPEND functionality. At the moment the two workarounds mentioned above are the only alternative to recompiling the kernel (and restricted modules) or using an older release.

It is very frustrating that hardware that has been 100% supported (just out-of-the-box plug and play) for a long time leaves you compiling kernels in Feisty. My Gentoo-using friends are finding my difficulties most amusing :(

---

### Post by fsando on 2007-04-21
Thanks for the reply.
I read through this thread and some other threads, I'm not sure I fully understand the workaround, I may try it later but I'm in windows right now - only because I need to scan - this will, of course, not work in a virtual machine :/.
It seems it's a problem limited to ubuntu. it seems that no one really know what's the cause, and apparently it is not even considered important - by the right people, that is. Of course, lots of unhappy scanner owners consider it quite important :).
In all, it does not look very promising.
Feisty is in some ways quite an improvement - but frankly, such an important hardware breakage doesn't look good.

---

### Post by matchstich on 2007-04-21
xsane just hangs when i try to use my epson 1200--using scanimage in command line--same result.

this scanner was a plug and play before the update.

---

### Post by noynac on 2007-04-21
Same problem here but with an Epson Perfection 3490. I do a lot of scanning and rebooting to Windows to do a scan is just too much. I went back to Edgy and will only upgrade when a fix is available.

---

### Post by fsando on 2007-04-22
Is there a way to vote for a specific bug?

---

### Post by autocrosser on 2007-04-22
I've been posting this workaround: [http://ubuntuforums.org/showthread.php?t=414474&page=2&highlight=scanner](http://ubuntuforums.org/showthread.php?t=414474&page=2&highlight=scanner)

My post is #15

I can verify that gscan2pdf works very well:guitar:

---

### Post by fsando on 2007-04-23
> **autocrosser said:**
> I've been posting this workaround: [http://ubuntuforums.org/showthread.php?t=414474&page=2&highlight=scanner](http://ubuntuforums.org/showthread.php?t=414474&page=2&highlight=scanner)

My post is #15

I can verify that gscan2pdf works very well:guitar:

Thanks - I tried your workaround, without success though. I've given details in the other thread.

---

### Post by matchstich on 2007-05-06
i saw this. wonder if it would help us . don't know which one of the updates caused xsane to quit working on my puter.

Maybe I can help someone as I game on this page with a similar
problem.
Note I use the 'Debian unstable' distro, but I think this can
help Ubuntu users too as Ubuntu is based on Debian.

Problem: 
Recently Xsane failed to detect my Epson Perfection scanner.

Fix:
The problem (for me) seems to be in the 'libsane
1.0.19~cvs20070421-1' package.
I downgraded this package with a manual install of
'libsane_1.0.18-6' from Debian testing and Xsane worked again.

My system:
- Debian unstable (well close enough to Ubuntu ;)
- Debian AMD64 kernel: 2.6.20-1-amd64
- Xsane: xsane_0.99+0.991-3_amd64

-- 
some usb_devices fault if usb_suspend enabled
[https://bugs.launchpad.net/bugs/85488](https://bugs.launchpad.net/bugs/85488)
You received this bug notification because you are a direct
subscriber
of the bug.

---

