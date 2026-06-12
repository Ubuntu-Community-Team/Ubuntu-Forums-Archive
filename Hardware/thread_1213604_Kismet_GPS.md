---
title: "Kismet GPS"
date: 2009-07-15
forum: Hardware
---

### Post by shang1 on 2009-07-15
Hey all,
I am currently attempting to connect my bluetooth GPS device to my linux machine and use gpsd with it.

I can connect to my device using:
```
rfcomm connect /dev/rfcomm1 00:13:6C:F1:FB:84 1
```

Which works because and is on the correct channel because my GPS shows my computers MAC address as connected and cat /dev/rfcomm1 shows a bunch of random, scrolling (hopefully/presumably NMEA) data.

Now when I try to execute gpsd using,
```
sudo gpsd -N -D 4 /dev/rfcomm1 &
```

I get the following output, followed by a stall:
```
gpsd: launching (Version 2.38)
gpsd: listening on port gpsd
gpsd: Priority sertting failed.
gpsd: shmat(983059,0,0) succeeded
gpsd: shmat(1015828,0,0) succeeded
gpsd: shmat(1048597,0,0) succeeded
gpsd: shmat(1081366,0,0) succeeded
gpsd: successfully connected to the DBUS system bus
gpsd: running with effective group ID 0
gpsd: running with effective user ID 0
gpsd: opening GPS data source at '/dev/rfcomm1'
gpsd: speed 9600, 8N1

```

Can anyone please, please assist me with this issue?
Thanks.

---

