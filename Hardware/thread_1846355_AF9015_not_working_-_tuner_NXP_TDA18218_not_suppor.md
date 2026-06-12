---
title: "AF9015 not working - tuner NXP TDA18218 not supported"
date: 2011-09-18
forum: Hardware
---

### Post by jjpcexpert on 2011-09-18
EDIT: fixed it, needed to install 2.6.38 from bpo and linux-base 3.3 from bpo
Consider this problem solved.
Still, will leave it up as a sort of minithread for people to discuss getting these things working in Debian.
And I had 0 hrs sleep!

I thought I had it, but I need to check out a different one now :oops: - By the way, need to go to bed, need to get up in 4 hrs! 

```
Sep 19 02:19:39 jack-laptop kernel: [10259.804980] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep 19 02:19:39 jack-laptop kernel: [10259.804986] usb 1-3: Product: USB2.0 DVB-T TV Stick
Sep 19 02:19:39 jack-laptop kernel: [10259.804991] usb 1-3: Manufacturer: NEWMI
Sep 19 02:19:39 jack-laptop kernel: [10259.804995] usb 1-3: SerialNumber: 010101010600001
Sep 19 02:19:39 jack-laptop kernel: [10259.805197] usb 1-3: configuration #1 chosen from 1 choice
Sep 19 02:19:40 jack-laptop kernel: [10260.177455] af9015: tuner NXP TDA18218 not supported yet
Sep 19 02:19:40 jack-laptop kernel: [10260.180837] NEWMI USB2.0 DVB-T TV Stick: Fixing fullspeed to highspeed interval: 16 -> 8
Sep 19 02:19:40 jack-laptop kernel: [10260.182014] input: NEWMI USB2.0 DVB-T TV Stick as /devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.1/input/input18
Sep 19 02:19:40 jack-laptop kernel: [10260.182342] generic-usb 0003:15A4:9016.000A: input,hidraw0: USB HID v1.01 Keyboard [NEWMI USB2.0 DVB-T TV Stick] on usb-0000:00:12.2-3/input1
Sep 19 02:23:26 jack-laptop kernel: [10486.680270] usbcore: deregistering interface driver dvb_usb_af9015
^Cjack@jack-laptop:~/bin/af/v4l-dvb$ sudo modprobe dvb_usb_af9015
^[[Ajack@jack-laptop:~/bin/af/v4l-dvb$ sudo tail -f /var/log/messages
Sep 19 02:19:39 jack-laptop kernel: [10259.804991] usb 1-3: Manufacturer: NEWMI
Sep 19 02:19:39 jack-laptop kernel: [10259.804995] usb 1-3: SerialNumber: 010101010600001
Sep 19 02:19:39 jack-laptop kernel: [10259.805197] usb 1-3: configuration #1 chosen from 1 choice
Sep 19 02:19:40 jack-laptop kernel: [10260.177455] af9015: tuner NXP TDA18218 not supported yet
Sep 19 02:19:40 jack-laptop kernel: [10260.180837] NEWMI USB2.0 DVB-T TV Stick: Fixing fullspeed to highspeed interval: 16 -> 8
Sep 19 02:19:40 jack-laptop kernel: [10260.182014] input: NEWMI USB2.0 DVB-T TV Stick as /devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.1/input/input18
Sep 19 02:19:40 jack-laptop kernel: [10260.182342] generic-usb 0003:15A4:9016.000A: input,hidraw0: USB HID v1.01 Keyboard [NEWMI USB2.0 DVB-T TV Stick] on usb-0000:00:12.2-3/input1
Sep 19 02:23:26 jack-laptop kernel: [10486.680270] usbcore: deregistering interface driver dvb_usb_af9015
Sep 19 02:23:43 jack-laptop kernel: [10503.831087] af9015: tuner NXP TDA18218 not supported yet
Sep 19 02:23:43 jack-laptop kernel: [10503.831168] usbcore: registered new interface driver dvb_usb_af9015
Sep 19 02:30:23 jack-laptop kernel: [10903.293315] usb 1-3: USB disconnect, address 11
Sep 19 02:30:26 jack-laptop kernel: [10906.052039] usb 1-3: new high speed USB device using ehci_hcd and address 12
Sep 19 02:30:26 jack-laptop kernel: [10906.190569] usb 1-3: New USB device found, idVendor=15a4, idProduct=9016
Sep 19 02:30:26 jack-laptop kernel: [10906.190578] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep 19 02:30:26 jack-laptop kernel: [10906.190585] usb 1-3: Product: USB2.0 DVB-T TV Stick
Sep 19 02:30:26 jack-laptop kernel: [10906.190589] usb 1-3: Manufacturer: NEWMI
Sep 19 02:30:26 jack-laptop kernel: [10906.190598] usb 1-3: SerialNumber: 010101010600001
Sep 19 02:30:26 jack-laptop kernel: [10906.190800] usb 1-3: configuration #1 chosen from 1 choice
Sep 19 02:30:26 jack-laptop kernel: [10906.566548] af9015: tuner NXP TDA18218 not supported yet
Sep 19 02:30:26 jack-laptop kernel: [10906.569763] NEWMI USB2.0 DVB-T TV Stick: Fixing fullspeed to highspeed interval: 16 -> 8
Sep 19 02:30:26 jack-laptop kernel: [10906.571045] input: NEWMI USB2.0 DVB-T TV Stick as /devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.1/input/input19
Sep 19 02:30:26 jack-laptop kernel: [10906.571351] generic-usb 0003:15A4:9016.000B: input,hidraw0: USB HID v1.01 Keyboard [NEWMI USB2.0 DVB-T TV Stick] on usb-0000:00:12.2-3/input1
```
So even though I now have it working, bang goes my hopes of having any telly to watch!
Can someone point me in the right direction (for Debian) please?
Help needed or else I won't have telly to watch this afternoon either.
I might not have telly to watch anyway because my aerial is indoor :(

---

