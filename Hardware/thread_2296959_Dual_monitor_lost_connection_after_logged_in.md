---
title: "Dual monitor lost connection after logged in"
date: 2015-09-30
forum: Hardware
---

### Post by Amy_Lin on 2015-09-30
Hello everyone,
I'm kind of new to Ubuntu.. Need your help plz
my computer is Acer aspire with another monitor is BenQ

Couple days ago, I got another monitor, and connect it to my laptop directly, everything seems pretty good.
But someday when I press Fn+F5(which changes whether to show on one or two monitors)
press it for 4 times and it changes to "only display on my laptop monitor" mode, and never come back...

So I tried to reboot my computer, 
I figured out that it can only display on dual monitor before logged in.
Ever since I logged in, another monitor suddenly turned black..

(( I'm no so sure whether the problem may be related to "apt-get dist-upgrade" which I've done yesterday, 
because it seemed like update many things about kernel(?
ps. I've "apt-get autoremove linux-image-...-generic" to get old stable version of kernel back.


Here is my result of lspci and lshw
```
$ lspci | grep -i vga
       00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)

```

```
$ sudo lshw -C video  *-display               
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:60 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:4000(size=64)



```

Thank you very much!!

---

