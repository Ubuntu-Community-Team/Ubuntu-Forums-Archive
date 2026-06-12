---
title: "Problem with DLink DWM-156 USB modem on my embedded ARM board running lubuntu"
date: 2015-03-02
forum: Hardware
---

### Post by isaacarsenal on 2015-03-02
Hi,

I am trying to use D-Link DWM-156 USB modem on my ARM board to access Internet on GPRS/3G. 
This modem works fine on my Desktop PC running Ubuntu.

Here is uname -a, lsusb, lsmod, and last dmesg outputs after connecting the USB modem:
```

[ 3802.636847] ehci_irq: port change detect
[ 3802.913735] usb 4-1: new high-speed USB device number 4 using sw-ehci
[ 3803.065547] scsi5 : usb-storage 4-1:1.0
[ 3804.066729] scsi 5:0:0:0: CD-ROM            HSPA USB SCSI CD-ROM      6225 PQ: 0 ANSI: 0 CCS
[ 3804.078537] sr0: scsi3-mmc drive: 0x/0x caddy
[ 3804.084214] sr 5:0:0:0: Attached scsi CD-ROM sr0
[ 3804.296813] ehci_irq: port change detect
[ 3804.300874] usb 4-1: USB disconnect, device number 4
[ 3804.849208] ehci_irq: port change detect
[ 3804.942010] wl_notify_connect_status nothing
[ 3804.946728] wl_bss_connect_done succeeded with 64:66:b3:9e:ea:96
[ 3805.133700] usb 4-1: new high-speed USB device number 5 using sw-ehci
[ 3805.303218] option 4-1:1.2: GSM modem (1-port) converter detected
[ 3805.310969] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[ 3805.318438] option 4-1:1.3: GSM modem (1-port) converter detected
[ 3805.327160] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[ 3805.338838] option 4-1:1.4: GSM modem (1-port) converter detected
[ 3805.353576] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[ 3805.366294] option 4-1:1.5: GSM modem (1-port) converter detected
[ 3805.381170] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB3
[ 3805.396810] scsi6 : usb-storage 4-1:1.6
[ 3806.413861] scsi 6:0:0:0: Direct-Access     HSPA USB SCSI CD-ROM      6225 PQ: 0 ANSI: 0 CCS
[ 3806.437768] sd 6:0:0:0: [sda] Attached SCSI removable disk
```

```

linaro@cubietruck:~$ uname -a
Linux cubietruck 3.4.79 #4 SMP PREEMPT Wed Sep 17 14:46:01 CST 2014 armv7l armv7l armv7l GNU/Linux
```

```

linaro@cubietruck:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 2001:7d01 D-Link Corp.
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```

linaro@cubietruck:~$ lsmod
Module                  Size  Used by
option                 24501  0
usb_wwan               11895  1 option
usbserial              35182  2 option,usb_wwan
sunxi_cedar_mod         9844  0
bcmdhd                598843  0
mali                  110768  0
ump                    48909  1 mali
lcd                     3709  0
usb_storage            44824  0
sunxi_gmac             29777  0
pwm_sunxi               9154  0
```


And here is the response of several AT commands from the modem when it was connected to the embedded board:
```

AT+CSQ
+CSQ: 99, 99


OK
ATI
MTK2
MOLY.WR8.W1231.DC.WG.MP.V3


OK
AT&V
DEFAULT PROFILE


V1 E1 Q0 &C1 &D2 &K3 X4 W2 +CBST=0,0,1 +CRLP=61,61,48,6 +CIWF=0


S00:000 S02:043 S03:013 S04:010 S05:008 S32:017 S33:019 S95:000


USER PROFILE


V1 E1 Q0 &C1 &D2 &K3 X4 W2 +CBST=0,0,1 +CRLP=61,61,48,6 +CIWF=0


S00:000 S02:043 S03:013 S04:010 S05:008 S32:017 S33:019 S95:000


ACTIVE PROFILE


V1 E1 Q0 &C1 &D2 &K3 X4 W2 +CBST=0,0,1 +CRLP=61,61,48,6 +CIWF=0


S00:000 S02:043 S03:013 S04:010 S05:008 S32:017 S33:019 S95:000


OK
AT+COPS?
+COPS: 0


OK
AT+COPS=?
ERROR
```

As you can see, I get **99, 99** for **AT+CSQ **command while it is typically **25, 95** on my desktop PC.

---

