---
title: "Intel GMA 950 and overscan"
date: 2010-01-25
forum: Hardware
---

### Post by aperture_kubi on 2010-01-25
On a fresh install of Ubuntu 9.10 (32 bit), it appears as though the OS/hardware is sending a signal with overscan compensentation, but the TV/monitor isn't doing overscan.
The result is I have black borders on all sides except the bottom which is cut off.

Hardware: MSI barebones Nettop 100.

---

### Post by mutrax on 2010-02-08
> **aperture_kubi said:**
> On a fresh install of Ubuntu 9.10 (32 bit), it appears as though the OS/hardware is sending a signal with overscan compensentation, but the TV/monitor isn't doing overscan.
The result is I have black borders on all sides except the bottom which is cut off.

Hardware: MSI barebones Nettop 100.

Had the same issue. **Increasing the video memory to 224mb in the bios** fixed the problem for me.... Now I'm only struggling to get the dvi out to work for my gma950 / Samsung 23" 2343bw monitor... any experience? I'm guessing the hardware is somewhere incompatible since I get no screen via dvi at boot. I also get an edid invalid message in dhe system logs.

---

### Post by aperture_kubi on 2010-02-14
> **mutrax said:**
> Had the same issue. **Increasing the video memory to 224mb in the bios** fixed the problem for me.... **Now I'm only struggling to get the dvi out to work for my gma950** / Samsung 23" 2343bw monitor... any experience? I'm guessing the hardware is somewhere incompatible since I get no screen via dvi at boot. I also get an edid invalid message in dhe system logs.

Umm, actually it seems we have the same video chipset but not the same motherboard, my nettop only has VGA out and nowhere in the bios do is see a setting for video memory.

---

### Post by mutrax on 2010-02-15
Oh,

I'm talking about the shuttle x27d barebone motherboard. Somewhere deep in the bios there was a setting for increasing this value.... the standard 128mb gave me a black border.

---

