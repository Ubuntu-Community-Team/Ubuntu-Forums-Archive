---
title: "Resize / without LiveCD"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by unknownmosquito on 2008-12-13
I need to resize my main partition (ext3) without using a LiveCD or LiveUSB. I have a no-optical-drive laptop running Linux Mint 5.0 (essentially Hardy) and I can't seem to locate my thumb-drive so it must be done either within the rescue mode or normal boot.

How can I do this?

Note I'm relatively comfortable using resize2fs and fdisk etc and I don't need to be limited to the GUI tools if I know it will work.

---

### Post by iaculallad on 2008-12-13
You CAN'T resize your main partition (Filesystem) when its mounted. It needs to be unmounted first before you could proceed resizing it, which means, you need to boot using a LiveCD.

---

### Post by unknownmosquito on 2008-12-13
I'm about 90% sure you're incorrect... I think you can do it with ext2online, in fact I have done it before on an LVM system; I didn't even have to reboot to update the system.. but I know it's a little different if you aren't using LVM + ext3, and are just using ext3.

---

