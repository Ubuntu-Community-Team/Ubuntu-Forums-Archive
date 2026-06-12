---
title: "Move Wubi to Virtual Machine"
date: 2008-10-12
forum: General Help
---

### Post by PulpDood on 2008-10-12
Hi, I was just wondering, is it possible to take my Wubi installation and use it on say VirtualBox or VMWare so I could use Ubuntu at the same time as windows?

---

### Post by mikedep333 on 2008-10-12
Hey,

I am interested in this too. What I do know is that there would be two steps:
1. Copying the contents from the filesystem image for the wubi install to a virtual machine's hard disk image.
2. Adapting the bootloader and the kernel for this hardware change.

There probably isn't anyway to automate this yet. But keep in mind that if you create a new virtual machine, you can always copy over your home folder (/home/username) with all of its hidden files from wubi to the VM. This way, unless you've customized your system in depth, you will have all your documents and settings (and any programs you've installed to your home folder.)

BTW: Welcome to the forums.

---

### Post by ago on 2008-10-13
1. VMs should be able to access raw filesystem images such as ubuntu/disks/root.disk
2. The issue is mostly how to get the VM to access boot which is an ntfs folder (ubuntu/disks/boot) mountbinded within Ubuntu. You could have a second VM disk with grub + /boot, synced from time to time with the /boot dir.

---

