---
title: "Help restoring grub"
date: 2008-10-25
forum: General Help
---

### Post by crhis on 2008-10-25
I had vista and ubuntu installed, then I tried installing another os. It worked fine, then restarted the computer. Before the grub menu came up, I got error 17. I then executed the following code from a ubuntu live cd

sudo grub

find /boot/grub/stage1

it gave me the output 
"find /boot/grub/stage1
  (hd0,1)"

Then I typed
root (hd0,1)

setup (hd0)

quit

It did not show any failures. Shouldn't it show more than just (hd0,1), being as I have 3 operating systems installed. 

When I boot up, the boot menu only shows vista and ubuntu. When I try and boot ubuntu it says

"error 17: cannot mount selected partition"

when I try and boot vista I get

"error 13: invalid or unsupported executable format"

when I try to boot to "other operating systems" I get 

"error 11: unrecognized device string"

The last one may have always been there. I have never tried it before.

Please help me get all three operating systems in the grub menu and have them boot.

---

### Post by geirha on 2008-10-25
Boot the ubuntu CD and mount your ubuntu partition at /media/disk/ then post the output of these commands
```

cat /media/disk/boot/grub/menu.lst
sudo fdisk -l

```

That should give us a proper overview

---

### Post by crhis on 2008-10-25
Sorry for not responding, I just decided to reinstall Ubuntu and grub along side it....

---

