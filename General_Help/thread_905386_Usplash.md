---
title: "Usplash?"
date: 2008-08-30
forum: General Help
---

### Post by 311005901 on 2008-08-30
Ok. I've been searching on the forums, but I keep getting confused.
How do I turn this off (picture attached)? I want to go into "quiet mode" I think?

I'm not sure what files I need to edit. I just want a black screen when it loads. I don't really want the Ubuntu logo. Thanks for the help!
[IMG]http://farm3.static.flickr.com/2023/1696867535_7e613dbf72.jpg[/IMG]

---

### Post by Vivaldi Gloria on 2008-08-30
Press ALT+F2 and start

```
gksudo gedit /boot/grub/menu.lst
```

Find the kernel	line which belongs to kernel you boot and change the end of it to

```
kernel		/boot/vmlinuz-2.6.??-??-generic root=UUID=??? ro [COLOR="Blue"]quiet nosplash[/COLOR]
```

Restart.

This will get rid off the ubuntu logo but you'll see the boot messages. You cannot get a completely black boot unless you design a black splash image yourself.

---

### Post by Zorael on 2008-08-30
Instead of the above, I suggest modifying the "default boot options" section of said /boot/grub/menu.lst file, to make the changes carry when you update kernels.

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=**ro quiet nosplash**
```
Then enter the following in a terminal.
```
$ sudo update-grub
```

And yes, to get a completely black startup you'd need to create your own black splash. It's not *that* difficult but there's some knowhow needed. :>

---

### Post by Vivaldi Gloria on 2008-08-30
> **Zorael said:**
> Instead of the above, I suggest modifying the "default boot options" section of said /boot/grub/menu.lst file, to make the changes carry when you update kernels.

Yeah, that's a better idea.

---

