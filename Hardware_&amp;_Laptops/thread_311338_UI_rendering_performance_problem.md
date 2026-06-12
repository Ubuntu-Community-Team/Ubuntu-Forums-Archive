---
title: "UI rendering performance problem"
date: 2006-12-02
forum: Hardware &amp; Laptops
---

### Post by Joe_Bishop on 2006-12-02
So, I have the following configuration:
Processor: Athlon XP 2500+
Motherboard: Gigabyte GA-7N400 (nForce2 400Ultra)
Memory: 1Gb + 0.5Gb DDR PC3200 Hynix D43
Videocard: Leadtek Winfast A7600GT TDH (256Mb GeForce 7600gt AGP 8x)
Soundcard: Creative Audigy 2zs
HDDs: Maxtor 6L300R0 (300Gb 16Mb IDE ATA133)
      Western Digital WD800BB (80Gb 2Mb IDE ATA100)
DVD-RW: LG GSA 4167B
TV tuner: Beholder 507rds
Ethernet adapters: 3Com Etherlink 10/100
                   Realtek 3189

The widgets (windows, dialogs, etc) are rendered too slowly. I was thinking it to be the feature of X-server, but then I saw that they are rendered on A64 2800+ powered machine (VIA chipset, GF 6600) without any tweaks even with the live-cd. It was much faster.
For example, when I drag window left-right, I am quite satisfied with the speed of rendering. But if I drag it up and down, it is rendered with small delays so that it moves with twitches. I am using nVidia binary drivers 9629 now. Before that I used binary drivers nVidia 8xxx and legacy driver nv. And I had the same problem with these drivers. I am using Edgy now, but with Dapper I had the twitches, too.
I'd be grateful to anyone who can tell what the problem here might be.

---

### Post by Joe_Bishop on 2006-12-04
I have just tried Knoppix, don't know exactly its version, it was made about 2004 year, so it doesn't know about my videocard. But it renders windows faster. :(

---

### Post by 23meg on 2006-12-04
Take a look at  [this]("http://www.ubuntuforums.org/showpost.php?p=1114025&postcount=31") for a start.

---

### Post by Joe_Bishop on 2006-12-04
Nothing related to my case.
I have forgotten to write, that rendering performance using live cd is terribly slow ("vesa"), similar to one in windows XP without video drivers, although on that A64 it exceeds my speed with "nvidia". Rendering on beryl or xgl+compiz is slow, too. It was much faster on kororaa.
I suppose the problem occures because of the incomplete support of my hardware, but don't know exactly which part of it.

---

