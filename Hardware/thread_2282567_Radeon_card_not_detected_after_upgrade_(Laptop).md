---
title: "Radeon card not detected after upgrade (Laptop)"
date: 2015-06-15
forum: Hardware
---

### Post by Ubugim on 2015-06-15
hello,

My laptop is unable to detect my radeon card after upgrade to ubuntu 14.04. Note that everything was fine before upgrade in ubuntu 12.04

Below is the output of lshw (only the part of radeon and intel card)

```
               resources: irq:42 ioport:3000(size=4096) memory:c0000000-c0ffffff ioport:a0000000(size=268435456)
           *-generic
                description: Unassigned class
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 0
                bus info: pci@0000:01:00.0
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list rom
                configuration: driver=radeon latency=255 maxlatency=255 mingnt=255
                resources: irq:49 memory:a0000000-afffffff memory:c0000000-c001ffff ioport:3000(size=256) memory:c0020000-c003ffff
        *-display
             description: VGA compatible controller
             product: 3rd Gen Core processor Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0


```

How do I make the system detect the card and assign class, vendor name etc .. 

Thank you

---

### Post by NoWayWin8 on 2015-06-17
What does **lspci** show for that device?

---

### Post by Ubugim on 2015-06-17
lspi | grep VGA 

```

00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Thames [Radeon HD 7500M/7600M Series] (rev ff)


```

xrandr --listproviders

```

Providers: number : 1
Provider 0: id: 0x48 cap: 0x9, Source Output, Sink Offload crtcs: 4 outputs: 5 associated providers: 0 name:Intel


```


Something seems to have gone wrong after upgrade it only detects 1 provider  and the fglrx proprietary driver can no longer detect the device.

---

### Post by Pilot6 on 2015-06-17
Install the proprietary driver by running

sudo apt-get install fglrx

---

### Post by NoWayWin8 on 2015-06-18
> **Pilot6 said:**
> Install the proprietary driver by running

sudo apt-get install fglrx

Yeah this is what you need to do. Proprietary drivers get lost after kernel/distribution upgrades and have to be reinstalled.

---

### Post by Ubugim on 2015-06-19
Yes I did that and then when I ran ati config it gave a message no supported devices found. Hence I started to dig in deeper and found the device isnt listed is xrandr --listproviders and this is definitely a problem from what I read on other posts.

---

### Post by yselim-126 on 2016-01-01
is there a way to solve this with use xorg?
I don't want to use flgrx.
because I cannot use hdmi with fglrx.

---

