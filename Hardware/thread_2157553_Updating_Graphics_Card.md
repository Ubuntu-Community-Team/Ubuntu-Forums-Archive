---
title: "Updating Graphics Card"
date: 2013-06-25
forum: Hardware
---

### Post by regice9 on 2013-06-25
Hello. I recently found out when doing some work on my laptop that my graphics card is out of date. After searching for a little while, I found that this can be taken care of by going to the Additional Drivers option in System Settings. In all of the examples that I have seen, usually the window that appears has data about the drivers and such. When I open mine, however, the place where the drivers would appear is blank, and the only text that can be seen is the usual message about how there are no proprietary drivers. At first, I believed that in some completely impossible way, I didn't have a graphics card, and yet after using the "lspci | grep VGA" and "sudo lshw -C video" commands, I got data of a graphics card. Most probably I am making a really simple mistake with this, but I don't quite know what to make of this predicament.

Resulting data from commands:
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

 *-display:0             
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:dc100000-dc17ffff ioport:1800(size=8) memory:c0000000-cfffffff memory:dc200000-dc23ffff
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
       resources: memory:dc180000-dc1fffff

---

### Post by Cheesemill on 2013-06-25
The drivers for Intel graphics cards are already built in to the kernel, you don't need to use 'Additional Drivers' to install them.

What makes you think that your graphics drivers are out of date?

---

### Post by regice9 on 2013-06-25
Not entirely sure why, but apparently I cannot run OpenGL 2.1.

---

### Post by Cheesemill on 2013-06-25
The Intel 945GM graphics chip only supports OpenGL version 1.4.

This is a hardware limitation of the chip itself and something that isn't possible to change by using a different driver.

---

