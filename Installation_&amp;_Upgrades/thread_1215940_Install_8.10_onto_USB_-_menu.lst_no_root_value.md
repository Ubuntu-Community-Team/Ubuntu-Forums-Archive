---
title: "Install 8.10 onto USB - menu.lst no root value?"
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by jake.c on 2009-07-17
Hi there everyone,

I've decided to install ubuntu, but because Vista is playing up with my partitioning of the HD I have decided to install ubuntu onto my USB stick following this guide:

[http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)

The guide is using 8.04, whereas I am using 8.10. The problem comes when I have to edit the media/disk/boot/grub/menu.lst .

The guide shows:

> 
5. open menu.lst with vi (make a backup first!)

6. Go to line 130 (or somewhere in that area).
You will find a line looking like:
## ## End Default options ##
And underneath it you will find three entries pointing to your Ubuntu you just installed:
title         Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd1,0)
kernel     /boot/vmlinuz&#8230;&#8230;&#8230;
initrd       /boot/initrd&#8230;&#8230;.
quiet
(the above 5 lines repeat 3 times with slight differences)

[B]7. The magic trick is to change (hd1,0) into (hd0,0) for all these three entries.
[/B]Why? Booting from USB device makes your USB device hd0, in stead of hd1 at time of installation.
However, it seems that in 8.10, there is no root value:

> title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        d595c56d-b14b-4a05-b7f2-429e274a2914
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=d595c56d-b14b-4a05-b7f2-429e274a2914 ro ROOTFLAGS=syncio quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quietCould anyone help if they know what the problem is? Either I need to edit something else for 8.1, or I'm doing something wrong?

Thanks very much :)

---

### Post by konnorrigby on 2009-07-17
go to [http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)

---

### Post by Herman on 2009-07-17
You don't need to do anything. Ubuntu uses UUID numbers now instead of device numbering. Your USB will always have the same UUID, no matter what device number it happens to be given. That's what UUID numbers are for, to fix that problem. Just leave it how it is. :)

---

