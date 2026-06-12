---
title: "Kernel Panic?"
date: 2009-04-08
forum: Hardware
---

### Post by msohn88 on 2009-04-08
After installing Korean Language Support on Ubuntu 8.10 on Thinkpad T42.

I get

[   0.397228] ACPI: Aborted because junk in compressed archive.
[   1.964716] invalid compressed format (err=1)
[   2.001029] Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

I have my term papers saved on this computer...
Please help!

thanks!

---

### Post by linuxuser21 on 2009-04-08
First, you can boot off the Live CD if you have it and get the documents you need and back them up on a flash drive or something like that if you want.  Then, I'd reinstall Ubuntu where it got messed up at.

---

### Post by msohn88 on 2009-04-08
> **linuxuser21 said:**
> First, you can boot off the Live CD if you have it and get the documents you need and back them up on a flash drive or something like that if you want.  Then, I'd reinstall Ubuntu where it got messed up at.

I did it with recovery mode.

Thanks.

---

### Post by RealSysace on 2009-06-11
I've had the same problem this morning, after installing some updates yesterday.

I'm quite sure that these updates (or maybe something else) corrupted my initrd image.

I managed to avoid the reinstallation by doing the following steps.

First, I replaced the following line in my menu.lst :

 ```
 kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=781e0ca1-6d5d-4b13-a8a9-98bc1746dabe ro quiet splash 
```

by 

```
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sda1 ro quiet splash
```

This allowed me to boot.

Then I rebuilt my initrd image :

```
mkinitramfs -o /boot/initrd.img-2.6.28-11-generic /lib/modules/2.6.28-11-generic/
```

and I replaced the ancient one with it.

After a last reboot everything was working fine again.

Hope this can help someone in this situation ;)

---

