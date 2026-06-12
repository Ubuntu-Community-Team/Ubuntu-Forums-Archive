---
title: "Boot Loader"
date: 2006-02-06
forum: Installation &amp; Upgrades
---

### Post by fahrenheit on 2006-02-06
Hi

I'm using a multi-user computer and the Windows users aren't going to be too appreciative of it booting Ubuntu by default. How can I change it so that it boots Windows by default after the timeout rather than Ubuntu?

Thanks
F

---

### Post by lordbf1 on 2006-02-06
edit your boot loader and set the default to win ntfs partition, not the hda linux partition.

---

### Post by fahrenheit on 2006-02-06
How would one go about that?
I can't find a program within Ubuntu that will let me change this, I know they exist because I can remember one on an old version of Mandrake.

I'm slightly worried about doing it with an editor.
I've looked at the boot file and it's got this at the end...

```

# This entry automatically added by the installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

Now, is it a case of just moving that block of code above...

```

## ## End Default Options ##

titleUbuntu, kernel 2.6.12-9-386 
root(hd0,2)
kernel/boot/vmlinuz-2.6.12-9-386 root=/dev/hdc3 ro quiet splash
initrd/boot/initrd.img-2.6.12-9-386
savedefault
boot

titleUbuntu, kernel 2.6.12-9-386 (recovery mode)
root(hd0,2)
kernel/boot/vmlinuz-2.6.12-9-386 root=/dev/hdc3 ro single
initrd/boot/initrd.img-2.6.12-9-386
boot

titleUbuntu, memtest86+
root(hd0,2)
kernel/boot/memtest86+.bin  
boot
```

... ^ this block.

---

### Post by lha on 2006-02-06
If you manually add an entry between lines
'### BEGIN AUTOMAGIC KERNELS LIST' and
'### END DEBIAN AUTOMAGIC KERNELS LIST',
your entry will be erased next time you upgrade kernel. You can find a line with 'default 0' and change the number to choose which menu entry is selected by default. If you want to put Windows in the top of grub's list, put that block of code you were moving above '### BEGIN AUTOMAGIC KERNELS LIST' line.

---

