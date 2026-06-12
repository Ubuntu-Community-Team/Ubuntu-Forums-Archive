---
title: "making dpatch problem"
date: 2005-03-27
forum: Hardware &amp; Laptops
---

### Post by arnieks on 2005-03-27
Hi, I am trying to get my orinoco based wireless cards in monitor mode.  It looks like I may need to patch the kernel source.  So I decided to install the 2.6.11 kernel and patch it with the orinoco-2.6.11-rfmon-dragorn-1.diff patch.
I was following the steps outlined in [http://www.ubuntulinux.org/wiki/KernelBuildpackageDetailedHowto](http://www.ubuntulinux.org/wiki/KernelBuildpackageDetailedHowto)
but I come unstuck at the point where I have to make a dpatch.
this is my command
 sudo dpatch patch-template -p "orinoco-2.6.11-rfmon-dragorn-1" "orinoco rfmon patch" < {pathto}orinoco-2.6.11-rfmon-dragorn-1.diff > debian/patches/orinoco-2.6.11-rfmon-dragorn-1.dpatch
this is the answer I get
bash: debian/patches/orinoco-2.6.11-rfmon-dragorn-1.dpatch: Permission denied

Now I take it this is some sort of limitation of sudo?
How do I get around it?
Thanks for your help
arnie

---

