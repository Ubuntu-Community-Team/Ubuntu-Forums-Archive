---
title: "linux dual booting"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by UncleMonty on 2009-06-03
I'm tempted to dual boot intrepid and jaunty as I'm having issues with Jaunty and need to check if Intrepid is as good as I remember. 

Having dual-booted two linux distros how can I delete the distro I no longer want?

---

### Post by logos34 on 2009-06-03
> **UncleMonty said:**
> Having dual-booted two linux distros how can I delete the distro I no longer want?

it depends which was installed last, which affects the bootloader.

Just do this: boot into the one you want, and run:

> sudo grub-install /dev/sda (or whatever the drive is)

Remove any entries for the other OS in /boot/grub/menu.lst and /etc/fstab

Now use Gparted to unmount and delete other ubuntu partition

---

### Post by UncleMonty on 2009-06-03
> **logos34 said:**
> it depends which was installed last, which affects the bootloader.

Just do this: boot into the one you want, and run:

 (or whatever the drive is)

Remove any entries for the other OS in /boot/grub/menu.lst and /etc/fstab

Now use Gparted to unmount and delete other ubuntu partition


Thanks, I've installed Jaunty now and will be installing Intrepid next.

Will I need to d/l gparted or does that come with the os?

---

### Post by merlinus on 2009-06-03
I believe you will have to d/l it from either Add/Remove or synaptic.

---

### Post by logos34 on 2009-06-03
> **merlinus said:**
> I believe you will have to d/l it from either Add/Remove or synaptic.

you mean it's still not included in fresh installation? (but it is on the live cd, go figure)

---

### Post by merlinus on 2009-06-03
weird, huh?  i looked all over for it after installing 9.04, but wound up having to d/l it.

of course i also have the gparted live cd, which is even better.

---

### Post by UncleMonty on 2009-06-04
Is it possible to merge a deleted partition with other partitions?

---

### Post by merlinus on 2009-06-04
You can add the freed-up space to an existing partition, or extend an existing one into that space if they are adjacent to one another.

---

