---
title: "dell xps m 1530 touchpad won't work"
date: 2008-07-27
forum: Hardware
---

### Post by chocolateforcoco on 2008-07-27
Hi, I'm a brand new ubuntu user and i've only used it once on a friend's computer. Basically though, i liked what i saw and decided to get it onto my laptop. 

I loaded it within vista, rather than creating a new partition. Everything seems to be working find, except my touchpad wont work at all. I connected a mouse to it through the usb, and that worked like a charm, but i primarily use the touchpad when im on the laptop but when i tried using it, it just started spazzing out and opening up random menus. 

Anything help would be great. Thanx

---

### Post by niglch on 2008-07-31
I had the exact same issue. To fix it open a terminal and get to your GRUB menu configuration file. ```
gksudo gedit /boot/grub/menu.lst
```
Next you need to add "i8042.nomux=1" to a few spots in this file.
```
kopt=root=* ro **i8042.nomux=1**
...
defoptions=quiet splash **i8042.nomux=1**
...
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8b094197-a280-44ce-9f1f-0355ae2541ef ro quiet splash **i8042.nomux=1**
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

```
Just look for those lines and add in the bolded text. It worked great for me and my touchpad no longer jumps around or doesn't respond. Another good topic too look at is [this one]("http://ubuntuforums.org/showthread.php?t=695420&highlight=dell+xps+1530") where the issue is discussed more at length. Anyway I hope this helps.

---

### Post by chocolateforcoco on 2008-08-01
Are you sure thats correct. I was able to find the 

"defoptions=quiet splash i8042.nomux=1" 

but i couldn't find the other lines. I was able to find lines close, but not word for word the same. Any ideas?

---

### Post by elelias on 2009-01-20
Thanks! it worked great.

The lines may not be exact, since they change with the kernel version and so on, but it works anyway.

---

### Post by patrixion on 2009-04-01
Thank you niglch... adding **i8042.nomux=1** worked like a charm!  I'm back in business with a functional touchpad.

THANK YOU SO MUCH!

---

