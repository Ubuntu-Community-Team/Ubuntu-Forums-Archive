---
title: "Proximity Sensing with Bluetooth Low Energy Device"
date: 2014-02-10
forum: Hardware
---

### Post by victorbrca2 on 2014-02-10
I bought one of the new Casio G-Shock with Bluetooth ([GB-X6900]("http://www.gshock.com/watches/Classic/GBX6900B-1")) in the hope that I would be able to use it with BlueProximity to auto lock/unlock, however I'm not able to detect/pair it with my computer. 

So I thought maybe I could write a script that will do the same... I can find the device using lescan, but for some reason I'm not able to connect to it. Any ideas? 

```
# hcitool lescan
LE Scan ...
CC:EE:18:57:D5:6A CASIO GB-X6900B

# gatttool -b CC:EE:18:57:D5:6A -m 48 --interactive
[   ][CC:EE:18:57:D5:6A][LE]> connect
Connecting... connect error: Device or resource busy (16)

# hcitool lecc CC:EE:18:57:D5:6A
Could not create connection: Input/output error

# hcitool cc CC:EE:18:57:D5:6A
Can't create connection: Input/output error
```

---

### Post by victorbrca2 on 2014-02-10
If anyone ever have this issue, try using "--random" with gatttool.

```
gatttool -b CC:EE:18:57:D5:6A -t random --interactive
```

And if that doesn't work, try stopping or removing the device, then try again:

```
# hciconfig hci0 down
# hciconfig hci0 up
# gatttool -b CC:EE:18:57:D5:6A -t random --interactive
[   ][CC:EE:18:57:D5:6A][LE]> connect
[CON][CC:EE:18:57:D5:6A][LE]>
```

However I'm still not able to figure out how to find the device distance. "rfcomm connect" always fails, so I can't use 'rssi'. Also, once the device is paired I can't even see it with 'lescan'. 

Any help is appreciated.

---

