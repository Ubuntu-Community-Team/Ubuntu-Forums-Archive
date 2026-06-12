---
title: "Bluetooth LE remote pairs, but no /dev/input created"
date: 2022-06-07
forum: Hardware
---

### Post by zang74 on 2022-06-07
Something happened between Impish and Jammy on my device, and my Xiaomi MiTV bluetooth remote control no longer works. After upgrading to 22.04, it just stopped creating a /dev/input, and has continued not working even switching to mainline kernel 5.17 (Jammy's 5.15.x doesn't work either) and the wishful thinking that every update on apt that shows up will fix it. 

Device in question:
[https://xiaomi-mi.ca/accessories-tv-box/xiaomi-mi-tv-mi-tv-box-bluetooth-remote-control/](https://xiaomi-mi.ca/accessories-tv-box/xiaomi-mi-tv-mi-tv-box-bluetooth-remote-control/)

I'm running Ubuntu Mate on an Odroid H2+ (j4115-based x86 SBC) as a media player. Bluetooth has been supplied via a BCM20702A-based IOGear BT4.0 adapter (driver installed), but I've also tried a (legit) CSR8510-based BT4.0 adapter with similar results.

It pairs fine if certain steps are followed—but it's been that way with this remove every ELEC I've had in the past that I've had in the past (PI ArmHF /Odroid ARM64). Note: It pairs and is usable on Windows, MacOS and iOS and pre-Jammy versions of Ubuntu. 

Addresses obfuscated to protect the innocent…

```

me@mybox:~$ bluetoothctl
[XiaoMi RC]# info
Device F4:XX:XX:XX:XX:XX (public)
    Name: XiaoMi RC
    Alias: XiaoMi RC
    Appearance: 0x03c0
    Paired: yes
    Trusted: yes
    Blocked: no
    Connected: yes
    WakeAllowed: yes
    LegacyPairing: no
    UUID: Generic Access Profile    (00001800-0000-1000-8000-00805f9b34fb)
    UUID: Generic Attribute Profile (00001801-0000-1000-8000-00805f9b34fb)
    UUID: Immediate Alert           (00001802-0000-1000-8000-00805f9b34fb)
    UUID: Link Loss                 (00001803-0000-1000-8000-00805f9b34fb)
    UUID: Tx Power                  (00001804-0000-1000-8000-00805f9b34fb)
    UUID: Device Information        (0000180a-0000-1000-8000-00805f9b34fb)
    UUID: Battery Service           (0000180f-0000-1000-8000-00805f9b34fb)
    UUID: Human Interface Device    (00001812-0000-1000-8000-00805f9b34fb)
    UUID: Scan Parameters           (00001813-0000-1000-8000-00805f9b34fb)
    Modalias: bluetooth:v2717p3200d0110
    Battery Percentage: 0x47 (71)
[XiaoMi RC]# show 5C:XX:XX:XX:XX:XX
Controller 5C:XX:XX:XX:XX:XX (public)
    Name: mybox
    Alias: mybox
    Class: 0x00000104
    Powered: yes
    Discoverable: no
    DiscoverableTimeout: 0x000000b4
    Pairable: yes
    UUID: Generic Attribute Profile (00001801-0000-1000-8000-00805f9b34fb)
    UUID: Generic Access Profile    (00001800-0000-1000-8000-00805f9b34fb)
    UUID: PnP Information           (00001200-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
    UUID: Device Information        (0000180a-0000-1000-8000-00805f9b34fb)
    Modalias: usb:v1D6Bp0246d0540
    Discovering: no
    Roles: central
    Roles: peripheral
Advertising Features:
    ActiveInstances: 0x00 (0)
    SupportedInstances: 0x05 (5)
    SupportedIncludes: tx-power
    SupportedIncludes: appearance
    SupportedIncludes: local-name
```
```
Bus 001 Device 005: ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0
```
```
busctl introspect 'org.bluez' '/org/bluez/hci0/dev_F4_XX_XX_XX_XX_XX'
NAME                                TYPE      SIGNATURE RESULT/VALUE                             FLAGS
org.bluez.Battery1                  interface -         -                                        -
.Percentage                         property  y         71                                       emits-change
org.bluez.Device1                   interface -         -                                        -
.CancelPairing                      method    -         -                                        -
.Connect                            method    -         -                                        -
.ConnectProfile                     method    s         -                                        -
.Disconnect                         method    -         -                                        -
.DisconnectProfile                  method    s         -                                        -
.Pair                               method    -         -                                        -
.Adapter                            property  o         "/org/bluez/hci0"                        emits-change
.Address                            property  s         "F4:XX:XX:XX:XX:XX"                      emits-change
.AddressType                        property  s         "public"                                 emits-change
.Alias                              property  s         "XiaoMi RC"                              emits-change writable
.Appearance                         property  q         960                                      emits-change
.Blocked                            property  b         false                                    emits-change writable
.Class                              property  u         -                                        emits-change
.Connected                          property  b         true                                     emits-change
.Icon                               property  s         -                                        emits-change
.LegacyPairing                      property  b         false                                    emits-change
.ManufacturerData                   property  a{qv}     -                                        emits-change
.Modalias                           property  s         "bluetooth:v2717p3200d0110"              emits-change
.Name                               property  s         "XiaoMi RC"                              emits-change
.Paired                             property  b         true                                     emits-change
.RSSI                               property  n         -                                        emits-change
.ServiceData                        property  a{sv}     -                                        emits-change
.ServicesResolved                   property  b         true                                     emits-change
.Trusted                            property  b         true                                     emits-change writable
.TxPower                            property  n         -                                        emits-change
.UUIDs                              property  as        9 "00001800-0000-1000-8000-00805f9b34fb… emits-change
.WakeAllowed                        property  b         true                                     emits-change writable
org.freedesktop.DBus.Introspectable interface -         -                                        -
.Introspect                         method    -         s                                        -
org.freedesktop.DBus.Properties     interface -         -                                        -
.Get                                method    ss        v                                        -
.GetAll                             method    s         a{sv}                                    -
.Set                                method    ssv       -                                        -
.PropertiesChanged                  signal    sa{sv}as  -
```
a few odd messages in syslog, but nothing that screams "major fail":
```
:~$ cat /var/log/syslog | grep "Blue"
Apr  5 22:50:24 mybox systemd[1]: Starting Bluetooth management mechanism...
Apr  5 22:50:24 mybox kernel: [    7.337177] Bluetooth: Core ver 2.22
Apr  5 22:50:24 mybox kernel: [    7.337217] Bluetooth: HCI device and connection manager initialized
Apr  5 22:50:24 mybox kernel: [    7.337222] Bluetooth: HCI socket layer initialized
Apr  5 22:50:24 mybox kernel: [    7.337227] Bluetooth: L2CAP socket layer initialized
Apr  5 22:50:24 mybox kernel: [    7.337234] Bluetooth: SCO socket layer initialized
Apr  5 22:50:24 mybox kernel: [    7.575381] Bluetooth: hci0: BCM: chip id 63
Apr  5 22:50:24 mybox kernel: [    7.576384] Bluetooth: hci0: BCM: features 0x07
Apr  5 22:50:24 mybox kernel: [    7.592401] Bluetooth: hci0: BCM20702A
Apr  5 22:50:24 mybox kernel: [    7.592411] Bluetooth: hci0: BCM20702A1 (001.002.014) build 0000
Apr  5 22:50:24 mybox kernel: [    7.594649] Bluetooth: hci0: BCM20702A1 'brcm/BCM20702A1-0a5c-21e8.hcd' Patch
Apr  5 22:50:24 mybox kernel: [    8.196379] Bluetooth: hci0: unexpected event 0xff length: 2 > 0
Apr  5 22:50:24 mybox systemd[1]: Started Bluetooth management mechanism.
Apr  5 22:50:24 mybox kernel: [    8.518390] Bluetooth: hci0: Broadcom Bluetooth Device
Apr  5 22:50:24 mybox kernel: [    8.518400] Bluetooth: hci0: BCM20702A1 (001.002.014) build 1764
Apr  5 22:50:24 mybox systemd[1]: Starting Bluetooth service...
Apr  5 22:50:24 mybox bluetoothd[970]: Bluetooth daemon 5.64
Apr  5 22:50:24 mybox systemd[1]: Started Bluetooth service.
Apr  5 22:50:24 mybox NetworkManager[699]: <info>  [1649213424.6320] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.36.4/libnm-device-plugin-bluetooth.so)
Apr  5 22:50:24 mybox systemd[1]: Reached target Bluetooth Support.
Apr  5 22:50:24 mybox kernel: [    8.948829] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr  5 22:50:24 mybox kernel: [    8.948837] Bluetooth: BNEP filters: protocol multicast
Apr  5 22:50:24 mybox kernel: [    8.948843] Bluetooth: BNEP socket layer initialized
Apr  5 22:50:24 mybox bluetoothd[970]: Bluetooth management interface 1.21 initialized
Apr  5 22:50:36 mybox kernel: [   20.341197] Bluetooth: RFCOMM TTY layer initialized
Apr  5 22:50:36 mybox kernel: [   20.341222] Bluetooth: RFCOMM socket layer initialized
Apr  5 22:50:36 mybox kernel: [   20.341233] Bluetooth: RFCOMM ver 1.11
Apr  5 22:56:28 mybox systemd[1777]: Reached target Bluetooth.
Apr  5 23:17:03 mybox systemd[1777]: Starting Bluetooth Manager...
Apr  5 23:17:03 mybox systemd[1777]: Started Bluetooth Manager.
Apr  5 23:17:25 mybox kernel: [ 1630.329450] Bluetooth: hci0: unexpected SMP command 0x0b from f4:xx:xx:xx:xx:xx
Apr  5 23:17:52 mybox blueman-manager[115657]: blueman.bluez.errors.BluezDBusException: org.freedesktop.DBus.Error.InvalidArgs No such interface 'org.bluez.Battery1'
Apr  6 06:21:33 mybox NetworkManager[660748]: <info>  [1649240493.3391] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.36.4/libnm-device-plugin-bluetooth.so)
```
The remote pairs and connects. I can obviously see it bluetoothctl. But no event is created in /dev/input:
```
me@mybox:~$ sudo evtest
No device specified, trying to scan all of /dev/input/event*
Available devices:
/dev/input/event0:    Power Button
/dev/input/event1:    Power Button
/dev/input/event2:    Video Bus
/dev/input/event3:    Logitech K400 Plus
/dev/input/event4:    Microsoft X-Box 360 pad
/dev/input/event5:    Microsoft X-Box 360 pad
/dev/input/event6:    Microsoft X-Box 360 pad
/dev/input/event7:    Pulse-Eight CEC Adapter
/dev/input/event8:    Microsoft X-Box 360 pad
/dev/input/event9:    HDA Intel PCH Mic
/dev/input/event10:    HDA Intel PCH Headphone
/dev/input/event11:    HDA Intel PCH HDMI/DP,pcm=3
/dev/input/event12:    HDA Intel PCH HDMI/DP,pcm=7
/dev/input/event13:    HDA Intel PCH HDMI/DP,pcm=8
/dev/input/event14:    HDA Intel PCH HDMI/DP,pcm=9
/dev/input/event15:    HDA Intel PCH HDMI/DP,pcm=10
Select the device event number [0-15]:
```
showkey and xev gets no keypresses, but btmon is seeing them:
```
me@mybox:~$ sudo btmon
Bluetooth monitor ver 5.64
= Note: Linux version 5.17.1-051701-generic (x86_64)                                                           0.026997
= Note: Bluetooth subsystem version 2.22                                                                       0.027002
= New Index: 5C:XX:XX:XX:XX:XX (Primary,USB,hci0)                                                       [hci0] 0.027004
= Open Index: 5C:XX:XX:XX:XX:XX                                                                        [hci0] 0.027004
= Index Info: 5C:XX:XX:XX:XX:XX (Broadcom Corporation)                                                  [hci0] 0.027005
@ MGMT Open: bluetoothd (privileged) version 1.21                                                     {0x0001} 0.027006
> ACL Data RX: Handle 64 flags 0x02 dlen 15                                                          #1 [hci0] 1.698718
      ATT: Handle Value Notification (0x1b) len 10
        Handle: 0x0032
          Data: 0000510000000000
> ACL Data RX: Handle 64 flags 0x02 dlen 15                                                          #2 [hci0] 1.774350
      ATT: Handle Value Notification (0x1b) len 10
        Handle: 0x0032
          Data: 0000000000000000
> ACL Data RX: Handle 64 flags 0x02 dlen 15                                                          #3 [hci0] 2.594360
      ATT: Handle Value Notification (0x1b) len 10
        Handle: 0x0032
          Data: 0000520000000000
> ACL Data RX: Handle 64 flags 0x02 dlen 15                                                          #4 [hci0] 2.754407
      ATT: Handle Value Notification (0x1b) len 10
        Handle: 0x0032
          Data: 0000000000000000
> ACL Data RX: Handle 64 flags 0x02 dlen 15                                                          #5 [hci0] 3.414342
      ATT: Handle Value Notification (0x1b) len 10
        Handle: 0x0032
          Data: 0000500000000000
> ACL Data RX: Handle 64 flags 0x02 dlen 15                                                          #6 [hci0] 3.574341
      ATT: Handle Value Notification (0x1b) len 10
        Handle: 0x0032
          Data: 0000000000000000
> ACL Data RX: Handle 64 flags 0x02 dlen 15                                                          #7 [hci0] 4.014365
      ATT: Handle Value Notification (0x1b) len 10
        Handle: 0x0032
          Data: 00004f0000000000
> ACL Data RX: Handle 64 flags 0x02 dlen 15                                                          #8 [hci0] 4.174358
      ATT: Handle Value Notification (0x1b) len 10
        Handle: 0x0032
          Data: 0000000000000000
> ACL Data RX: Handle 64 flags 0x02 dlen 15                                                          #9 [hci0] 4.674365
      ATT: Handle Value Notification (0x1b) len 10
        Handle: 0x0032
          Data: 0000660000000000
> ACL Data RX: Handle 64 flags 0x02 dlen 15                                                         #10 [hci0] 4.934380
      ATT: Handle Value Notification (0x1b) len 10
        Handle: 0x0032
          Data: 0000000000000000
> ACL Data RX: Handle 64 flags 0x02 dlen 15                                                         #11 [hci0] 5.794429
      ATT: Handle Value Notification (0x1b) len 10
        Handle: 0x0032
          Data: 0000800000000000
> ACL Data RX: Handle 64 flags 0x02 dlen 15                                                         #12 [hci0] 6.034380
      ATT: Handle Value Notification (0x1b) len 10
        Handle: 0x0032
          Data: 0000000000000000
> ACL Data RX: Handle 64 flags 0x02 dlen 15                                                         #13 [hci0] 7.194396
      ATT: Handle Value Notification (0x1b) len 10
        Handle: 0x0032
          Data: 0000810000000000
> ACL Data RX: Handle 64 flags 0x02 dlen 15                                                         #14 [hci0] 7.354432
      ATT: Handle Value Notification (0x1b) len 10
        Handle: 0x0032
          Data: 0000000000000000
> ACL Data RX: Handle 64 flags 0x02 dlen 15                                                         #15 [hci0] 8.454406
      ATT: Handle Value Notification (0x1b) len 10
        Handle: 0x0032
          Data: 00004a0000000000
> ACL Data RX: Handle 64 flags 0x02 dlen 15                                                         #16 [hci0] 8.694405
      ATT: Handle Value Notification (0x1b) len 10
        Handle: 0x0032
          Data: 0000000000000000
> ACL Data RX: Handle 64 flags 0x02 dlen 15                                                        #17 [hci0] 10.414431
      ATT: Handle Value Notification (0x1b) len 10
        Handle: 0x0032
          Data: 0000650000000000
> ACL Data RX: Handle 64 flags 0x02 dlen 15                                                        #18 [hci0] 10.654417
      ATT: Handle Value Notification (0x1b) len 10
        Handle: 0x0032
          Data: 0000000000000000
> ACL Data RX: Handle 64 flags 0x02 dlen 15                                                        #19 [hci0] 11.134410
      ATT: Handle Value Notification (0x1b) len 10
        Handle: 0x0032
          Data: 0000f10000000000
> ACL Data RX: Handle 64 flags 0x02 dlen 15                                                        #20 [hci0] 11.294427
      ATT: Handle Value Notification (0x1b) len 10
        Handle: 0x0032
          Data: 0000000000000000
> ACL Data RX: Handle 64 flags 0x02 dlen 15                                                        #21 [hci0] 12.094482
      ATT: Handle Value Notification (0x1b) len 10
        Handle: 0x0032
          Data: 0000280000000000
> ACL Data RX: Handle 64 flags 0x02 dlen 15                                                        #22 [hci0] 12.234598
      ATT: Handle Value Notification (0x1b) len 10
        Handle: 0x0032
          Data: 0000000000000000
```

This is driving me **nuts**. Especially because another similar model of the same remote that uses AAA batteries instead of a coin-cell battery works (that one disconnects regularly, and is slow to reconnect however, but pairs fine, creates an input event and all keypresses are recognized).

---

