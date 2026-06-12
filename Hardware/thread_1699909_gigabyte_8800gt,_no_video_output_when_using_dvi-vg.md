---
title: "gigabyte 8800gt, no video output when using dvi-vga adapter"
date: 2011-03-04
forum: Hardware
---

### Post by felixnine on 2011-03-04
ubuntu lucid, up-to-date

i just got a gigabyte nvidia 8800gt pci-express for my htpc/media server. it works going straight dvi to my monitor, but doesn't produce a signal when connected to my monitor or tv via a dvi-vga adapter (dvi-i).

the reason i ask here is because i've read about situations where it will work once the os starts, but not during boot, for whatever reason. xrandr reports a connected display called LVDS1, but with incorrect resolutions. trying to switch to this display does not produce an error, but it still doesn't work.

any ideas? i know the drivers aren't right as the old video card needs 96.xx while the new one needs 270.xx, but that should't matter; i should still be able to see the console, right? even if it can't start x?

thanks in advance.

---

### Post by felixnine on 2011-03-10
just checked the adapter using a multimeter. all the analog pins test fine. i'm going nuts here.

---

### Post by felixnine on 2011-03-10
yup, i'm an idiot. all i had kicking around was dvi-d cables, so i have to pony up and buy a dvi-a --> svga cable.

---

