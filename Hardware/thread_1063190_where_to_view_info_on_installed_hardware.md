---
title: "where to view info on installed hardware?"
date: 2009-02-07
forum: Hardware
---

### Post by Kain000 on 2009-02-07
Hey everyone,
I am looking for a place comperable to the view hardware area of windows.  
I want to see what hardware and firmware/driver verition I have installed and was wondering where to view that info.

this will be handy in general but right now I am looking for all the info I can view on my installed graphics card in my laptop.   

Thankyou,

---

### Post by x22 on 2009-02-07
lspci -vv

---

### Post by Kain000 on 2009-02-07
> **x22 said:**
> lspci -vv

thanks alot, 

do you know the command to output to a text file? and/or where to save that file?

---

### Post by avishalom on 2009-02-10
to output to a file
use 
command > filename

lspci -vv > list.txt

---

### Post by martinbaselier on 2009-02-10
lspci does not actually show which hardware is installed (has drivers). It only shows the available pci/pcie/agp/isa devices. "sudo lshw" will show you info on the other devices. and lsusb -v is quite useful for info on usb-devices.
lshal will show you the devices controlled by hal. 
lsmod will show you all the kernel modules, which are currently loaded. 
Among other things the kernel modules provide basic hardware support.

---

### Post by Kain000 on 2009-02-10
> **martinbaselier said:**
> lspci does not actually show which hardware is installed (has drivers). It only shows the available pci/pcie/agp/isa devices. "sudo lshw" will show you info on the other devices. and lsusb -v is quite useful for info on usb-devices.
lshal will show you the devices controlled by hal. 
lsmod will show you all the kernel modules, which are currently loaded. 
Among other things the kernel modules provide basic hardware support.

wow thanks for that info, this is really helpful.   I'm going to sound like a total noob here but what is hal?  and not the crazy killer computer. lol

---

### Post by jespdj on 2009-02-10
HAL = [Hardware Abstraction Layer](http://en.wikipedia.org/wiki/Hardware_abstraction_layer)

---

