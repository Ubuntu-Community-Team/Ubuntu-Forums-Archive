---
title: "wireless xsupplicant problem"
date: 2006-03-21
forum: Hardware &amp; Laptops
---

### Post by nishoba on 2006-03-21
hi

i have problems connecting to ap-s on my schools wireless network

i have canyon cn-wf513 pcmcia wireless card with rt2500 chipset
the wireless card is recognized by ubuntu and works fine
(i'm very new to linux so my friend told me how to connect to ap)
so i installed xsupplicant version 1.2.1 from ubuntu reprositories

i connect to the network with:
```
$sudo iwconfig ra0 essid essidname
$sudo iwconfig ra0 key open
$sudo ifconfig ra0 up
$sudo xsupplicant -i ra0
$sudo dhclient ra0
```

where the config file of xsupplicant is:
```
default_netname = essidname
logfile = /var/log/xsupplicant.log
FERwlan {
        type=wireless
        wireless_control=yes
        identity=<BEGIN_ID>myusername<END_ID>
        eap-peap {
                root_cert=NONE
                chunk_size=1398
                random_file=/dev/urandom
                cnexact=yes
                allow_types=eap_mschapv2
                eap-mschapv2 {
                        username=<BEGIN_UNAME>myusername<END_UNAME>
                        password=<BEGIN_PASS>mypass<END_PASS>
                }
        }
}
```

my friend has the same config file and it works normaly(but he has centrino and fedora core4)

well my problem is i am authenticated, i get with dhclient ip adress and i can normaly surf web pages for about 3-4 minutes and then nothing???
the network monitors displays that my wireless card and ap are sending each other packages but i cannot surf web or anything similar

what to do?
thx

---

### Post by nishoba on 2006-03-22
sry for offtopic, plz mod move this topic to networking

on the topic. doesn't anyone have a idea how to fix the problem???

---

