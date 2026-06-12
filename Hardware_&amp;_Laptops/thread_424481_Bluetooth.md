---
title: "Bluetooth"
date: 2007-04-26
forum: Hardware &amp; Laptops
---

### Post by r-mo on 2007-04-26
Bought a bluetooth dongle today to transfer pictures from my phone and see if I could get a Wii remote working.  Think it's kind of working, when I run hcitool scan I see my devices:
```
        00:16:DB:2F:8B:2B       SGH-S500i
        00:19:1D:69:5A:4A       Nintendo RVL-CNT-01

```
but, I had a look in the syslog and the message

```
ATH64 kernel: [  301.020000] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
```

is coming up over 200 times a second from when I connect the dongle to when I disconnect it.  This can't be good :confused:

---

### Post by Spleenie on 2007-06-18
I am getting the same error message over and over again in both my syslog and in the Fx terminal windows.

```
hc1_scodata_packet: hci SCO packet for unknown connection handle 92
```

made a 3Gb syslog file in a around 24 hours.

removed the dongle, and it stopped. Turned off bluetooth using /etc/init.d/bluetooth stop, inserted dongle, no messages, restart bluetooth and it happens again, and stopped when the dongle is removed.

Using Ubuntu Feisty 2.6.20-16-generic

Cheers, S.

---

### Post by sarutv on 2007-08-04
I face the same problem. I bought a USB Bluetooth dongle so that I can sync the calendar from my Google Calendar -> Evolution -> Phone. As soon as I inserted the dongle the messages you mentioned appears several times in syslog.

The dongle seems to be working as I can do "hcitool scan" and it lists my Nokia N70 phone. A bug report has already been filed -> [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/39414](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/39414). So watch it for further developments.

---

