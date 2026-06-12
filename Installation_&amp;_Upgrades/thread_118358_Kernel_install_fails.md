---
title: "Kernel install fails"
date: 2006-01-16
forum: Installation &amp; Upgrades
---

### Post by tthkbw on 2006-01-16
I have a sempron processor on an ECS motherboard.  System runs Live CD of 5.10 without problem, so I decided to install to the primary master IDE hard drive.

Install proceeds to the point where, when installing the base system, it prompts for the Kernel to install and gives three options:

1. Linux-386
2. linux-image-386
3. linux-image-2.6.12-9-386

I have tried each of these options, but the install errors out at this point.  

I left the original install unattended and when I came back, it was at the point of asking me for time zones and user name and password.  I completed this process, then it asked me for multi boot options and I selected grub and multi boot with windows on another hard drive.  But when I rebooted, the boot failed on the hard drive that ubuntu was installed to.

Any ideas?

---

### Post by WoodPost on 2006-01-16
I'm just curious, what are the differences in these kernels?

---

### Post by tthkbw on 2006-01-16
I have no idea what the kernel differences are.

If I repetively try the install, sometimes the kernel installs, but in every case, when the install apparently completes successfully, the subsequent boot process fails--that is, on boot, the machine reports a boot device failure when it tries to boot from the linux hard drive.

---

