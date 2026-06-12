---
title: "Touchpad goes haywire on an XPS M1530 laptop."
date: 2009-01-23
forum: Hardware
---

### Post by CodyK46 on 2009-01-23
Almost every Linux distro I've tried has the same problem. I know it's a common problem. Anybody know any good fixes to get my touchpad to work in ubuntu?

Also, it works just fine when I plug in a mouse.

---

### Post by pablopancho on 2009-01-23
Yeah, it's pretty easy. Open terminal and type: 
```
sudo gedit /boot/grub/menu.lst
```
You need to find kernel line and add "i8042.nomux=1". This should look similar to this:
```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		c7917b95-9265-4065-9d79-295d28196523
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c7917b95-9265-4065-9d79-295d28196523 ro quiet splash [COLOR="Red"]**i8042.nomux=1 **[/COLOR]
initrd		/boot/initrd.img-2.6.27-11-generic
quiet
```

You must modify the menu.lst file everytime a new kernel is installed or you can set i8042.nomux=1 in default options in menu.lst:
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash [COLOR="Red"]**i8042.nomux=1**[/COLOR] vga=789

```
Note that some values my vary in your case, this is just an example.

---

### Post by damis648 on 2009-01-23
Actually, a better solution is to add it to the defoptions so that a kernel update won't mess up your trackpad again. Open a terminal and do the following:
```
gksudo gedit /boot/grub/menu.lst
```
and find (Ctrl+F) 'defoptions'. It will take you to a section looking something like this:
```
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
```
modify the second line (the one with only one #) to look like this
```
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash i8042.nomux=1
```
Now you can save and close that. Now all you must do is
```
sudo update-grub
```
Cheers!:popcorn:

---

### Post by CodyK46 on 2009-01-23
You guys are great. Will that work with any Linux distro? Or will I have to use some other command? Because I know each distro is different.

---

### Post by damis648 on 2009-01-24
Both of these methods should work on any linux distro, as long as they use GRUB (the bootloader Ubuntu uses) and grub is located in /boot. :popcorn:

---

