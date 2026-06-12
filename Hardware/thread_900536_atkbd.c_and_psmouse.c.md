---
title: "atkbd.c and psmouse.c"
date: 2008-08-25
forum: Hardware
---

### Post by phooter on 2008-08-25
Hi, 

I recently buy a Dell XPS M1530 and install on it Kubuntu 8.04.

Sometimes, the keyboard fail, keeping it freezen or writing the same letter 1 or 2 seconds, and the touchpad directly not work, i cant use it. 

dmesg:
```

[ 1731.392761] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[ 1731.403681] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[ 1731.417898] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[ 1731.608701] psmouse.c: Failed to reset mouse on isa0060/serio1
[ 1731.612350] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[ 1731.719490] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[ 1731.756241] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[ 1731.817893] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[ 1731.990400] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[ 1732.017676] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[ 1732.087945] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[ 1733.929034] printk: 17 messages suppressed.
[ 1733.929046] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[ 1737.415527] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input12
[ 1737.625352] psmouse.c: Failed to enable mouse on isa0060/serio1

```

I hope that you can help me,

Regards

---

### Post by ntropy on 2008-09-22
Adding **i8042.panicblink=0** to the boot options has helped minimise this issue for me in the last 2 days (from [http://kerneltrap.org/node/5898](http://kerneltrap.org/node/5898))

I am unable to comment on what other issues this may cause.

/boot/grub/menu.lst

```
title       Ubuntu 8.04.1, kernel 2.6.24-19-no_panicblink
root        (hd0,6)
kernel      /boot/vmlinuz-2.6.24-19-generic root=UUID=00a0039d-1a17-4f82-8f3c-3e8802345123 ro quiet i8042.panicblink=0
initrd      /boot/initrd.img-2.6.24-19-generic

```EDIT: Hmm, scratch that. I think the perceived effects were purely psychological.

---

