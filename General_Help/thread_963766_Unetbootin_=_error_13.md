---
title: "Unetbootin = error 13"
date: 2008-10-30
forum: General Help
---

### Post by trill on 2008-10-30
Just installed Unetbootin, rebooted, selected Unetbootin and I get this
```
 error 13 invalid or unsupported executable format
```

Halp out a dummy :confused:

```
title		Linux Mint, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
boot

title		Linux Mint, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.22-14-generic
boot

title		Linux Mint, kernel memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


title UNetbootin
root (hd0,0)
kernel  /boot/ubnkern splash=silent showopts
initrd /boot/ubninit 
boot

title linux
root (hd0,0)
kernel /boot/i386/loader/linux splash=silent showopts
initrd /boot/i386/initrd-xen
boot

title repair
root (hd0,0)
kernel /boot/i386/loader/linux splash=silent repair=1 showopts
initrd /boot/i386/initrd-xen
boot

title rescue
root (hd0,0)
kernel /boot/i386/loader/linux splash=silent rescue=1 showopts
initrd /boot/i386/initrd-xen
boot

title mediachk
root (hd0,0)
kernel /boot/i386/loader/linux splash=silent mediacheck=1 showopts
initrd /boot/i386/initrd-xen
boot

title firmware
root (hd0,0)
kernel /boot/i386/loader/linux splash=silent install=exec:/bin/run_biostest showopts
initrd /boot/ubninit
boot

title memtest
root (hd0,0)
kernel /suse/i586/memtest86+-2.01-11.1.i586.rpm 
initrd /boot/ubninit
boot

```

---

### Post by trill on 2008-10-30
[IMG]http://img371.imageshack.us/img371/3688/halpcatsv5.jpg[/IMG]

I need to figure this out tonight :(

---

### Post by trill on 2008-10-30
[IMG]http://img373.imageshack.us/img373/5156/halpmecatcf9.jpg[/IMG]

---

