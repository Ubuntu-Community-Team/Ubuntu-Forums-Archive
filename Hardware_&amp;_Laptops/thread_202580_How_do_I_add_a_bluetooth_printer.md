---
title: "How do I add a bluetooth printer?"
date: 2006-06-23
forum: Hardware &amp; Laptops
---

### Post by MikkelMJ on 2006-06-23
Hi, I've got a HP Deskjet 460 wbt printer. I've installed it in Ubuntu by using the System -> Administration -> Printing -> Add Printer GUI. It worked fine, but the special thing about the 460 wbt is that it has support for bluetooth printing. This works with Windows, but I can't seem to make it work on Ubuntu. It's like there's no option for it anywhere. Ubuntu finds the printer and tells me that it has support for serial port printing, but cannot print through it. I've followed this guide, but it didn't work:

```
sudo apt-get install bluez-cups bluez-pcmcia-support bluez-pin bluez-utils libbluetooth1
```

Check that the Bluetooth device is detected via
```
hciconfig
```

The output should look like:

```
hci0:   Type: USB
        BD Address: 00:20:E0:85:7F:65 ACL MTU: 192:8  SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN AUTH ENCRYPT
        RX bytes:1201 acl:29 sco:0 events:48 errors:0
        TX bytes:746 acl:22 sco:0 commands:18 errors:0
```

To find out which Bluetooth devices are in range you can use the command
```
hcitool scan
```

To find out which services these devices provide (and on which channel they provide them) use the command
```
sudo sdptool browse
```

Edit the file /etc/bluetooth/printers.conf and add an entry similar to the following:

```
default {
     # Bluetooth address of the device
     device 00:40:8C:5E:5D:A4;

     # Bluetooth printing protocol
     protocol serial;

     # Description of the connection
     comment "My Bluetooth printer";
}
```

Restart your CUPS system, and you should then see the printer ready for
administration. The Bluetooth backend performs an SDP inquiry on the tar-
get printer to discover the RFCOMM channel on which to send data.

How do I do to make it work?

Thanks

---

### Post by MikkelMJ on 2006-06-24
Hmm, somebody in the world must have tried to do this before me... If it's not possible then, please someone, just tell me that it's not possible so I can stop wasting my time to find a solution.

---

