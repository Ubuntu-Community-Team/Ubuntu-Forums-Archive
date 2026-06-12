---
title: "Installing GRUB on a floppy image"
date: 2007-07-09
forum: Hardware &amp; Laptops
---

### Post by Blazeix on 2007-07-09
Hi, I need to create a bootable floppy image for a virtual machine. My laptop does not have a floppy drive. I created a blank floppy image using 'dd', and I formatted it as a bootable vfat. Now I need to install grub on it. The normal command for physical floppies is 
>grub
root (fd0)
setup (fd0)
quit
how would I specify this for a floppy image? I have the image mounted under /media/floppy, and I'm not sure what would go in place of the (fd0). Is there some way to point it toward my image? Thanks.

---

