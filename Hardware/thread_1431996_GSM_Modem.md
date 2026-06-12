---
title: "GSM Modem"
date: 2010-03-17
forum: Hardware
---

### Post by hselvaggi on 2010-03-17
Hi,

I have problem working with some GSM Modems. I connected the GSM Modem to the USB port and a new device appeared /dev/ttyACM0, after a while that device stop working and another one is created named /dev/ttyACM1 and so on. That way the software stop working as soon as the new device is created.

Can anybody help me with that please?

Regards:
Harold.

---

### Post by Fafler on 2010-03-17
I use a Nokia N79 as modem and sometimes it does the same thing. I've just set the NetworkManager Applet to autoconnect to the phone. At this point i think it uses ttyACM53, but it doesn't matter, except for the downtime each time it happens.

---

### Post by hselvaggi on 2010-03-17
Hi,

Thanks. The problem with it is I'm using the GSM modem not for network, I'm doing it just to work with SMS messages and in production it will be running in a ubuntu server.

Regards:
Harold.

---

### Post by Fafler on 2010-03-19
Maybe you (or someone else) can fix it with udev?

---

### Post by dyslexia on 2010-03-19
It changes dynamicly, not durring boot, sometimes a lock gets put on ACM0 so it makes another device.

I use this script, connected to a launcher on gnome-panel:

```
$ cat /usr/local/bin/oneline
#!/bin/sh

pppd /dev/ttyACM$((`ls /dev/ttyACM* | wc -l` - 1)) 460800 nodetach defaultroute noipdefault lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','<APN>'" OK "atdt*99#" CONNECT' user web password web

```

Now, how to do this in Windows?

---

### Post by hselvaggi on 2010-03-23
Hi,

Thanks very much. udev did the work. I configure udev so the device is always loading in the same device file and give it permissions for all the users in the .rules file.

In the first place it was a permission problem, everytime a user try to read or write that device the device got disconnected and reconnected in another port. After setting up udev with the rigth permissions it works great. The device still disconnect and reconnect but about once in a day and the device is reloaded by udev so the application keep working.

Regards:
Harold.

---

