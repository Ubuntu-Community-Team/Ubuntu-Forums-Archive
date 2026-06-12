---
title: "USB DAC disconnecting while switching applications"
date: 2020-08-28
forum: Hardware
---

### Post by arungn on 2020-08-28
I'm not sure if this is the right forum to post this, but here goes. I bought a FiiO BTR5 DAC/Amp and I've been getting this terrible disconnect loops every time I switch apps. I'm using it in USB mode on Ubuntu 20.04.1 LTS. Let's say I'm playing a youtube video in firefox, I stop the video and switch to Spotifyd or DeaDBeeF, the DAC disconnects and then tries to reconnect. It goes into a loop while throwing the below messages in `dmesg`

```
 
[ 9171.589745] usb 2-1-port2: unable to enumerate USB device
[ 9171.813671] usb 2-1.2: new full-speed USB device number 43 using ehci-pci
[ 9172.101645] usb 2-1.2: device descriptor read/64, error -32
[ 9172.705676] usb 2-1.2: device descriptor read/64, error -32
[ 9173.309605] usb 2-1.2: new full-speed USB device number 44 using ehci-pci
[ 9173.597922] usb 2-1-port2: attempt power cycle
[ 9174.201557] usb 2-1.2: new full-speed USB device number 45 using ehci-pci
[ 9174.617574] usb 2-1.2: device not accepting address 45, error -32

```

Some times this goes on for minutes and I have un-plug and re-plug the DAC. Other times it re-connects back in under 10 seconds. The interesting thing is that the DAP doesn't disconnect if I have one app playing audio through the DAC and I start audio in another app. Now I can hear both audio at the same time and can even stop playing audio in one and the other will keep playing without disconnecting.

```

[ 6564.157461] usb 2-1.1.1: new full-speed USB device number 18 using ehci-pci          
[ 6564.325570] usb 2-1.1.1: new high-speed USB device number 19 using ehci-pci          
[ 6564.443455] usb 2-1.1.1: New USB device found, idVendor=2972, idProduct=0047, bcdDevice= 0.2e
[ 6564.443462] usb 2-1.1.1: New USB device strings: Mfr=1, Product=3, SerialNumber=0    
[ 6564.443466] usb 2-1.1.1: Product: FiiO BTR5                                                                                                                                  
[ 6564.443469] usb 2-1.1.1: Manufacturer: FiiO                                          
[ 6564.770310] usb 2-1.1.1: 1:3 : unsupported format bits 0x100000000                   
[ 6760.623731] usb 2-1.1.1: USB disconnect, device number 19                            
[ 6760.706304] usb 2-1.1.1: new full-speed USB device number 20 using ehci-pci          
[ 6760.786332] usb 2-1.1.1: device descriptor read/64, error -32                        
[ 6761.182336] usb 2-1.1.1: device descriptor read/64, error -32                        
[ 6761.786338] usb 2-1.1.1: new full-speed USB device number 21 using ehci-pci          
[ 6762.074295] usb 2-1.1.1: device descriptor read/64, error -32                                                                                                                
[ 6762.678316] usb 2-1.1.1: device descriptor read/64, error -32                        
[ 6762.786418] usb 2-1.1-port1: attempt power cycle                                     
[ 6763.618253] usb 2-1.1.1: new high-speed USB device number 22 using ehci-pci          
[ 6763.647973] usb 2-1.1.1: New USB device found, idVendor=2972, idProduct=0047, bcdDevice= 0.2e
[ 6763.647980] usb 2-1.1.1: New USB device strings: Mfr=1, Product=3, SerialNumber=0    
[ 6763.647983] usb 2-1.1.1: Product: FiiO BTR5                                                                                                                                  
[ 6763.647987] usb 2-1.1.1: Manufacturer: FiiO                                          
[ 6763.975484] usb 2-1.1.1: 1:3 : unsupported format bits 0x100000000                   

```

`alsamixer` doesn't show volume control for this device. Below is the output from `udevadm monitor` while this happens

```

KERNEL[11553.007770] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.0/sound/card1/controlC1 (sound)
KERNEL[11553.008238] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.0/sound/card1/pcmC1D0p (sound)
UDEV  [11553.008350] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.0/sound/card1/controlC1 (sound)
KERNEL[11553.009120] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.0/sound/card1 (sound)
UDEV  [11553.009179] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.0/sound/card1/pcmC1D0p (sound)
KERNEL[11553.009864] unbind   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.0 (usb)
UDEV  [11553.010077] unbind   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.1 (usb)
KERNEL[11553.010222] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.0 (usb)
KERNEL[11553.010264] unbind   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.1 (usb)
KERNEL[11553.010312] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.1 (usb)
KERNEL[11553.010353] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.2 (usb)
KERNEL[11553.010395] unbind   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1 (usb)
KERNEL[11553.010435] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1 (usb)
UDEV  [11553.011545] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.0/sound/card1 (sound)
UDEV  [11553.016700] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.1 (usb)
UDEV  [11553.017169] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.2 (usb)
UDEV  [11553.025347] unbind   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.0 (usb)
UDEV  [11553.029337] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.0 (usb)
UDEV  [11553.035394] unbind   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1 (usb)
UDEV  [11553.062888] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1 (usb)
KERNEL[11553.188238] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1 (usb)
KERNEL[11553.189291] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.0 (usb)
KERNEL[11553.816529] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.0/sound/card1 (sound)
KERNEL[11553.816600] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.0/sound/card1/pcmC1D0p (sound)
KERNEL[11553.816669] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.0/sound/card1/controlC1 (sound)
KERNEL[11553.816717] bind     /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.0 (usb)
KERNEL[11553.816878] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.1 (usb)
KERNEL[11553.816916] bind     /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.1 (usb)
KERNEL[11553.816955] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.2 (usb)
KERNEL[11553.816999] bind     /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1 (usb)
UDEV  [11554.410603] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1 (usb)
UDEV  [11554.425683] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.2 (usb)
UDEV  [11554.429341] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.1 (usb)
UDEV  [11554.430818] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.0 (usb)
UDEV  [11554.435822] bind     /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.1 (usb)
UDEV  [11554.439145] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.0/sound/card1 (sound)
UDEV  [11554.449477] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.0/sound/card1/pcmC1D0p (sound)
KERNEL[11554.452836] change   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.0/sound/card1 (sound)
UDEV  [11554.464353] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.0/sound/card1/controlC1 (sound)
UDEV  [11554.468822] bind     /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.0 (usb)
UDEV  [11554.481093] bind     /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1 (usb)
UDEV  [11554.492521] change   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.0/sound/card1 (sound)

```

Here's the output from `lsusb`
```

[~]> lsusb
Bus 002 Device 005: ID 046d:c33b Logitech, Inc. 
Bus 002 Device 004: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 068: ID 2972:0047  
Bus 002 Device 003: ID 0bda:5409 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[~]> cat /proc/asound/cards 
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf2520000 irq 33
 1 [BTR5           ]: USB-Audio - FiiO BTR5
                      FiiO FiiO BTR5 at usb-0000:00:1d.0-1.1.1, high speed

```


The no-name entry is the DAC. I've tried swapping cables and switching ports. Any help is highly appreciated.

---

