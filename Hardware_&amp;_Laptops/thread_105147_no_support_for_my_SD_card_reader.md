---
title: "no support for my SD card reader?"
date: 2005-12-17
forum: Hardware &amp; Laptops
---

### Post by taseal on 2005-12-17
It works on XP, but not on ubuntu  I'd really like it too... this is the only reason (and my ipod not synching up) that I still have XP on my comp...

anything I can do to fix this?

I'd give u driver info, but I'm not sure on that since its built into the laptop

it is an asus a3500n laptop btw if it helps...

---

### Post by mlomker on 2005-12-18
[QUOTE=taseal]it is an asus a3500n laptop btw if it helps...[/QUOTE]

It probably isn't supported...only a couple of chipsets are.  You'll want to look for the chipset in **lspci** and then you can Google for that.

```

0000:00:09.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator

```

O2 refuses to release the specs or write a linux driver, so I'm stuck as well.  There are a couple USB readers that are supported...you'll find them on the HCL at the linuxquestions site as well as a few threads on here.

---

### Post by taseal on 2005-12-18
Well that sux :(

---

