---
title: "update screwed it !!"
date: 2008-07-13
forum: General Help
---

### Post by ettercap on 2008-07-13
i updated ubuntu 8.04...then a dialog box came which asked somthing about menu.lst ...
i set it to : apply the new one
after the restart ubuntu started up in low-graphics mode...
and  i couldn't see any hardware drivers enabled...

what should i do ???

---

### Post by overdrank on 2008-07-14
> **ettercap said:**
> i updated ubuntu 8.04...then a dialog box came which asked somthing about menu.lst ...
i set it to : apply the new one
after the restart ubuntu started up in low-graphics mode...
and  i couldn't see any hardware drivers enabled...

what should i do ???

Hi and if you altered the grub menu list then you may be booting into the wrong kernel. When booting and at the grub make sure you are using the latest kernel and you may check your grub menu list and check the default is 0.   ```
gksu gedit /boot/grub/menu.lst
```
Example
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

---

### Post by ettercap on 2008-07-16
the default value is set to 0..

what else should i edit in that.

---

### Post by Cannaregio on 2008-07-16
> **ettercap said:**
> the default value is set to 0..

what else should i edit in that.

You should have, somewhere in the menu.lst, something like this:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.

default		0
```

And to this "default 0" should correspond something like this in the "zero" (id est, first) position of the kernel list:

```

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=[COLOR="Blue"]long_alphanumeric_sequence[/COLOR] ro splash verbose 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```

edit your menu.lst with

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by overdrank on 2008-07-16
> **ettercap said:**
> the default value is set to 0..

what else should i edit in that.

Ok then what is the model of the graphics card?

---

### Post by ettercap on 2008-07-18
its an NVIDIA M GS 128 MB graphic card...earlier i had restricted drivers on it...

---

### Post by overdrank on 2008-07-18
> **ettercap said:**
> its an NVIDIA M GS 128 MB graphic card...earlier i had restricted drivers on it...

Could you post the output of the command ```
lspci
``` this will identify your model and then you may search if you need the nvidia-glx or glx-new driver. As I am getting off line and will not be able to help until tonight. :)

---

