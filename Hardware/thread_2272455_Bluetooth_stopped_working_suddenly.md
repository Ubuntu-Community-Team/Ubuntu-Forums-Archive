---
title: "Bluetooth stopped working suddenly"
date: 2015-04-06
forum: Hardware
---

### Post by prodicus on 2015-04-06
I am not able to see `bluetooth` symbol on the `panel`. 
I checked with `Unity Tweak Tool` and there is a tick mark for bluetooth.

Further, I ran the command ```
sudo service bluetooth status
``` and it gave ```
bluetooth start/running, process 744
```
```

    tasdik@Acer:~/Dropbox/code$ rfkill list
    0: acer-wireless: Wireless LAN
            Soft blocked: no
            Hard blocked: no
    1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
```

And 

    ```
tasdik@Acer:~/Dropbox/code$ sudo bluetoothd -d -n
    bluetoothd[18809]: Bluetooth daemon 4.101
    bluetoothd[18809]: src/main.c:p****_config() parsing main.conf
    bluetoothd[18809]: src/main.c:p****_config() discovto=0
    bluetoothd[18809]: src/main.c:p****_config() pairto=0
    bluetoothd[18809]: src/main.c:p****_config() pageto=8192
    bluetoothd[18809]: src/main.c:p****_config() auto_to=60
    bluetoothd[18809]: src/main.c:p****_config() name=%h-%d
    bluetoothd[18809]: src/main.c:p****_config() class=0x000100
    bluetoothd[18809]: src/main.c:p****_config() Key file does not have key 'DeviceID'
    D-Bus setup failed: Name already in use
    bluetoothd[18809]: Unable to get on D-Bus
```


Because of it I am not able to transfer files between my PC and mobile devices. 

Any ideas guys?

[SIZE=2]**Edit : Tried some more things, gave me these**[/SIZE]

    ```

    tasdik@Acer:~$ lsusb
    Bus 002 Device 003: ID 413c:2107 Dell Computer Corp. 
    Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
    Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 001 Device 004: ID 1bcf:2c00 Sunplus Innovation Technology Inc. 
    Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    
```

And
```

    tasdik@Acer:~$ lsmod | grep bluetooth
    bluetooth             446190  10 bnep,rfcomm
    6lowpan_iphc           18702  1 bluetooth

```

And 

```

    tasdik@Acer:~$ dmesg | grep -i bluetooth
    [    1.779150] usb 1-1.4: Product: Bluetooth USB Host Controller
    [   22.545624] Bluetooth: Core ver 2.19
    [   22.545650] Bluetooth: HCI device and connection manager initialized
    [   22.545661] Bluetooth: HCI socket layer initialized
    [   22.545666] Bluetooth: L2CAP socket layer initialized
    [   22.545682] Bluetooth: SCO socket layer initialized
    [   22.553720] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
    [   22.553725] Bluetooth: BNEP filters: protocol multicast
    [   22.553734] Bluetooth: BNEP socket layer initialized
    [   22.594494] Bluetooth: RFCOMM TTY layer initialized
    [   22.594510] Bluetooth: RFCOMM socket layer initialized
    [   22.594517] Bluetooth: RFCOMM ver 1.11

```

And 
```

    tasdik@Acer:~$ dmesg | grep -i firmware
    [    0.164868] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query honored via cmdline
    [    1.907636] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x461f00)

```

And 

```

    tasdik@Acer:~$ rfkill list all
    0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
    1: acer-wireless: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```

---

