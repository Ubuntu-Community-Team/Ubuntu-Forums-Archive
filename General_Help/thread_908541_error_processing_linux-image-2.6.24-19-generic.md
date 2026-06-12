---
title: "error processing linux-image-2.6.24-19-generic"
date: 2008-09-02
forum: General Help
---

### Post by 4Play on 2008-09-02
Hello, recently every time I install something via apt-get (new package or updates) I get an error at the end. Inoirder to fix it I tried to run 
> sudo dpkg --configure -a
but I got the exact same error I get with apt-get

> 
sudo dpkg --configure -a
Setting up linux-image-2.6.24-19-generic (2.6.24-19.41) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.24-19.36 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.24-19.36 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.24-19-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.24-19-generic


I am not using a seprate boot partition (so the problem is not because of lack of space) and I reinstalled grub (sudo grub-install hd0) just to be sure because I read somewhere that this could be grub related.

I recently added the rootflags=data=writeback option to the kernel...but im not sure this could cause problems...

here is my menu.lst (the part that matters, anyway)

> title		Ubuntu
root		(hd0,6)
savedefault
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5cf30022-9385-430e-a102-97aa732ce546 ro quiet splash rootflags=data=writeback i8042.nomux=1
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

any ideas on how to fix this?

Thanks for any help :D

---

### Post by 4Play on 2008-09-05
fixed this by editing /sbin/update-grub

sudo gedit /sbin/update-grub

change the #!/bin/sh to #!/bin/bash

sudo apt-get dist-upgrade

worked....no idea why this started happening all of a sudden, but it's working now.

---

