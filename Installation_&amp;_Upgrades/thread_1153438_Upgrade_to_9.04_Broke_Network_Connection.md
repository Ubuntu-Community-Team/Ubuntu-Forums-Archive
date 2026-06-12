---
title: "Upgrade to 9.04 Broke Network Connection"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by jcobban on 2009-05-08
I have just performed the network upgrade to 9.04 and after rebooting I have no network connectivity.

My /etc/network/interfaces file is unchanged from before the upgrade:

auto lo
iface lo inet loopback

auto eth0
iface etho inet dhcp

---

### Post by RedSingularity on 2009-05-08
Did you try reinstalling the drivers?  What is your "lspci" output?

---

### Post by jcobban on 2009-05-08
> **Shadow121 said:**
> Did you try reinstalling the drivers?  What is your "lspci" output?

Thank you for telling me about the lspci command.

I have resolved the problem, as evidenced by the fact that I am able to post this from my upgraded 9.04 system.

As a result of a failed attempt a few weeks ago to install a second copy of Ubuntu on a second partition of my hard drive GRUB was looking at the copy of /root/grub/menu.lst on the second partition, but the upgrade to 9.04 changed the copy of menu.lst on the first partition.  Copying menu.lst from the first to the second partition and rebooting resolved the problem.  I will have to delve into the GRUB commands to figure out how to point it back at the first partition.

---

### Post by RedSingularity on 2009-05-08
Glad you got it working:)

---

