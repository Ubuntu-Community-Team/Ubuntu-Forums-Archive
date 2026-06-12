---
title: "Light Brightness Problem(Too Dark)"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by icechen1 on 2007-10-19
Hi,I am using Ubuntu 7.10(Gusty)
I found a problem when I try to adjust the screen brightness,the screen just turn black(you can see a little little) and i have to use the buttons in my keyboard to adjust the brightness to max to see the desktop again.

I found there is a problem when use battery too,i have to use the max brightness to see anything.

I am using a Gateway MX6214.

Battery Info(as seen in lshw):
  *-battery
       description: Lithium Ion Battery
       product: MAL32b
       vendor: SANYO
       physical id: 1
       version: 2006/08/04
       serial: 50702
       slot: In the Back side
       capacity: 4800mWh
       configuration: voltage=11.1V

Video card info:
 *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga bus_master cap_list
             configuration: latency=0
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

Help Please.

---

### Post by icechen1 on 2007-10-19
Another Problem,The laptop now can't estimate the remaining time but it worked in feisty.

---

### Post by icechen1 on 2007-10-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/136693](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/136693) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This might be related to a bug at [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/136693](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/136693)

---

