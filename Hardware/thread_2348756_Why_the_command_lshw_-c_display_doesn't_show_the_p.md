---
title: "Why the command lshw -c display doesn't show the product name ?"
date: 2017-01-06
forum: Hardware
---

### Post by fbio7 on 2017-01-06
O.S Ubuntu 14.04.2 LTS
Dell inspiron 5557 - pré install 
I7 6500U

why the product name doesn't show after do the command lshw -c display ?

results


Eu:~$ sudo lshw -c display
[sudo] password for fabio: 
  *-display               
       description: VGA compatible controller
**       product: Intel Corporation**
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915_bpo latency=0
       resources: irq:133 memory:d4000000-d4ffffff memory:b0000000-bfffffff ioport:f000(size=64)
  *-display
       description: 3D controller
**       product: NVIDIA Corporation**
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:135 memory:d2000000-d2ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:d3000000-d307ffff

---

### Post by Keith_Helms on 2017-01-07
Because the product name is created by a marketing committee and slapped on the box and is not burned into the hardware itself.

---

### Post by mörgæs on 2017-01-07
How does the same command work in a live boot of 16.10?

---

### Post by gordintoronto on 2017-01-07
I use lshw slightly differently:
cd Desktop
sudo lshw -html > config.htm

Then I double-click on the file on my dekstop, and the display product name does appear in the browser.

---

### Post by Yellow Pasque on 2017-01-07
Run this:
```
sudo update-pciids; sudo update-usbids
```

Then, try lshw again.

---

### Post by fbio7 on 2017-01-07
Keith I'm looking for hardware information in this case intel corporation didn't help. I saw on the internet people who posted product name using the command: lshw -c display but in my case It didn't work, do you know why ?

Gordin that's a interesting form of view the results of the command lshw. 

I found some more information in the folder /proc and a linux user for other forum recomend inxi tool. 

thanks guys.

---

### Post by Yellow Pasque on 2017-01-07
> I saw on the internet people who posted product name using the command: lshw -c display but in my case It didn't work, do you know why ?

Because you're running an older version of Ubuntu on relatively newer hardware. Your local copy of the PCI database names is out-of-date, and you need to run the command I gave you in my previous post.

---

### Post by fbio7 on 2017-01-09
Hi Temujin I did the commands and worked very well. Thanks a lot.

---

