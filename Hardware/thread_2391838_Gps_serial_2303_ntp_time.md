---
title: "Gps serial 2303 ntp time"
date: 2018-05-13
forum: Hardware
---

### Post by kc7noa2 on 2018-05-13
ok, i have searched and cant quite get my desired outcome ...

i have an Ambicom gps-usb that i do get some data out of ...but the NEMA strings look dirty or something 

$GPRMC,235254.537,V,,,,,,,130518,,,N*45

$GPGGA,235255.537,,,,,0,00,,,M,0.0,M,,0000*51

$GPGSA,A,1,,,,,,,,,,,,,,,*1E

$GPRMC,235255.537,V,,,,,,,130518,,,N*44

$GPGGA,235256.537,,,,,0,00,,,M,0.0,M,,0000*52

$GPGSA,A,1,,,,,,,,,,,,,,,*1E

$GPRMC,235256.537,V,,,,,,,130518,,,N*47

$GPGGA,235257.537,,,,,0,00,,,M,0.0,M,,0000*53

$GPGSA,A,1,,,,,,,,,,,,,,,*1E

$GPRMC,235257.537,V,,,,,,,130518,,,N*46


i would also like to set system time from non-PPS source ..... even WWVH would be great

my system is quad core arm 64 with Ubuntu 16.04 and

XXXXxXXX@odroid64:~$ uname -r
3.14.79-117

---

