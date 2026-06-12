---
title: "proper way to permanantly enable dma?"
date: 2004-12-01
forum: Hardware &amp; Laptops
---

### Post by stateq2 on 2004-12-01
Hello.  How can I properly enable dma support for my drive.  I use the "hdparm -d1" command, but it goes back to normal at reboot.  Thanks.

---

### Post by cabu on 2004-12-01
You need to edit /etc/hdparm.conf to your needs. This file gets called up by the hdparm script at boot time.

---

### Post by bob k on 2004-12-02
[QUOTE=stateq2]Hello.  How can I properly enable dma support for my drive.  I use the "hdparm -d1" command, but it goes back to normal at reboot.  Thanks.[/QUOTE]

My first question would be what kind of HD and controller you have. I believe that the boot hardware probe asks the disk controller if it is able to do DMA and at what level it can do it. I would think if you forced DMA on the drive you would end up with some kind of corruption down the road. Just a thought.

Bob

---

### Post by stateq2 on 2004-12-02
[QUOTE=bob k]My first question would be what kind of HD and controller you have. I believe that the boot hardware probe asks the disk controller if it is able to do DMA and at what level it can do it. I would think if you forced DMA on the drive you would end up with some kind of corruption down the road. Just a thought.

Bob[/QUOTE]

actually, it's for my dvd drive (/dev/hdb)...and If I don't enable dma, I can't rip cd's properly.

---

