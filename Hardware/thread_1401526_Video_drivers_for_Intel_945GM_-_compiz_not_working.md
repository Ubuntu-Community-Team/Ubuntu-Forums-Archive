---
title: "Video drivers for Intel 945GM - compiz not working"
date: 2010-02-08
forum: Hardware
---

### Post by opto09 on 2010-02-08
I'm trying to get compiz working on my laptop but I can't seem to get it going. Compiz worked fine under jaunty but on upgrade it cannot be enabled (selecting normal visual effects in Appearance Preferences returns a "Desktop effects could not be enabled" error).

Details:
I'm using a Dell Inspiron 640m laptop.
```

$lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
```

```
$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 
```

Things I've tried:
Reinstalling xserver-xorg-video-intel
Intalling any xserver-xorg-video-xxx i could find (probably not good idea)
Looked around dell.com for linux news but all I could find was an ISO for 9.04.

If anyone could give any help at all I'd much appreciate it!

---

### Post by Chitown on 2010-02-08
I had the same issue until I updated my system, As of the moment I am using Compiz.

*-display:0             
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:eff00000-eff7ffff ioport:eff8(size=8) memory:d0000000-dfffffff(prefetchable) memory:efec0000-efefffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:eff80000-efffffff

---

### Post by opto09 on 2010-08-19
Hmm any chance you could show me how to do that? I've got Lucid installed now but clicking system->preferences->appearance and selecting normal visual effects gives me "visual effects could not be enabled".

---

### Post by varunendra on 2010-08-21
> **opto09 said:**
> Hmm any chance you could show me how to do **that**?
....what? If you mean 'how to **Update**', goto **System>Administration>Update Manager**.

I got similar problem a few days ago (with Intel 865 chipset). Reinstalling driver didn't help, but reinstalling compiz metapackage (without uninstalling first) did!

---

### Post by opto09 on 2010-08-24
No not that... I know how to update my system thanks. I meant what updates Chitown did? What is the xorg intel driver? The compiz package?

---

### Post by varunendra on 2010-08-25
In update Manager, the proposed updates are listed (make sure all kind of update options are checked in "**Update Manager>settings**"). You can choose all of them or selectively or can even ignore all of them if you wish. I assume that you already know this much (even more....).

So I'd suggest to check for all kind of updates (Upd.Man>Settings, as suggested above), and go with the ones that are seemingly related with graphics or compiz or the ones you are not sure about.

xorg-intel driver is graphics driver for intel chipset family. You can install/update it via synaptic.

[**Most Imp.:** To cover max. range of drivers/updates, make sure to tick all kind of repositories under 'Software Sources' and **refresh** the list in synaptic.]

---

