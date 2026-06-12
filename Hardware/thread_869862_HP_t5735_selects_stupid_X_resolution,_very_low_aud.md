---
title: "HP t5735 selects stupid X resolution, very low audio volume"
date: 2008-07-25
forum: Hardware
---

### Post by blackhelicopter on 2008-07-25
Hi

I've got a couple of brand spanking HP t5735 thin clients with Samsung 940B monitors, on which I'd like to run LTSP 5 from an Ubuntu 8.04.1 server.

When I boot these terminals with the monitors connected to the DVI interface, for some reason, X comes up in 1280x800 instead of the monitor's native 1280x1024. This behaviour does not occur under HP's default debian install. It occurs both with the LTSP image and the live CD.

I've tried copying HP's xorg.conf into the image, and using the following lts.conf line, to no avail.

```

X_MODE_0 = 1280x1024 108.00  1280 1328 1440 1688  1024 10 25 1028 1066 +hsync +vsync
```

When I use the VGA interface, it works OK. I'd rather not, though, thanks to the inferior image quality.

Any ideas as to how to persuade these terminals to select the correct resolution on startup?

Additionally, under LTSP, the audio volume from the server is very quiet, even while cranked right up using the server-side controls. Any ideas?

Cheers

---

### Post by chri on 2009-01-11
Hi,

we have exactly the same ThinClients but other monitors (Dell E2209W) and I've experienced exactly the same problem. If the monitor is connected to the VGA port, the monitor runs with 1680x1050 (but with bad quality, some flickering, looks fuzzy). If the monitor is connected to the DVI port, the resolution is stuck at 1280x768 and no adjustments can be done (but there is no flickering).

I run this LTSP server as a virtual machine with vmware-server 2.0 on a Ubuntu server 8.04. The LTSP is actually Kubuntu 8.04 with the ltsp-server package installed.

The problem goes even further: In KDE the Display settings module is missing if the monitor is connected to the DVI port, instead an error message assumes that the corresponding module is not correctly installed/missing. When using the VGA port the module is present and I can change the resolution.

I have tested it with other monitors (21" Benq, 19" Samsung, both TFT) but the same problem occurs.

Is the display quality always that bad if it is connected to the VGA port or is the VGA interface of the HP Thinclient crappy?

The sound is not working at all, but I have not figured out yet if this may be a KDE, HP, VMware, etc. specific problem.

Cheers,
chri

---

