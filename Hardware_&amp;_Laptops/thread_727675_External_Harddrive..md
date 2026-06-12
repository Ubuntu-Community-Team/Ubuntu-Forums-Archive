---
title: "External Harddrive."
date: 2008-03-18
forum: Hardware &amp; Laptops
---

### Post by KaiXXV on 2008-03-18
Alright I'm new to the Linux scene so please excuse me if this is a simple problem.  I've been browsing the web for a while trying to figure out the solution to my problem.  It seems that my external HDD is no longer recognized by Ubuntu.  I've looked at using the sudo fdisk -l and sudo lshw neither of which seem to indicate it exists.  The light for power is on.  My Windows machine detects it and it works just fine there.  I do recall having to use an odd command when I installed Ubuntu it was something like noapic in the GRUB menu on the live CD.  Any advice would be lovely!  
 ```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x282d282d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9376    75312688+  83  Linux
/dev/sda2            9377        9729     2835472+   5  Extended
/dev/sda5            9377        9729     2835441   82  Linux swap / Solaris
 
```
```
 *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
 
```

---

### Post by logos34 on 2008-03-18
Boot ubuntu with the usb unplugged.  Then connect it and turn it on.  Is it detected now?

---

### Post by KaiXXV on 2008-03-18
Sadly no.  However, it did continue spinning for a while which gives me hope!  Oh, and just for fun I decided to boot it with it plugged in and got a -110 error on the device.

---

