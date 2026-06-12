---
title: "Linux Image package probelm"
date: 2008-12-26
forum: Installation &amp; Upgrades
---

### Post by rrbrandolino on 2008-12-26
I am suddenly having issues w/ my NVIDIA card -- no display, even though  the right drivers are installed, the xorg.conf file is known to work and the Xorg log files look fine. 

After some digging, I noted that the restricted module kernel versions for nvidia don't match the installed kernel. Linux 2.6.26-10 is installed ( Intrepid system ). The linux-image version shows installed in adept for linux image 2.6.26-11 but for unknown reasons no 2.6.26-11 kernel is available in /boot. I thought about using apt-get to reinstall the kernel image, but apt-get lists dozens of packages that will be uninstalled in the process. many of which I know I need.

Any suggestions short of a total reinstall??

---

