---
title: "PCI SATA Card Compatibility"
date: 2009-05-18
forum: Hardware
---

### Post by electrosam on 2009-05-18
Hello
I have an old Pentium 3 850MHz desktop. It has 80GB HDD, 256MB RAM and Mercury motherboard. I want to use it as a server to share HDDs over network. Its motherboard doesn't hav SATA ports. I have got a PCI Sata card which is working fine with Windows. I have connected my 500GB SATA HDD to it. Now I want to install Ubuntu on the machine and use it as a server. So will ubuntu will idenitify the HDDs connected through PCI Card ? Please Help. Thanks.;)

---

### Post by logos34 on 2009-05-18
> **electrosam said:**
> I have connected my 500GB SATA HDD to it. Now I want to install Ubuntu on the machine and use it as a server. So will ubuntu will idenitify the HDDs connected through PCI Card ?

Chances are it will recognize the sata(s). Where you might have a problem is if, say, you were to install ubuntu on a sata...Everything will appear to go great--until you reboot, at which time ubuntu will be unable to see the pci card-connected sata drive...So I would suggest putting ubuntu on the internal 80 gb disk, and maybe make a separate /home or data partition during install on the 500 gb sata. (Or if ubuntu / must go on sata disk, you could make a small, separate /boot on the internal).

Here's how to [specify additional partitions]("http://www.easy-ubuntu-linux.com/ubuntu-installation-606-12.html") at installation time.

---

