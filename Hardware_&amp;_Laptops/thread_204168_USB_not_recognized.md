---
title: "USB not recognized"
date: 2006-06-26
forum: Hardware &amp; Laptops
---

### Post by Jeroenverh on 2006-06-26
Hello Ubuntu users,

Last week, suddenly ubuntu stopped recognizing my usb-stick.
When I insert my usb-stick nothing happens.
Does anyone know what I can do to make it work again?

thanks in advance,

Jeroen Verhoeckx

---

### Post by Jeroenverh on 2006-06-26
using the command "sudo tail -f /var/log/messages" I get:

Jun 26 21:37:41 jeroen-desktop kernel: [17184437.752000] usb 4-5: new high speed USB device using ehci_hcd and address 


Fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0

---

### Post by Jasper Houtman on 2006-06-26
can you mount it using the disks tool? system > administration > disks
try that and see if it works

---

### Post by tonyr on 2006-06-26
...and the worst case scenario: can you verify that the stick itself is not dead?...

---

### Post by Jeroenverh on 2006-06-26
It works again!!
It didn't show up in system > administration > disks. To be sure that the stick itself wasn't dead I tried another one, nothing happens. Than I was curious what would happen when I sticked in an WLAN in the usb connector. And yes there it was; first there were no lights but when I pushed it in a little bit further the lights went on! After that I pushed in the USB-stick and the lights went on!
Thanks for the advice!

Jeroen

---

