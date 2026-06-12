---
title: "Non-raid SATA hard drive via raid card?"
date: 2008-11-10
forum: Hardware
---

### Post by kernalsanders123 on 2008-11-10
I recently purchased a VIA VT6421 SATA raid card. Under Windows, it installed fine, and I can read sata drives without difficulty. However, when  I boot an Ubuntu LiveCD, the card itself is detected, as it appears when I run lspci in the terminal. However, it cannot detect the drive that is attached to it. Searching on the forums and elsewhere, I was only able to find posts on how to set up raid on it, but I just want to be able to access the drive individually, like in Windows. Any insights on how I may be able to do this? Thanks a bunch!

---

### Post by valentt on 2009-11-29
I found the answer on how to make this VIA VT6421 card work on Ubuntu:

sudo modprobe sata_via

more details on my blog:
[http://kernelreloaded.blog385.com/index.php/archives/ubuntu-and-via-vt6421-pci-sata-howto/](http://kernelreloaded.blog385.com/index.php/archives/ubuntu-and-via-vt6421-pci-sata-howto/)

---

