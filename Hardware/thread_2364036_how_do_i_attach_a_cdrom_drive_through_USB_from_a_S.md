---
title: "how do i attach a cdrom drive through USB from a SATA/ide Combo Bridge linux"
date: 2017-06-17
forum: Hardware
---

### Post by aparolin on 2017-06-17
greetings;
I was trying to get a cd rom player/writer that i pulled out of a windows desktop to attach/mount thru a usb2 to ide/sata bridge.
The file manager does not recognize it.
Note:   cd rom is externally powered and the bridge lights are on (USB and IDE/busy); tray will not open/close
if connection is reversed, usb light on and ide light off, tray will open/close

I am using the latest gallium os.
This is what i get from terminal:


```
sudo lsusb
[sudo] password for aparolin: 
Bus 002 Device 002: ID 1b1c:1a15 Corsair 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 001 Device 005: ID 0461:4e2a Primax Electronics, Ltd 
Bus 001 Device 004: ID 0461:4e17 Primax Electronics, Ltd 
Bus 001 Device 003: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 001 Device 002: ID 8087:07dc Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


```
sudo dmesg|tail
[ 9788.373814] usb 1-5.4: Manufacturer: JMicron
[ 9788.373816] usb 1-5.4: SerialNumber: 152D203380B6
[ 9788.375208] usb-storage 1-5.4:1.0: USB Mass Storage device detected
[ 9788.376338] scsi host3: usb-storage 1-5.4:1.0
[ 9789.433665] scsi 3:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[ 9789.435302] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 9789.436818] sd 3:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 9789.439699] sd 3:0:0:0: [sdc] Asking for cache data failed
[ 9789.439709] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[ 9789.445632] sd 3:0:0:0: [sdc] Attached SCSI disk
```


am i close?
ask or post commands for any further info.
many thanx for ur help...:p
if this question has been asked before; i apologize; i did look for it...

---

### Post by efflandt on 2017-06-19
It appears that Linux seems to think that you connected a hard drive (sd device). BTW you do not need to use sudo for dmesg, and do not need it for lsusb unless using -v option for more detail (same for lspci).

This is what my LG USB optical device shows as for those commands:```
~$ lsusb
Bus 002 Device 021: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 025: ID 0e8d:1836 MediaTek Inc. Samsung SE-S084 Super WriteMaster Slim External DVD writer
Bus 002 Device 003: ID 18e3:9106 Fitipower Integrated Technology Inc 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 045e:0768 Microsoft Corp. Sidewinder X4
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

~$ dmesg | tail
[581439.420922] usb 2-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[581439.420925] usb 2-1.4: Product: MT1836 
[581439.420927] usb 2-1.4: Manufacturer: MediaTek Inc
[581439.420929] usb 2-1.4: SerialNumber: K38B11F3233     
[581439.429433] usb-storage 2-1.4:1.0: USB Mass Storage device detected
[581439.429737] scsi host7: usb-storage 2-1.4:1.0
[581440.466549] scsi 7:0:0:0: CD-ROM            HL-DT-ST DVDRAM GP40LB10  1.00 PQ: 0 ANSI: 0
[581440.488499] sr 7:0:0:0: [sr1] scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[581440.488760] sr 7:0:0:0: Attached scsi CD-ROM sr1
[581440.488858] sr 7:0:0:0: Attached scsi generic sg7 type 5
```I have a SATA drive caddy that connects with USB or eSATA, but I cannot see what that would show for a CD/DVD drive because it only accepts drives up to 3.5".

---

### Post by aparolin on 2017-06-27
thx for ur reply;
i guess i have too many connections to figure out; (chromebox to usb microhub to usb sata/ide bridge to cdrw drive); and i am not fluent enough with linux to command it to follow the data flow.
since time is money; went ahead and just bought a usb3 cdrw drive that will plug and play...
but would like to be able to mount spare peripheral drives thru sata/ide bridge in the future...
again thx,
ciao

---

