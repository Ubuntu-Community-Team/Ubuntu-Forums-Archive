---
title: "qemu caching question"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by anystupidname on 2009-06-14
I've been testing multiboot USB thumb drive configurations a lot lately using qemu. (I realize this isn't the most realistic way to test but it DOES save me time as far as menu testing and such) 

My question: why does it seem almost always necessary to unmount and remount the thumb drive between changes for qemu to recognize them? To be more clear, I'll boot the thumb drive with qemu "qemu -hda /dev/sdc" and it will show a syslinux or isolinux or grub4dos menu. Then I shut down the VM. I make some modification to menus. I fire up the VM again and the changes won't be reflected. I shutdown the VM, unmount and remount the thumb drive and fire up the VM and the changes are in place... I tried deleting the "virtual-something" folder in /tmp/ which I thought might be some sort of qemu cache but that doesn't help. Is there a different cache I should be deleting? Is there a different qemu command line I can use to force not reading from cache?

Thanks for any advice!

---

