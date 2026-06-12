---
title: "problem with menu.lst"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by ali200reza on 2009-06-26
i was installed fedora 10 on my system and now i install ubuntu 9.04 on my system
but when i install ubuntu 9.04 i dont install grub because it was with fedora and i think i can add my ubuntu address to menu.lst in fedora.
my problem is that this file initrd.img-2.6.28-11-generic is not in ubuntu boot 
in /boot/ which i want to add in menu.lst
plz Help me
with thanks

---

### Post by Herman on 2009-06-26
Well, you could just boot your Ubuntu installation by the symlinks to your current linux kernel and initrd.img, assuming you do have a kernel and initrd.img. The symlinks are in /, and by using the symlinks you will avoid the need to specify the exact path and filename for those files. That way you won't need to re-edit your menu.lst file in Fedora every time Ubuntu has a new updated kernel.
```
title    Ubuntu
uuid   <fsnumber>
kernel /vmlinuz root=UUID=<fsnumber><kerneloptions>
initrd  /initrd.img

```

Otherwise, maybe re-install and next time choose to install GRUB.
You will have a choice whether to install GRUB to MBR or somewhere else.
If you install Ubuntu's GRUB to MBR it will probably detect your other operating system(s) and add them to it's boot menu automatically.
If you decide to install Ubuntu's GRUB to the first sector of your new Ubuntu partition, you can chainload Ubuntu's GRUB from Fedora's GRUB. That would also be better than using the direct kernel boot where you need the exact path and filename for your current Ubuntu kernel and initrd.img files.

---

