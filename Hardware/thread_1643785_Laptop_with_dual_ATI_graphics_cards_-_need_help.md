---
title: "Laptop with dual ATI graphics cards - need help"
date: 2010-12-12
forum: Hardware
---

### Post by olembe on 2010-12-12
Hello all,

I'm REALLY sorry if this is already covered somewhere - I *did* search but couldn't find a suitable answer. 

I have an HP Pavilion DM3 laptop which is running 10.10 Maverick almost flawlessly, dual booting with Windows. The computer has dual ATI graphics cards. lspci gives:

```
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series] (rev ff)
```

However, I seem only to be using the HD 3200 card the whole time. I would like to be able to activate the HD 4300 card to get faster graphics processing. I can run Ubuntu with or without the proprietary ATI driver and both work fine. At the moment I'm running without the ATI driver and so have no xorg.conf. When I did have the ATI driver installed I had an xorg.conf file which specifically mention the 01:05.0 PCI slot, but I found that changing this to 02:00.0 stopped GDM from starting.

Any help would be very well appreciated.

---

### Post by olembe on 2010-12-17
As a mixed bump and more info message, I've noticed that although lspci lists both cards, lshw doesn't.

```
sudo lshw -C video

  *-display               
       description: VGA compatible controller
       product: RS780M/RS780MN [Radeon HD 3200 Graphics]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:18 memory:d0000000-dfffffff ioport:7000(size=256) memory:f2300000-f230ffff memory:f2200000-f22fffff
```

Does anybody know the process whereby the hardware in lspci is detected and translated into lshw? Might this give me a clue?

---

### Post by louistan3 on 2011-02-01
Any progress on this?? Im having problems as well. I have the same laptop and was wondering if I can activate the better GPU.

And was thinking this should activate the HDMI port as well..

---

### Post by olembe on 2011-02-01
No, I've not been able to make any progress and am stuck using only the 3200 card. I also suspect the more powerful card is on all the time, using power, but am not sure how to test this.

I also run Crunchbang Linux on another partition and used smxi to set up the video on that. smxi is a big script to help set up computers, and has loads of support for getting video cards working. I tried various options through there to get the more powerful card running and nothing worked. 

I'm not a totally hard-core linux guru, however, so there's still hope that somebody with more know-how could crack this!

---

### Post by realzippy on 2011-02-01
maybe [this]("http://asusm51ta-with-linux.blogspot.com/") is interesting for you...

---

### Post by olembe on 2011-02-01
Thanks, Realzippy. I had vga_switcheroo working when using the open-source radeon video driver. However, with that driver the laptop would not resume after suspend. The only driver that gives me suspend and resume functions is the fglrx driver, and this doesn't allow vga_switcheroo. It's such a bind!

---

