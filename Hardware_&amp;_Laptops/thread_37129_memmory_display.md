---
title: "memmory display"
date: 2005-05-26
forum: Hardware &amp; Laptops
---

### Post by glasscleaner on 2005-05-26
first of all, this is my first try to Ubuntu and at the same time my first post.

btw, I say hello to everyone on this forum and I will try to say active as far i will get skill with the new os for me. (and my english sux too)  :roll: 

well, my question is:

i have looked into the "application/system tools/system monitor/ and the monitor show me a total ram of 885.4mb. I want to know why i dont have 1024mb here. i dont have any video shared ram or anything else.

here a screenshot:
[http://img44.echo.cx/img44/6132/screenshot2rc.png](http://img44.echo.cx/img44/6132/screenshot2rc.png)

thanks for any help!

---

### Post by Alexander Kirillov on 2005-05-26
[QUOTE=glasscleaner]first of all, this is my first try to Ubuntu and at the same time my first post.

btw, I say hello to everyone on this forum and I will try to say active as far i will get skill with the new os for me. (and my english sux too)  :roll: 

well, my question is:

i have looked into the "application/system tools/system monitor/ and the monitor show me a total ram of 885.4mb. I want to know why i dont have 1024mb here. i dont have any video shared ram or anything else.

here a screenshot:
[http://img44.echo.cx/img44/6132/screenshot2rc.png](http://img44.echo.cx/img44/6132/screenshot2rc.png)

thanks for any help![/QUOTE]
 What is the output of 
```
dmesg|grep mem
```

---

### Post by glasscleaner on 2005-05-26
Memory: 901916k/917504k available (1436k kernel code, 14980k reserved, 754k data, 224k init, 0k highmem)
Freeing initrd memory: 4300k freed
Freeing unused kernel memory: 224k freed
Freeing memory... done (458 pages freed)
agpgart: Maximum main memory to use for agp memory: 816M
ehci_hcd 0000:00:10.3: irq 21, pci mem 0xe2005000

---

### Post by Alexander Kirillov on 2005-05-26
[QUOTE=glasscleaner]Memory: 901916k/917504k available (1436k kernel code, 14980k reserved, 754k data, 224k init, 0k highmem)
Freeing initrd memory: 4300k freed
Freeing unused kernel memory: 224k freed
Freeing memory... done (458 pages freed)
agpgart: Maximum main memory to use for agp memory: 816M
ehci_hcd 0000:00:10.3: irq 21, pci mem 0xe2005000[/QUOTE]
 Apparently, it means that the kernel only sees 917504k when booting - not 1024 Mb. If you are positive that you have indeed 1024 Mb (Does BIOS show it?), you can try explicitly modify the command used to load the kernel in GRUB: it allows one to specify explicitly amount of memory -- do not remember the syntax, but Google will help.

---

### Post by glasscleaner on 2005-05-26
well i have 2x 512mb and the bios show me 1024mb as well.

i wrote what you say and ill look an eye later when i will have more skills :P

thanks dude!

---

