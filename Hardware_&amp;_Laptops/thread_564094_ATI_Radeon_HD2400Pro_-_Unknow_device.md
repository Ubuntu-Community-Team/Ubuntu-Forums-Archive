---
title: "ATI Radeon HD2400Pro - Unknow device?"
date: 2007-09-30
forum: Hardware &amp; Laptops
---

### Post by Hal.9000 on 2007-09-30
I just bought a ATI Radeon HD2400Pro pcie graphics card and I'm using the new 8.41.7 fglrx driver.  Everything seems to be working fine but the weird thing is it show up as
```
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 94c3
```
when I run lspci from a terminal.  While it works fine I was just wondering why it would show up as an unknown device.
Thanks

---

### Post by Natr0n on 2007-09-30
I don't think it's an issue. I get the same output on my computer, but haven't had any problems so far. I wouldn't worry about it.

---

### Post by westep23 on 2007-09-30
[http://pci-ids.ucw.cz/](http://pci-ids.ucw.cz/)

I'm pretty sure that file is stored /usr/share/misc/pci.ids

I also dont believe it has any ill effects because of the way nvidia/ati drivers do there own probing when xorg starts.

---

### Post by Hal.9000 on 2007-09-30
Good to hear that its not going to be a problem. Thanks for clearing that up for me.

---

