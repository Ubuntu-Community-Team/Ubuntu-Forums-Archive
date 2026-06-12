---
title: "Fujitsu Siemens Amilo L700 Series"
date: 2006-08-05
forum: Hardware &amp; Laptops
---

### Post by butlershouse on 2006-08-05
This is a fairly recent laptop from FJ and out of the box and with the current Ubutnu release 6.06 pretty much everything bar the USB was working. 

I ran all the usuall updates and have opted for the 2.6.15-26-686 kernels and modules but to no avail. When plugging in usb devices I see.


Aug  5 15:08:24 localhost kernel: [17180099.708000] usb 4-3: device not accepting address 4, error -110
Aug  5 15:08:24 localhost kernel: [17180099.820000] usb 4-3: new high speed USB device using ehci_hcd and address 5



Booting with nopic isnt helping since usb just stops altogether. I am wondering about a bios firmware update but FJ seem to not have released any and I am wondering about the laptop fan as now that I am typinh my wrist si getting a little cooked ! ...

Any suggestions for getting the iPod recognised here would be appreciatted !

Thanks

Nik

---

### Post by butlershouse on 2006-08-05
scratch some of that ....

Using noapic ( instead of nopaic [ spelling ] ) has worked for the 686 modules. In as far as the ipod is now seen by rythm box! Meanwhile the onboard network card which is spotted in the -23 version of the kernel above is not seen in the -26 .

thanks

---

### Post by butlershouse on 2006-08-05
Okay ... so heres an extract from my menu.lst

sudo vi /boot/grub/menu.lst

title           Ubuntu, kernel 2.6.15-26-686
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/hda2 ro quiet splash noapic
initrd          /boot/initrd.img-2.6.15-26-686
savedefault
boot


The key line is in kernel

I found the usb working okay and banshee spots the ipod and plays the content. So back to getting amarok working as I would expect it to.

---

