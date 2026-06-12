---
title: "Grub Error 11 after update"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by DiWO on 2009-01-28
Hello there

After auto update I did few hours ago grub started to throw Error 11 at me :o

```
title		Debian GNU/Linux, kernel 2.6.27-11-generic
root		4715408b-0ef1-47f5-a2e2-51bf72cfb9c5
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=4715408b-0ef1-47f5-a2e2-51bf72cfb9c5 ro quiet splash vga=788
initrd		/boot/initrd.img-2.6.27-11-generic

title		Debian GNU/Linux, kernel 2.6.27-11-generic (recovery mode)
root		4715408b-0ef1-47f5-a2e2-51bf72cfb9c5
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=4715408b-0ef1-47f5-a2e2-51bf72cfb9c5 ro single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Debian GNU/Linux, kernel 2.6.27-9-generic
root		4715408b-0ef1-47f5-a2e2-51bf72cfb9c5
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=4715408b-0ef1-47f5-a2e2-51bf72cfb9c5 ro quiet splash vga=788
initrd		/boot/initrd.img-2.6.27-9-generic

title		Debian GNU/Linux, kernel 2.6.27-9-generic (recovery mode)
root		4715408b-0ef1-47f5-a2e2-51bf72cfb9c5
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=4715408b-0ef1-47f5-a2e2-51bf72cfb9c5 ro single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Debian GNU/Linux, kernel 2.6.27-7-generic
root		4715408b-0ef1-47f5-a2e2-51bf72cfb9c5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4715408b-0ef1-47f5-a2e2-51bf72cfb9c5 ro quiet splash vga=788
initrd		/boot/initrd.img-2.6.27-7-generic

title		Debian GNU/Linux, kernel 2.6.27-7-generic (recovery mode)
root		4715408b-0ef1-47f5-a2e2-51bf72cfb9c5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4715408b-0ef1-47f5-a2e2-51bf72cfb9c5 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Debian GNU/Linux, kernel memtest86+
root		4715408b-0ef1-47f5-a2e2-51bf72cfb9c5
kernel		/boot/memtest86+.bin
```

I normally had only 27-7 kernel and it wasn't labeled "Debian GNU/Linux" None of them work atm Error 11 all the way. 

Anyone have any ideas what causes this? As if I fix this up and after update it drops dead again that wouldn't be anything I'd be looking forward to :D


Edit:

I'm not asking how to fix it as its just replaced and wrong grub menu. Just wondering why this happened.

---

### Post by caljohnsmith on 2009-01-28
How about changing all the "root" lines to "uuid" instead similar to:
```
title		Debian GNU/Linux, kernel 2.6.27-11-generic
[COLOR="Blue"]uuid[/COLOR]		4715408b-0ef1-47f5-a2e2-51bf72cfb9c5
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=4715408b-0ef1-47f5-a2e2-51bf72cfb9c5 ro quiet splash vga=788
initrd		/boot/initrd.img-2.6.27-11-generic
```
And to prevent that from happening again, I would recommend changing the "groot" line to be:
```
# groot=4715408b-0ef1-47f5-a2e2-51bf72cfb9c5
```
Then I think you should be all set, but let me know if you run into any problems.

---

### Post by kure-ji on 2009-01-29
it works for me!

a big thanks to caljohnsmith :D

---

### Post by DiWO on 2009-01-29
Like i said i didn't need help fixing it, but glad it helped a person who had the same problem ^^

The point is i don't get why auto update replaced whole menu.lst in the first place O.o 
I forced my friends to at least dual-boot with ubuntu and when they can't even boot it anymore just because of update really dissapoints as I have to hear all the whining now :/

---

### Post by Pelonchas on 2009-04-09
I have the same problem. And i think the other guy really answer your question, he tell you how prevent that to happen again. Need to have the menu.lst configured to not change the whole kernels thing again. Yes, i know it must be pre-configured by ubuntu.

Find this code:

```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all
```

And changue howmany=all by howmany=n , n its the number of kernels you had that you wish to appear in the list. Lets say n=1.
Like this.

```

## e.g. howmany=all
##      howmany=7
# howmany=1

```

I hope this works for you. Works for me.

---

