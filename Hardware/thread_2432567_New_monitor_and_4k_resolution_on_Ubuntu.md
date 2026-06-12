---
title: "New monitor and 4k resolution on Ubuntu"
date: 2019-12-04
forum: Hardware
---

### Post by Hibari on 2019-12-04
As the title says, I've bought a new 4K monitor to replace my ancient one, but Ubuntu won't let me set any resolution higher than the older 1920x1080.

Any ideas about how to fix this?

---

### Post by Autodave on 2019-12-04
We need some info please.  What 'buntu are you running?  What are the specs on your equipment?  Graphics card installed?  How is your monitor connected to the PC: what cables and adapters?

---

### Post by Hibari on 2019-12-04
Version: 18.04.3 LTS 64bit
Processor: Intel® Core&#8482; i5 CPU 650 @ 3.20GHz × 4 
Graphics: AMD® Cedar
Cable: High speed HDMI cable

Anything else?

---

### Post by SeijiSensei on 2019-12-04
The Cedar seems to also be known as a Radeon 5000.  It's not listed as supporting 4K here: [https://www.amd.com/en/products/specifications/graphics](https://www.amd.com/en/products/specifications/graphics)

I know essentially nothing about AMD video though; I've much preferred to use NVIDIA on Linux over the years. So I might be entirely wrong.

---

### Post by Hibari on 2019-12-04
> **SeijiSensei said:**
> The Cedar seems to also be known as a Radeon 5000.  It's not listed as supporting 4K here: [https://www.amd.com/en/products/specifications/graphics](https://www.amd.com/en/products/specifications/graphics)

I know essentially nothing about AMD video though; I've much preferred to use NVIDIA on Linux over the years. So I might be entirely wrong.

I know for sure than some guy managed to run 4k on it (on Windows, though), so I thought it could be possible.
Anyway, it should be at least able to go beyond 1080p, but I don't see that option at all.

---

### Post by Autodave on 2019-12-04
Saw a previous post where it was recommended to remove *nomodeset *from grub.

There are several HDMI cables: do you know what version you have?  Just because it is HDMI doesn't mean that it will support a 4K monitor.

---

### Post by Autodave on 2019-12-04
4K resolution is normally considered to be 3840 x 2160.  The Cedar card is maxed out at 2560×1600.

---

### Post by Hibari on 2019-12-04
> **Autodave said:**
> Saw a previous post where it was recommended to remove *nomodeset *from grub.

I don't see it in /etc/default/grub, so I assume it was already removed?

> **Autodave said:**
> There are several HDMI cables: do you know what version you have?  Just because it is HDMI doesn't mean that it will support a 4K monitor.

It came with the monitor, I supposed it should support it.

> **Autodave said:**
> 4K resolution is normally considered to be 3840 x 2160.  The Cedar card is maxed out at 2560×1600.

Well, why can't I at least increase it to that?

---

