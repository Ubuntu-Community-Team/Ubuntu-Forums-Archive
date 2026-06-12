---
title: "how to tell grub to make my Windows default boot system"
date: 2008-07-29
forum: General Help
---

### Post by gotix on 2008-07-29
I have installed Ubuntu 8.04. Now at the boot I have ubuntu set as the default system to boot

what is the easiest way to configure grub to set Windows as the default boot option?

---

### Post by hyper_ch on 2008-07-29
altering the grub conf (menu.lst) file and set it to boot windows

---

### Post by ad_267 on 2008-07-29
Go to applications - accessories - terminal.

Enter
```
gksu gedit /boot/grub/menu.lst
```

Change this
```
default		0
```
to
```
default		saved
```

and make sure there's a line that says
```
savedefault
```
under the windows entry. I think it should be there by default.

---

### Post by gotix on 2008-07-29
> **ad_267 said:**
> 
...

and make sure there's a line that says
```
savedefault
```
under the windows entry. I think it should be there by default.

it is ! worked flawlesly, thanks a lot !

---

