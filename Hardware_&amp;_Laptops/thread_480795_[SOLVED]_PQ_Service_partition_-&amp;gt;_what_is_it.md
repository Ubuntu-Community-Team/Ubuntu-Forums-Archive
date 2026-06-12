---
title: "[SOLVED] PQ Service partition -&amp;gt; what is it?"
date: 2007-06-21
forum: Hardware &amp; Laptops
---

### Post by neburzaragoza on 2007-06-21
Hi,

I installed a few months ago Ubuntu 6.06. I don't remember exactly what I did with my partitions. The things is that I have one I can't understand
It's my*hda1 * and its name is *PQ SERVICE*.

here I show you a *fdisk*, it's the one where you read *Compaq diagnostics*

```

xx@xx-laptop:~$ sudo fdisk -l.
Password:

Disco /dev/hda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hda1               1         509     4088511   12  Compaq diagnostics
/dev/hda2   *         510        5087    36772785    c  W95 FAT32 (LBA)
/dev/hda3            5088        9092    32170162+   c  W95 FAT32 (LBA)
/dev/hda4            9093        9729     5116702+   5  Extendida
/dev/hda5            9093        9528     3502138+  83  Linux
/dev/hda6            9529        9729     1614501   82  Linux swap / Solaris

```

inside this hd I have folders with these names: *autorun, Minint, factory, d2d.*

can you explain me what is it for?
and if I can delete it or wether I could use the free space on it?

Thank you for the help

---

### Post by 5-HT on 2007-06-21
It's probable that it was put on by the computer manufacturer. I don't have a compaq so I'm not sure exactly what it is, but it could be some diagnostic tests for the computer (dell has something similar, and I find it quite handy to keep around). You can always add an entry for it in your menu.lst to boot it and test it out, or just boot it using grub's interactive prompt.

---

### Post by neburzaragoza on 2007-06-22
Ye,

thank you for you answer, it's pretty probably what you say.
i'll try to find somehing else in internet...

bye

---

### Post by jfinkels on 2007-06-22
> **5-HT said:**
> It's probable that it was put on by the computer manufacturer. I don't have a compaq so I'm not sure exactly what it is, but it could be some diagnostic tests for the computer (dell has something similar, and I find it quite handy to keep around). You can always add an entry for it in your menu.lst to boot it and test it out, or just boot it using grub's interactive prompt.

Compaq, Dell, etc. will put goofy little partitions on your computer for their own purposes, because they don't expect most end users to go looking through his or her partitions.

---

### Post by neburzaragoza on 2007-06-22
And do you think it'll be a problem if a take the free volume of that partition for my own partitions?
I just want to know whether the 1Gb free taht I have inside this partition will be used by itself or it'll reamin free.

thank you;)

---

### Post by silverglade00 on 2007-06-22
That partition is most likely there as a restore or recovery partition in case your Windows system gets broken. Usually if you boot from there, it will write over your hard drive, returning it to the state it was in when it left the factory. If you have another way of installing Windows, or don't care to install Windows anymore, then you can get rid of it.

---

### Post by neburzaragoza on 2007-06-22
Thank you for the answers.
Now I have an clear idea of what it is.

bye

---

