---
title: "ubuntu dont works with two ram slots"
date: 2008-09-20
forum: Hardware
---

### Post by syms on 2008-09-20
hello
i have two 512 mb ram slots. when i have two ram slockets installed windows working fine but ubuntu dont even boots, it gives me kernel panic errors. when i change positions of these two ram slockets ubuntu boots and works, but it sometimes just freezes, and windows freezes too. i tested memory - its good i guarantee.when i have only one ram slocket installed the problems with ubuntu gone and windows working fine too. how can i fix that problem because ubuntu with 512 mb ram dont works very good.

---

### Post by IntuitiveNipple on 2008-09-20
> **syms said:**
> when i change positions of these two ram slockets ubuntu boots and works, but it sometimes just freezes, and windows freezes too. i tested memory - its good i guarantee
These are classic signs of a faulty or failing RAM module.

Run memtest on the modules and let it continue overnight. If that reports no issues then you can be more confident the RAM modules are good. If they pass that test and the system still has the problem then it is likely there is a motherboard or BIOS configuration issue.

Reporting the hardware of the system might help others give you some clues:
```

lspci -nn

lsusb

```
Also, attaching a (compressed) copy of /var/log/dmesg would let us know what the linux kernel discovers at start-up:
```

cd ~
cat /var/log/dmesg | gzip > dmesg.log.gz

```

---

### Post by Sef on 2008-09-20
> Run memtest on the modules and let it continue overnight. If that reports no issues then you can be more confident the RAM modules are good. If they pass that test and the system still has the problem then it is likely there is a motherboard or BIOS configuration issue.


If you want a newer version that what is in GRUB, then [download memtest86]("http://www.memtest86.com/") from their website.

---

### Post by syms on 2008-09-20
thanks but ive already tested it and it has no problems found

---

