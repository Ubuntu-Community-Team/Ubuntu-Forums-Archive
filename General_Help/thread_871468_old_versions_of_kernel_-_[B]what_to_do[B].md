---
title: "old versions of kernel - [B]what to do??[/B]"
date: 2008-07-26
forum: General Help
---

### Post by toylas on 2008-07-26
Dear All,

I recently upgraded to Hardy. Right now I have 5 copies of kernel

/boot/vmlinuz-2.6.20-16-generic
/boot/vmlinuz-2.6.22-14-generic
/boot/vmlinuz-2.6.22-15-generic
/boot/vmlinuz-2.6.24-19-generic
/boot/vmlinuz-2.6.24-20-generic

My question is:

**Do I just delete the old copies and modify the /boot/grub/menu.lst file? Or is there some special utility or care to be used to remove the old copies??**

Thanks,
Toylas

---

### Post by logos34 on 2008-07-26
You should keep one other kernel (that you know works) besides the most recent.  So you change this section:

> ## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
**# howmany=2**


Then run

sudo update-grub

You can also remove the kernels completely by uninstalling them in synaptic (search 'linux-image')

---

### Post by toylas on 2008-07-27
Thanks logos34!! This is exactly what I was looking for. Thanks a lot!

---

### Post by SoftwareExplorer on 2008-07-27
So can this thread be marked as solved? ("Thread tools->Mark as SOLVED" or something like that).

---

### Post by lynlow on 2008-07-27
or you could try startup manager in synaptic i find that very usefull.

---

