---
title: "USB is not being detected properly, or rather assigned!?!"
date: 2017-05-12
forum: Hardware
---

### Post by p2bc on 2017-05-12
On a fresh install, I plug a USB thumb drive in that has a few script to help finish the install, and it is mount sporadically at best.

The first time I thought it was because I might not have ejected it properly from the other computer, which I know should not make a difference, but tried it anyways. Plugged it back into the first computer, ejected it, and plugged in into the fresh install , and it work.

After restarting the computer to make sure the new setting will persisted on reboot, just to be safe, I re-insert the thumb drive and nothing. Being a created of habit and I guess superstition, I know I know should make a difference, I bring in back to the first computer, insert, eject, and insert into fresh install; nothing.

I do:
```

# fdisk -l
...

```

Not listed, other that the main drive "/dev/sda".

I try:
```

# lsusb
...
Lexar Media, Inc. JumpDrive V10
...

```

And it is there!
 I unplug it, do "lsusb" again it is gone, so it gone.
 Plug in again it is back. Awesome! 
Do "fdisk -l", no entries other than main drive.
Plug a second thumb drive, an external HD, and to "lsusb", all show up, but not auto mount, or register to "/dev/..." which I check with a "fdisk -l".
So I checked the logs:
```

tail -n 20 /var/log/syslog
May 12 19:21:27 dream-machine kernel: [ 3592.228718] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
May 12 19:21:27 dream-machine kernel: [ 3592.228725] usb 1-1: Product: USB Flash Drive
May 12 19:21:27 dream-machine kernel: [ 3592.228730] usb 1-1: Manufacturer: Lexar
May 12 19:21:27 dream-machine kernel: [ 3592.228735] usb 1-1: SerialNumber: AAOLN42AYYB4AFOE
May 12 19:21:27 dream-machine kernel: [ 3592.229504] usb 1-1: ep 0x81 - rounding interval to 128 microframes, ep desc says 255 microframes
May 12 19:21:27 dream-machine kernel: [ 3592.229518] usb 1-1: ep 0x2 - rounding interval to 128 microframes, ep desc says 255 microframes
May 12 19:21:27 dream-machine mtp-probe: checking bus 1, device 16: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-1"
May 12 19:21:27 dream-machine mtp-probe: bus: 1, device: 16 was not an MTP device
May 12 19:33:19 dream-machine cinnamon-screensaver-pam-helper: pam_ecryptfs: seteuid error
May 12 19:33:23 dream-machine kernel: [ 4308.477089] usb 1-5.2: USB disconnect, device number 15
May 12 19:33:51 dream-machine kernel: [ 4336.323196] usb 1-5.2: new high-speed USB device number 17 using xhci_hcd
May 12 19:33:52 dream-machine kernel: [ 4336.932145] usb 1-5.2: New USB device found, idVendor=05dc, idProduct=a815
May 12 19:33:52 dream-machine kernel: [ 4336.932172] usb 1-5.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
May 12 19:33:52 dream-machine kernel: [ 4336.932190] usb 1-5.2: Product: USB Flash Drive
May 12 19:33:52 dream-machine kernel: [ 4336.932205] usb 1-5.2: Manufacturer: Lexar
May 12 19:33:52 dream-machine kernel: [ 4336.932218] usb 1-5.2: SerialNumber: AATX6JGXXSTXJN3M
May 12 19:33:52 dream-machine kernel: [ 4336.933437] usb 1-5.2: ep 0x81 - rounding interval to 128 microframes, ep desc says 255 microframes
May 12 19:33:52 dream-machine kernel: [ 4336.933470] usb 1-5.2: ep 0x2 - rounding interval to 128 microframes, ep desc says 255 microframes
May 12 19:33:52 dream-machine mtp-probe: checking bus 1, device 17: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5.2"
May 12 19:33:52 dream-machine mtp-probe: bus: 1, device: 17 was not an MTP device 

```

So I am not familiar with a "MTP Device", not sure what the relevance.

Anyways, need to get this fix, and I need to insure it does not do this for the friend that the computer belongs to, that I am converting to Linux.

Any help would be appreciated, as to how to fix this, and make sure it doesn't happen again, or even sporadically, some time it mount and sometimes it doesn't.


Thanks in advance.

---

### Post by p2bc on 2017-05-12
I forgot to mention.

dmesg:
```

...
[  929.429873] usb 1-1: USB disconnect, device number 8 
[  933.641899] usb 1-1: new high-speed USB device number 10 using  xhci_hcd 
[  938.753847] usb 1-1: device descriptor read/64, error -110                                             <====== Error ======
[  953.969064] usb 1-1: device descriptor read/64, error -110                                             <====== Error ======
[  954.185021] usb 1-1: new high-speed USB device number 11 using  xhci_hcd 
[  959.297029] usb 1-1: device descriptor read/64, error -110                                             <====== Error ====== 
[  974.512270] usb 1-1: device descriptor read/64, error -110                                             <====== Error ====== 
[  974.728092] usb 1-1: new high-speed USB device number 12 using  xhci_hcd 
[  979.743776] usb 1-1: device descriptor read/8, error -110                                              <====== Error ======
[  984.863891] usb 1-1: device descriptor read/8, error -110                                              <====== Error ====== 
[  985.079693] usb 1-1: new high-speed USB device number 13 using  xhci_hcd 
[  990.095579] usb 1-1: device descriptor read/8, error -110                                              <====== Error ======  
[  995.215440] usb 1-1: device descriptor read/8, error -110                                              <====== Error ====== 
[  995.319049] usb usb1-port1: unable to enumerate USB device 
[ 1556.138431] usb 1-5.2: new high-speed USB device number 14 using  xhci_hcd 
[ 1556.747005] usb 1-5.2: New USB device found, idVendor=05dc,  idProduct=a815 
[ 1556.747030] usb 1-5.2: New USB device strings: Mfr=1, Product=2,  SerialNumber=3 
[ 1556.747040] usb 1-5.2: Product: USB Flash Drive 
[ 1556.747049] usb 1-5.2: Manufacturer: Lexar 
[ 1556.747056] usb 1-5.2: SerialNumber: AATX6JGXXSTXJN3M 
[ 1556.748241] usb 1-5.2: ep 0x81 - rounding interval to 128  microframes, ep desc says 255 microframes 
[ 1556.748261] usb 1-5.2: ep 0x2 - rounding interval to 128 microframes,  ep desc says 255 microframes 
[ 1621.989425] usb 1-5.2: USB disconnect, device number 14 
[ 1636.268159] usb 1-5.2: new high-speed USB device number 15 using  xhci_hcd 
[ 1636.876122] usb 1-5.2: New USB device found, idVendor=05dc,  idProduct=a815 
[ 1636.876149] usb 1-5.2: New USB device strings: Mfr=1, Product=2,  SerialNumber=3 
[ 1636.876166] usb 1-5.2: Product: USB Flash Drive 
[ 1636.876181] usb 1-5.2: Manufacturer: Lexar 
[ 1636.876194] usb 1-5.2: SerialNumber: AATX6JGXXSTXJN3M 
[ 1636.877636] usb 1-5.2: ep 0x81 - rounding interval to 128  microframes, ep desc says 255 microframes 
[ 1636.877671] usb 1-5.2: ep 0x2 - rounding interval to 128 microframes,  ep desc says 255 microframes 
[ 3592.040611] usb 1-1: new high-speed USB device number 16 using  xhci_hcd 
[ 3592.228705] usb 1-1: New USB device found, idVendor=05dc,  idProduct=a81d 
[ 3592.228718] usb 1-1: New USB device strings: Mfr=1, Product=2,  SerialNumber=3 
[ 3592.228725] usb 1-1: Product: USB Flash Drive 
[ 3592.228730] usb 1-1: Manufacturer: Lexar 
[ 3592.228735] usb 1-1: SerialNumber: AAOLN42AYYB4AFOE 
[ 3592.229504] usb 1-1: ep 0x81 - rounding interval to 128 microframes,  ep desc says 255 microframes 
[ 3592.229518] usb 1-1: ep 0x2 - rounding interval to 128 microframes,  ep desc says 255 microframes 
[ 4308.477089] usb 1-5.2: USB disconnect, device number 15 
[ 4336.323196] usb 1-5.2: new high-speed USB device number 17 using  xhci_hcd 
[ 4336.932145] usb 1-5.2: New USB device found, idVendor=05dc,  idProduct=a815 
[ 4336.932172] usb 1-5.2: New USB device strings: Mfr=1, Product=2,  SerialNumber=3 
[ 4336.932190] usb 1-5.2: Product: USB Flash Drive 
[ 4336.932205] usb 1-5.2: Manufacturer: Lexar 
[ 4336.932218] usb 1-5.2: SerialNumber: AATX6JGXXSTXJN3M 
[ 4336.933437] usb 1-5.2: ep 0x81 - rounding interval to 128  microframes, ep desc says 255 microframes 
[ 4336.933470] usb 1-5.2: ep 0x2 - rounding interval to 128 microframes,  ep desc says 255 microframes 

```

---

