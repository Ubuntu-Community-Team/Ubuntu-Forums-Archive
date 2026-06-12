---
title: "Bluetooth PCMCIA issues on dell latitude"
date: 2006-01-19
forum: Hardware &amp; Laptops
---

### Post by Dr. Blues on 2006-01-19
i am running breezey on a dell latitude cpx. also using a billionton bluetooth 56k modem. with usb dongle i have no problems. but when i try to use the bluetooth PCMCIA (billionton PCBTC1) things go wrong. if the card is in the slot at boot, bluetooth does not detect it and its light does not flash. cardctl ident does detect it. if the card is inserted after boot and bluez-utils is restarted, bluetooth detects and starts using it. i need the usb port for my ext hard drive and it's a pain to go through this procedure to get online. i suspect the probem may be with the bluez-utils file. it has this line in it:

UART_CONF=/etc/bluetooth/uart

however, no such file exists.  but why does it work if the card is inserted after boot? my plan is to download bluez-utils from bluez.org and try to find /etc/bluetooth/uart.

here is a copy the current session:

simon9x@RED-DWARF:~$ hcitool dev
Devices:
        hci0    00:10:60:A8:A1:58
simon9x@RED-DWARF:~$ hciconfig hci1 up
Can't get device info: No such device
simon9x@RED-DWARF:~$ hcitool scan
Scanning ...
        00:10:60:30:90:85       Bluetooth Modem
simon9x@RED-DWARF:~$ rfcomm
rfcomm0: 00:10:60:30:90:85 channel 1 clean
simon9x@RED-DWARF:~$ sudo hciattach ttyS0 any 115200
Password:
simon9x@RED-DWARF:~$ sudo hciconfig up
hci0:   Type: USB
        BD Address: 00:10:60:A8:A1:58 ACL MTU: 192:8 SCO MTU: 64:8
        UP RUNNING
        RX bytes:143 acl:0 sco:0 events:18 errors:0
        TX bytes:318 acl:0 sco:0 commands:15 errors:0

(at this point PCMCIA card is inserted)

simon9x@RED-DWARF:~$ hcitool dev
Devices:
        hci0    00:10:60:A8:A1:58
        hci2    00:10:60:AB:AB:08
simon9x@RED-DWARF:~$ hciconfig up
hci0:   Type: USB
        BD Address: 00:10:60:A8:A1:58 ACL MTU: 192:8 SCO MTU: 64:8
        UP RUNNING
        RX bytes:143 acl:0 sco:0 events:18 errors:0
        TX bytes:318 acl:0 sco:0 commands:15 errors:0

simon9x@RED-DWARF:~$ hciconfig hci2 up
Can't init device hci2: Permission denied (13)
simon9x@RED-DWARF:~$ sudo /etc/init.d/bluez-utils restart
 * Restarting Bluetooth services...                                      [ ok ]
simon9x@RED-DWARF:~$ hciconfig
hci0:   Type: USB
        BD Address: 00:10:60:A8:A1:58 ACL MTU: 192:8 SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN
        RX bytes:189 acl:0 sco:0 events:25 errors:0
        TX bytes:601 acl:0 sco:0 commands:22 errors:0

hci1:   Type: UART
        BD Address: 00:00:00:00:00:00 ACL MTU: 0:0 SCO MTU: 0:0
        DOWN
        RX bytes:0 acl:0 sco:0 events:0 errors:0
        TX bytes:8 acl:0 sco:0 commands:2 errors:0

hci2:   Type: UART
        BD Address: 00:10:60:AB:AB:08 ACL MTU: 192:8 SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN
        RX bytes:431 acl:0 sco:0 events:22 errors:0
        TX bytes:872 acl:0 sco:0 commands:23 errors:0

simon9x@RED-DWARF:~$

as you can see, bluetooth now detects and uses the card.

any suggestions on what to do to get the PCMCIA card recognized by bluetooth at boot or am i on the right track to get the missing file?

tia

ciao...dr. blues

---

