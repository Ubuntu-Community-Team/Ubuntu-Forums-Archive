---
title: "installation impossible - Acer Travelmate with Radeon 9700 black screen"
date: 2006-01-26
forum: Hardware &amp; Laptops
---

### Post by ulgor on 2006-01-26
Hi,
I also posted here: [http://ubuntuforums.org/showthread.php?t=48153]("http://ubuntuforums.org/showthread.php?t=48153")

Even when I turn acpi and apic off for installation, my screen just goes black. It seems to be a problem with the ATI radeon 9700. I can´t even install version 5.10, :(  ...any ideas??

There are some people here that didn´t have problems with their Travelmates, right?

---

### Post by ulgor on 2006-01-30
Hi,
I didn´t get much help on this one, but I finally found a solution..
Please read the thread mentioned above, the solution was the "vga=771" setting when installing (instead of pressing ENTER for default settings), like this:

```
linux vga=771
```

---

### Post by nalmeth on 2006-01-31
good job figuring it out and posting your results. I hope this is noted by staff

---

