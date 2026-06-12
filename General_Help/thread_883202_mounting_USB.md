---
title: "mounting USB"
date: 2008-08-07
forum: General Help
---

### Post by Lodui on 2008-08-07
I'm trying to mount my USB. Plug and play isn't working.

Please let me know.

---

### Post by spiderbatdad on 2008-08-07
```
dmesg | tail
```after plugging it in and removing it.

Also what is it, storage, or some other device? Also while it's plugged in:
```
lsusb
```post results of those two commands here.

---

### Post by Lodui on 2008-08-07
It's a digi camcorder

dmesg is while plugged in:

[25753.535337] CPU0 attaching sched-domain:
[25753.535348]  domain 0: span 03
[25753.535353]   groups: 01 02
[25753.535360] CPU1 attaching sched-domain:
[25753.535364]  domain 0: span 03
[25753.535368]   groups: 02 01
[25762.514063] usb 5-5: new high speed USB device using ehci_hcd and address 4
[25762.648372] usb 5-5: configuration #1 chosen from 1 choice
[25762.648886] hub 5-5:1.0: USB hub found
[25762.649231] hub 5-5:1.0: 4 ports detected

dmesg while removed is:

[25783.052236]    groups: 03
[25856.205212] CPU0 attaching NULL sched-domain.
[25856.205222] CPU1 attaching NULL sched-domain.
[25856.225125] CPU0 attaching sched-domain:
[25856.225136]  domain 0: span 03
[25856.225140]   groups: 01 02
[25856.225148] CPU1 attaching sched-domain:
[25856.225152]  domain 0: span 03
[25856.225156]   groups: 02 01
[25891.048522] usb 5-5: USB disconnect, address 4

lsusb is:

Bus 005 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by spiderbatdad on 2008-08-07
mmm. it doesn't appear to be recognized. Maybe attach your entire dmesg by right clicking the following file and creating an archive of it...upload the archive here, or use a pastebin.
I'm thinking you may need the boot option irqpoll to get the kernel to see this device.```
dmesg > ~/Desktop/dmesg.txt
```

---

### Post by Lodui on 2008-08-07
irqpoll eh? I don't specifically recall that boot option. 

Hmmm...

---

### Post by Lodui on 2008-08-07
Er, how do I create an archive of that file I just created?

Thanks BTW.

---

### Post by Lodui on 2008-08-07
There we go:

[http://www.pastebin.ca/1095164](http://www.pastebin.ca/1095164)

---

### Post by spiderbatdad on 2008-08-07
wow. did you run the command as I posted above? I've never seen a dmesg like that...at least not so incomplete.

you can add irqpoll to the end of the kernel line in /boot/grub/menu.lst also delete the quiet splash option. Or try a one time boot, and at the grub menu, at startup, press e to edit, then move the highlighted line to the kernel line hit e again, and use arrow key to go to the end of the line. Delete --quiet splash and add irqpoll, hit enter and then b to boot.

---

### Post by Lodui on 2008-08-07
Yeah, that was the entire content of the file.

I've got gedit /boot/grub open. I googled it. You want me to add this?:

kernel /vmlinuz-2.4.21-20.EL ro root=LABEL=/ hda=ide-scsi irqpoll



Also, I'm not sure what exactly too delete with the quiet splash. I see it twice. The contents of /boot/grub are:

[http://pastebin.ca/1095181](http://pastebin.ca/1095181)

Thanks.

---

### Post by spiderbatdad on 2008-08-07
```
#
## ## End Default Options ##
#
 
#
title      Ubuntu 8.04, kernel 2.6.24-16-generic
#
root        (hd0,0)
#
kernel    /boot/vmlinuz-2.6.24-16-generic root=UUID=9942309f-(more #'s) ro** irqpoll**
#
initrd    /boot/initrd.img-2.6.24-16-generic
#
quiet
```
Just like that...use backspace to delete.
You can also try a one time boot with the option, as I described above, without editing this file.

---

