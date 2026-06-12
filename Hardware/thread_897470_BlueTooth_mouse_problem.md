---
title: "BlueTooth mouse problem"
date: 2008-08-22
forum: Hardware
---

### Post by devill on 2008-08-22
I've been struggling with this for a week now, so I really desperately need help on this problem. :( I have **Sony VAIO VGN-AR550U laptop** and **Trust Bluetooth Optical Mini Mouse** and I just can't get them working together with **Ubuntu 8**.

Things I have tried: 

I have modified /etc/default/bluetooth : 
```
HIDD_ENABLED=1
```

I have used "hcitool scan", but it didn't find the mouse even though it is in connect mode.

I have tried to use the bluetooth-applet, and it did discovere the mouse, but when I tried to connect it returned an error: 

```
Couldn't display "obex://[00:0A:94:C2:73:4B]/"

Error: DBus error org.freedesktop.DBus.Error.NoReply:
Message did not recive a reply (timeout by message bus)
Please select another viewer and try again.
```

If I check the preferences in Bluetooth Manager, than the mouse is now bound to the laptop, but it won't show up in the list of input devices.

After that I figured, that 00:0A:94:C2:73:4B should be the MAC address for the mouse, so I tried:
```

devill@devillsvaio:~$ sudo hidd --connect 00:0A:94:C2:73:4B
Can't get device information: Host is down

```

Also the laptop did find my NOKIA phone, and it could connect. I even managed to copy files from the phones memory.

Thanks for your help in advance :-)

---

