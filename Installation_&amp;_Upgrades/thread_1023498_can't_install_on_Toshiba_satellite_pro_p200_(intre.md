---
title: "can't install on Toshiba satellite pro p200 (intrepid)"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by faminator on 2008-12-28
Fairly new laptop.
It worked fine with hardy

With intrepid I can't get a GUI either from a live CD for install or after alternate cd install

Any ideas?

Famine

---

### Post by lykwydchykyn on 2008-12-28
Do you know what video card it uses?  Try this command:
```

lspci |grep -i vga

```

That will show you what video card you have in there.

---

### Post by faminator on 2008-12-28
> **lykwydchykyn said:**
> Do you know what video card it uses?  Try this command:
```

lspci |grep -i vga

```

That will show you what video card you have in there.

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 2400

Thanks

---

### Post by lykwydchykyn on 2008-12-28
Hmmm...  Can you post the output from this:

```

cat /var/log/Xorg.0.log |grep "(EE)"

```

(that command searches your Xorg logs for errors)

---

