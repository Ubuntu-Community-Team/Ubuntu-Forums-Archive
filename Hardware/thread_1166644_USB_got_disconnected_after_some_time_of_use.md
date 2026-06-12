---
title: "USB got disconnected after some time of use"
date: 2009-05-21
forum: Hardware
---

### Post by tuxmsn on 2009-05-21
All.. I have a problem over my laptop. When i plug my 3g modem, after some time of use, it got disconnected.

dmesg shows the following:

[ 2153.000527] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 2153.000566] option 1-2:1.0: device disconnected
[ 2153.000773] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 2153.000807] option 1-2:1.1: device disconnected
[ 2153.001128] option 1-2:1.3: device disconnected
[ 2153.117129] usb 1-2: reset high speed USB device using ehci_hcd and address 6
[ 2153.410765] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[ 2168.236115] usb 1-2: device descriptor read/64, error -110
[ 2183.452127] usb 1-2: device descriptor read/64, error -110
[ 2183.668137] usb 1-2: reset high speed USB device using ehci_hcd and address 6
[ 2198.780192] usb 1-2: device descriptor read/64, error -110
[ 2213.996425] usb 1-2: device descriptor read/64, error -110
[ 2214.212181] usb 1-2: reset high speed USB device using ehci_hcd and address 6
[ 2224.620172] usb 1-2: device not accepting address 6, error -110
[ 2224.736048] usb 1-2: reset high speed USB device using ehci_hcd and address 6
[ 2235.145100] usb 1-2: device not accepting address 6, error -110
[ 2235.145167] usb 1-2: USB disconnect, address 6
[ 2235.149860] scsi 3:0:0:0: Device offlined - not ready after error recovery
[ 2235.156106] scsi 3:0:0:0: rejecting I/O to dead device
[ 2235.156130] scsi 3:0:0:0: rejecting I/O to dead device
[ 2235.156145] scsi 3:0:0:0: rejecting I/O to dead device
[ 2235.156157] scsi 3:0:0:0: rejecting I/O to dead device
[ 2235.156166] scsi 3:0:0:0: [sdb] READ CAPACITY failed
[ 2235.156170] scsi 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 2235.156181] scsi 3:0:0:0: [sdb] Sense not available.
[ 2235.156192] scsi 3:0:0:0: rejecting I/O to dead device
[ 2235.156201] scsi 3:0:0:0: [sdb] Write Protect is off
[ 2235.156206] scsi 3:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 2235.156212] scsi 3:0:0:0: [sdb] Assuming drive cache: write through
[ 2235.212585] scsi 3:0:0:0: rejecting I/O to dead device
[ 2235.278601] usb 1-2: new high speed USB device using ehci_hcd and address 7

-
my lsusb:

root@saturn:~# lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 19d2:0031  
Bus 001 Device 002: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@saturn:~# 

''
Any idea????

---

### Post by GeorgeVita on 2009-05-23
Hi **tuxmsn**,
my 3G modem (ZTE MF636) is reported as yours **19d2 : 0031** and I have not faced this prooblem.

What is your Ubuntu version, how did you configured the system to "see" your modem (if you did any file modification) and how are you connecting?

I could do some tests to find out.
Regards,
George

---

### Post by tuxmsn on 2009-05-24
Hi!, Well I have the ZTE MF636 indeed. Im running the latest ubuntu version (9.10 jaunty)

Linux saturn 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
root@saturn:~# 

I read in several forums that to make the modem visible to ubuntu i should do connect trhough telenet to the modem and do a at+zcdrun=8 (that would disable modem drivers autorun) i did it and the modem became visible. However im having this "disconnection problem"

I did no other changes on my ubuntu or the modem itself.

Thanks for the help

---

### Post by GeorgeVita on 2009-05-24
Hi again! As **19d2 : 0031** is not included in the HAL info file, if you add it it is possible to become more steady.

Try the following:

[B]sudo gedit /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
[/B]
**Search** (ctrl-F) for **19d2**, after line "<!-- ZTE MF628 HSDPA USB dongle -->" **change** "usb.product_id" from "0015" to "**0031**"
**Save** and **Exit** from gedit

Boot with the modem attached and connect. If you have more than one SAME selections to connect (provider's name) click on the LAST one.

Check and inform me if it is better.

Regards,
George

---

### Post by tuxmsn on 2009-05-25
Well I changed the product ID accordingly:

  <!-- ZTE MF628 HSDPA USB dongle -->
        <match key="@info.parent:usb.product_id" int="0x0031">
          <match key="@info.parent:usb.interface.number" int="3">
            <append key="modem.command_sets" type="strlist">GSM-07.07</append>
            <append key="modem.command_sets" type="strlist">GSM-07.05</append>
          </match>
        </match>


i will check and i let u know.

---

