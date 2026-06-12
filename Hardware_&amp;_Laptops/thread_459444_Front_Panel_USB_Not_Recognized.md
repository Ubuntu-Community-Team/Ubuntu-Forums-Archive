---
title: "Front Panel USB Not Recognized"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by mini_g on 2007-05-30
System: Dell Optiplex GX240
OS: Ubuntu 7.10
Kernel: 2.6.20-15-386 (I don't wish to upgrade unless necessary due to modem driver)
Replicable: Yes, it is also happening to a homebuild box that used to be able to use the front panel under 6.04.
Note: The audio-out port on both work.

When I plug in any USB devices into my front ports under the above system, they are not recognized, however the rear ports do happen to work.

Here's the "lspci -v" output with only the USB portions:
```

00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12) (prog-if 00 [UHCI])
        Subsystem: Dell Optiplex GX240
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at ff80 [size=32]

00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12) (prog-if 00 [UHCI])
        Subsystem: Dell Optiplex GX240
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at ff60 [size=32]

```

---

### Post by strider_mt2k on 2007-08-24
I was just doing a search on this subject because I also have a GX240 and it's front USB ports aren't working under Feisty Fawn.

My only testing was in the form of putting WinXP on the thing and seeing the ports work.

I'm surprised there aren't more threads about this since there are a ton of these old machines floating around on eBay (where I found mine) and they run Ubuntu like a champ (for the most part).

I know it's an old post, but this might be better if it was moved to the Dell section.

---

