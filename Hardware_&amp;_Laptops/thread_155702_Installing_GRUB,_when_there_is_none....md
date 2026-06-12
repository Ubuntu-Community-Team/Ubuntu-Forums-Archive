---
title: "Installing GRUB, when there is none..."
date: 2006-04-05
forum: Hardware &amp; Laptops
---

### Post by gappy on 2006-04-05
I am encountering a strange problem. I installed Kubuntu breezy on a machine with 2 hard drives, a 30GB IDE, and a 250GB SATA. GRUB was installed on the MBR of IDE disk, and the OS was put on the SATA disk. Recently, I had to remove the IDE disk, and with it GRUB. As a result, the system won't boot. I'd like to install GRUB on the one remaining disk. Questions:

 
[LIST=1]
[*]Can the system be saved? [I assume yes, but hey, asking doesn't hurt]
[*]Can I use the Ubuntu install CD? If I remember correctly, it allowed the user to install GRUB at some point. But can this still be done nondestructively?
[*]Is there anything one should be careful about?
[/LIST]

Thanks in advance!

---

### Post by hollywoodb on 2006-04-05
in my opinion, the BEST option is to use a livecd to boot, use console to chroot into your kubuntu system.

```

mount <path to kubuntu> <dir on livecd>
chroot <mountpoint> /bin/bash

```

then you should be at console, effectively within your kubuntu system.  then edit /boot/grub/menu.lst to reflect changes in your partitions/drives

one thing to keep in mind is your partitions.  if the only disk you have left is the SATA drive, than that drive will be (hd0) ... the first partition will be (hd0,0), second partition (hd0,1), etc etc.

once you're sure all that is correct, you should be able to run:
grub-install '(hd0)'
(or whatever drive is going to be bootable).

full instruction are available in the docs from [The GRUB Manual]("http://www.gnu.org/software/grub/manual/html_node/index.html#Top")


note that you will need to edit /boot/grub/menu.lst on your kubuntu install no matter what.  this is because grub reads this file to provide you with a boot menu.

---

### Post by Sutekh on 2006-04-06
You can also check out this wiki page

[Ubuntu Wiki - Recovering Ubuntu After Installing Windows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

Don't be fooled by the name, it restores GRUB using the Install CD or the Live CD.

---

### Post by Sutekh on 2006-04-06
Woh I double posted

:oops:

---

