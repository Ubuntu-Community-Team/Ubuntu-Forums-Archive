---
title: "boot directly from an iso using grub2?"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by pythonscript on 2009-10-26
Can anyone tell me how to set up my /boot/grub/grub.cfg file to boot directly from an iso stored on my root partition? I found something online that talked about adding this to the file:
```

menuentry "Ubuntu 9.04 Live" {
  loopback loop (hd0,3)/boot/ubuntu-9.04-desktop.iso
  linux    (loop)/boot/ubuntu-9.04-desktop.iso isofrom=/dev/sda1/boot/ubuntu-9.04-desktop.iso boot=live quiet vga=791 noeject noprompt
  initrd   (loop)/boot/ubuntu-9.04-desktop.iso
}
```but I'm not sure how I would go about adding that to the file... because a) I read that I'm not supposed to directly update that file itself ( I actually read this in the file itself!), but rather use configuration scripts, and b) I have no idea where in that file I should place that code segment if I *did* edit it directly. Any help with either the code itself or how/where to edit it would really be appreciated. Thanks!

---

### Post by oldfred on 2009-10-27
Here is a how to:
**HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2  **

[http://ubuntuforums.org/showthread.php?t=1288604&highlight=iso+grub2](http://ubuntuforums.org/showthread.php?t=1288604&highlight=iso+grub2)

---

### Post by kagashe on 2009-10-27
> **pythonscript said:**
> but I'm not sure how I would go about adding that to the file... because a) I read that I'm not supposed to directly update that file itself ( I actually read this in the file itself!), but rather use configuration scripts, and b) I have no idea where in that file I should place that code segment if I *did* edit it directly. Any help with either the code itself or how/where to edit it would really be appreciated. Thanks!
Put the code in /etc/grub.d/40_custom file then update with 'sudo update-grub' and the menu entry gets written to /boot/grub/grub.cfg

I think you need to change the code. Read it on [Ubuntu Community Docs]("https://help.ubuntu.com/community/Grub2#Booting%20an%20ISO").

kagashe

---

