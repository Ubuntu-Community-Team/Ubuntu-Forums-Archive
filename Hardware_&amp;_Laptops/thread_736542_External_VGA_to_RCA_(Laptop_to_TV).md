---
title: "External VGA to RCA (Laptop to TV)"
date: 2008-03-26
forum: Hardware &amp; Laptops
---

### Post by Serenity55 on 2008-03-26
I have a Gateway laptop with an Intel graphics card and I want to play movies in totem and view them on my TV. I purchased an adapter that has a vga port on one end and S-video and RCA (yellow cable) on the other and a headphone port to RCA (red and white cables) adapter. The first problem I ran into is that when you press Fn+F4 (the switch that is supposed to switch over to that external vga port) the laptop freezes requiring a reboot. After much goggling I found that if I go into grub during boot and and the commands noapic and nolapic the laptop doesn't freeze but it also doesn't display to my TV. I assume that I need to do something to Xorg.conf to have settings that the TV can recognize.

So my questions are twofold:

1) How do I set it up so that that noapic and nolapic commands are persistent instead of having to add it to grub on every boot.

2) What (if anything) do I need to do to Xorg.conf to make this work.

Any help would be appreciated, I've been at this all day. Thanks!!!

---

