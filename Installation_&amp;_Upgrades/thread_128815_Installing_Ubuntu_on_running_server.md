---
title: "Installing Ubuntu on running server"
date: 2006-02-12
forum: Installation &amp; Upgrades
---

### Post by pwhiting on 2006-02-12
I'd like to install Ubuntu on a remote server that is currently running redhat. I don't want to reboot the server until Ubuntu has been put on one of the available partitions. Ideally I'd mount the iso on a loopback device, reformat the target partition (currently unused), put enough of a stage 1 install on that partition to support the rest of the install, chroot into that partition,  execute a command (commands...) to do the rest of the package installs, and then manually edit the esisting grub configuration to point to the new partition. All of this would be done remotely with no convenient access to the server, so I'd have to get everything right and hopefully verify the install prior to rebooting the box. Once reboot, the box would come up in Ubuntu.

This approach would have two advantages for me: 1) it would allow me to do the install on a remote box that I do not have console access to (risky, I know...) and  2) it would minimize the downtime to only be the period of time during which the box is rebooting.

Is there documentation somewhere that would help me understand the needed steps?

---

