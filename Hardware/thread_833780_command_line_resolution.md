---
title: "command line resolution"
date: 2008-06-18
forum: Hardware
---

### Post by victory2007 on 2008-06-18
Hi all, I just installed Ubuntu server on my laptop for a project of mine.  But I can't see the whole screen.  When type on the screen the text disappears one it gets to the bottom of my screen and I can never get it to move up.  Is there a way to change the resolution of the command line.

Thanks

---

### Post by cdtech on 2008-06-18
Try changing the vga in your /boot/grub/menu.lst:

```
/vmlinuz-2.6.22-14-generic root=UUID=41d95d32-e6bf-418b-b3fe-278d0c7ba5e1 ro quiet splash vga=792
```

You may need to select the proper number but this works for me.

```

        640×480 800×600 1024×768 1280×1024 1600×1200 Ask user at boot
8 bits  vga=769 vga=771 vga=773  vga=775   vga=796   vga=ask
16 bits vga=785 vga=788 vga=791  vga=794   vga=798   vga=ask
32 bits vga=786 vga=789 vga=792  vga=795   vga=799   vga=ask

```

---

### Post by victory2007 on 2008-06-23
Worked great, Thanks

---

