---
title: "Network Card and keyboard not detected Ubntu 22.04 dual boot"
date: 2022-09-08
forum: Hardware
---

### Post by brueb44 on 2022-09-08
Hey all,
Keyboard as well as network card arent detected when when trying out Ubuntu from a USB and also not after installing Ubuntu from said USB.
Ive browsed some stackoverflow pages to see how to diagnose the problem.
The firs thing I did was try:
```

sudo lshw -C network
  *-network UNCLAIMED       
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:81a00000-81afffff
  *-network
       description: Ethernet interface
       physical id: 1
       bus info: usb@10:1
       logical name: enxa0cec8fb3f95
       serial: a0:ce:c8:fb:3f:95
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ax88179_178a driverversion=5.15.0-46-generic duplex=full ip=192.168.178.132 link=yes multicast=yes port=MII speed=1Gbit/s

```
The UNCLAIMED keyword confuses me. What does that mean? That output doesnt tell me enough about the exact card type so I tried the command below:
It also seems that there is no driver for the network card, as that would show up in condifurtions: driver = xyz
```

sudo lspci -nn | grep Net -A2
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:b852]
03:00.0 SD Host controller [0805]: O2 Micro, Inc. SD/MMC Card Reader Controller [1217:8621] (rev 01)
04:00.0 Non-Volatile memory controller [0108]: Intel Corporation Device [8086:f1aa] (rev 03)

```
Im not really sure how that helps.

I also have an issue with my built in keyboard, which doesnt work. It does work however, in the GRUB menu. An external keyboard works as well.
```
xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ELAN2841:00 04F3:31AD Mouse                 id=15    [slave  pointer  (2)]
&#9116;   &#8627; ELAN2841:00 04F3:31AD Touchpad              id=16    [slave  pointer  (2)]
&#9116;   &#8627; USB USB Keyboard Consumer Control           id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Integrated Camera: Integrated C             id=12    [slave  keyboard (3)]
    &#8627; Integrated Camera: Integrated I             id=13    [slave  keyboard (3)]
    &#8627; Ideapad extra buttons                       id=14    [slave  keyboard (3)]
    &#8627; USB USB Keyboard                            id=9    [slave  keyboard (3)]
    &#8627; USB USB Keyboard System Control             id=10    [slave  keyboard (3)]
    &#8627; USB USB Keyboard Consumer Control           id=17    [slave  keyboard (3)]

```
Most of this output is gibberish to me, so would much appreciate any help.

Kind Regards

---

### Post by brueb44 on 2022-09-08
Quick update: after switching over to windows heres some mode details regarding the network card:
[FONT=Arial] Realtek RTL8852BE WiFi 6 802.11ax PCIe Adapter
[/FONT]The keyboard itsself is a standard PS/2 keyboard
The windows driver used is as follows:
Driver	C:\WINDOWS\SYSTEM32\DRIVERS\I8042PRT.SYS (10.0.22000.653, 152.00 KB (155,648 bytes), 9/7/2022 5:24 PM)

---

### Post by saby-gaby on 2022-10-27
I have exactly the same problems
network-card problem solution --> [https://github.com/HRex39/rtl8852be](https://github.com/HRex39/rtl8852be)
I still haven't found a solution to the keyboard issue

---

### Post by brueb44 on 2022-11-22
Have you figured out a solution to the keyboard issue?
I tried a different kernel module from a different repo, which didnt fix the problem sadly.

---

