---
title: "mg2522 wont print"
date: 2019-02-21
forum: Hardware
---

### Post by dhotrum on 2019-02-21
I bought an MG2522 printer. Mint recognizes the printer, I have paper loaded, The black ink light is on and the printer refuses to print. This is a brand new printer, right out of the box.

---

### Post by brian_p on 2019-02-21
Give the output of

```
lpinfo -v
```

---

### Post by dhotrum on 2019-02-22
dave@dave-HP:~$ lpinfo -v
file cups-brf:/
serial serial:/dev/ttyS0?baud=115200
network beh
file cups-pdf:/
direct parallel:/dev/lp0
direct hp
network lpd
network socket
network ipps
network ipp
network http
network https
network bjnp
direct hpfax
dave@dave-HP:~$ 

It is greek to me. I hope you understand

---

### Post by brian_p on 2019-02-22
> It is greek to me. I hope you understand 

Hello Dave,

The MG2522 is a USB printer which is supported by Gutenprint in Ubuntu, but the output you provide does not show any USB connection. There should be a line beginning "direct usb://". It is connected? It's switched on? The printer should also appear in the output of

```
lsusb
```

What does

```
lpstat -t
```

give?

---

### Post by dhotrum on 2019-02-22
dave@dave-HP:~$ lpstat -t
scheduler is running
system default destination: MG2500-series
device for MG2500-series: usb://Canon/MG2500%20series?serial=4D07E1&interface=1
MG2500-series accepting requests since Fri 22 Feb 2019 02:22:36 PM PST
printer MG2500-series is idle.  enabled since Fri 22 Feb 2019 02:22:36 PM PST
    Rendering completed
MG2500-series-120       dave              1024   Fri 22 Feb 2019 02:22:18 PM PST
dave@dave-HP:~$

---

### Post by dhotrum on 2019-02-22
dave@dave-HP:~$ lsusb
Bus 002 Device 006: ID 04a9:176d Canon, Inc. PIXMA MG2550
Bus 002 Device 002: ID 046d:0825 Logitech, Inc. Webcam C270
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 008 Device 002: ID 192f:0416 Avago Technologies, Pte. ADNS-5700 Optical Mouse Controller (3-button)
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
dave@dave-HP:~$

---

### Post by dhotrum on 2019-02-22
I followed the usb cable, yes plugged in both ends. Turned on. I will try another cable

---

### Post by dhotrum on 2019-02-22
Can I scream? I want to scream. It will make me feel so much better AAAAAAAAHHHHHHHH. It was the cable. that solved it. Brand new cable.
 Thank you for your help Brian

---

### Post by dhotrum on 2019-02-22
But why is the black ink light on? Obviously there is ink??

---

### Post by brian_p on 2019-02-22
You are printing now?

---

### Post by dhotrum on 2019-02-22
yes, thank you Brian

---

