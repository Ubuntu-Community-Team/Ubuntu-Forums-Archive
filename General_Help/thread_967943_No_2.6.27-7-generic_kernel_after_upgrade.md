---
title: "No 2.6.27-7-generic kernel after upgrade"
date: 2008-11-02
forum: General Help
---

### Post by linuxpyro on 2008-11-02
I just did an upgrade of my Hardy installation to Intrepid.  Under Hardy I used the 2.6.24-19-generic kernel.  During the installation I noticed that the upgrade to 2.6.27-7-generic was done, however it does not show up in the Grub menu.  I can see the initrd and system.map files in /boot (one for 2.6.24-19-generic as well as for 2.6.27-7-generic), but apparently grub did not configure it.  I tried running sudo update-grub, which did mention the 2.6.27 kernel in the output in the terminal but did not actually add it to the menu.lst.

I tried adding it to the menu.lst file manually, using the other entries as a template.  It started to boot, but would not complete after complaining about not being able to find the disk.

Any ideas?  I've been looking at this late, so I'm sorry if it's something obvious that I missed (that would figure)...

---

### Post by taurus on 2008-11-02
If it complains about couldn't find the disk, it means you probably have to UUID in /boot/grub/menu.lst wrong (or even in /etc/fstab).  Can you post your /boot/grub/menu.lst and /etc/fstab?  You don't have to post all the lines that start with # since those are comments.

---

### Post by linuxpyro on 2008-11-02
Sure.  The top entry is the one I manually created, while the bottom one is the last one that works, which I am booted into now.

```

title           Ubuntu 8.10, kernel 2.6.27-7-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=e9aaa8e5-4e01-4a45-b4$
initrd          /boot/initrd.img-2.6.27-7-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=e9aaa8e5-4e01-4a45-b4fa-f30f0994b3c9 ro quiet splash elevator=cfq
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

```

---

### Post by ptn107 on 2008-11-02
The UUIDs in your kernel lines do not match.  Maybe that's the cause?

---

### Post by fooman on 2008-11-02
yeah what ptn107 said...

give this a try in place of the top entry and see if that boots:

```
title           Ubuntu 8.04.1, kernel 2.6.27-7-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27.7-generic root=UUID=e9aaa8e5-4e01-4a45-b4fa-f30f0994b3c9 ro quiet splash elevator=cfq
initrd          /boot/initrd.img-2.6.27-7-generic
quiet
```

---

### Post by linuxpyro on 2008-11-02
Wow, I guess that's what I get for not paying attention to the fact that nano didn't do wordwrapping.  :)  Thanks, it's fine now.

It still seems weird that I couldn't get the update-grub script to stick the new kernel into menu.lst, but I guess it's not a big deal right now.

Again, thanks a bunch!

---

### Post by taurus on 2008-11-02
> **linuxpyro said:**
> Wow, I guess that's what I get for not paying attention to the fact that nano didn't do **_wordwrapping_**.  :)  Thanks, it's fine now.


Next time, run nano with the -w option.

```
nano -w filename
```

---

