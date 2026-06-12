---
title: "Adding a second CPU = no boot | Ubuntu Server 14.04.1"
date: 2014-12-17
forum: Hardware
---

### Post by daniel201 on 2014-12-17
Hi,

I have Ubuntu Server 14.04.1 installed on a Dell Precision T5400. At present the machine has a single Xeon [FONT=Trebuchet MS, Meiryo UI Reg, &#12513;&#12452;&#12522;&#12458; Reg, MS UI Gothic Reg, Hiragino Kaku Gothic Reg, &#12498;&#12521;&#12462;&#12494;&#35282;&#12468; Pro W3 Reg, Microsoft YaHei, &#24494;&#36719;&#38597;&#40657;, Hiragino Sans GB, Microsoft JhengHei, &#24494;&#36575;&#27491;&#40657;&#39636;, Malgun Gothic, Gulim, Tahoma, Arial Unicode, sans-serif][COLOR=#444444]E5420 installed.[/COLOR][/FONT]

[FONT=Trebuchet MS, Meiryo UI Reg, &#12513;&#12452;&#12522;&#12458; Reg, MS UI Gothic Reg, Hiragino Kaku Gothic Reg, &#12498;&#12521;&#12462;&#12494;&#35282;&#12468; Pro W3 Reg, Microsoft YaHei, &#24494;&#36719;&#38597;&#40657;, Hiragino Sans GB, Microsoft JhengHei, &#24494;&#36575;&#27491;&#40657;&#39636;, Malgun Gothic, Gulim, Tahoma, Arial Unicode, sans-serif][COLOR=#444444]Adding a second Xeon E5420 results in the machine rebooting after Ubuntu has been selected from the Grub boot loader. The same behaviour occurs when booting into recovery mode, or trying to boot Linux Mint 17 from a USB disk.
The machine happily runs memtest or boots Windows XP from the Hirens boot DVD so I don't think there's are hardware issue. There don't seem to be any configurable BIOS settings related to dual CPU use.

Any thoughts on whether Ubuntu Server 14.04.1 supports this configuration or whether this issue can be resolved?
(I'm just trying an Ubuntu 14.04.1 live CD)

Thanks
Daniel[/COLOR][/FONT]

---

### Post by daniel201 on 2014-12-17
Resolved it.
Although both CPUs had the same model number, they were different steppings. One was SLANV and the other was SLBBL.
Another SLANV CPU is on order.

---

