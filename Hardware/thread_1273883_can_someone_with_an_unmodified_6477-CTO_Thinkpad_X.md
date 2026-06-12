---
title: "can someone with an unmodified 6477-CTO Thinkpad X300 generate DSDT?"
date: 2009-09-23
forum: Hardware
---

### Post by gnychis on 2009-09-23
Hi all,

I was wondering if someone with a 6477-CTO X300 that uses Linux can generate their DSDT for me.  It is important that you do NOT use Zender's BIOS hack to support another wireless card (if you don't know what I'm talking about, don't worry about it!).  I suspect the BIOS hack screwed up my graphics after sleeping, but I'm not entirely sure.  So, I was wondering if someone could generate me their DSDT.

In Linux:
```

sudo apt-get install iasl
sudo cat /proc/acpi/dsdt > dsdt.dat
iasl -d dsdt.dat
iasl -tc dsdt.dsl

```

Then zip me dsdt.dsl and attach it if you can.  I would **sincerely** appreciate it.

- George

---

