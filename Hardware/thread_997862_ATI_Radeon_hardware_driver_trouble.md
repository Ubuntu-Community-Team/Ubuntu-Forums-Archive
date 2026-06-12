---
title: "ATI Radeon hardware driver trouble"
date: 2008-11-30
forum: Hardware
---

### Post by gmstalk on 2008-11-30
When I load the hardware driver for my graphics card, my laptop (dell inspiron 1521 AMD Turion 64) screen is misaligned. The screen is shifted right, leaving a black rectangle. This rectangle is not inactive. I need to move the mouse in to this box to click on, say, the applications menu. So I blindly move the mouse and hope for the popup window to know where to click. 

Like all my other problems, this started with my upgrade to intrepid. 

I had to disable the driver to send this plea for help. So I hope the ouput below is not misleading.

 sudo lshw -C Display
  *-display               
       description: VGA compatible controller
       product: RS690M [Radeon X1200 Series]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=fglrx_pci latency=64 module=fglrx


lspci:
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]

I tried Envy and the AMD installer ([http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html))

My xorg.conf contains no resolution statements. 

Does any one have a clue how I can get this to work?

---

### Post by gmstalk on 2008-12-02
Is any one out there?

---

