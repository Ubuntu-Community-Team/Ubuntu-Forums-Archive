---
title: "USB 3.0 hub"
date: 2019-07-30
forum: Hardware
---

### Post by chris230291 on 2019-07-30
Hello. I just picked up a USB 3.0 hub for my server. It appears to be detected but none of the devices plugged into it are.

```
chris@Server:~$ lspci | grep -i usb00:1a.0 USB controller: Intel Corporation C600/X79 series chipset USB2 Enhanced Host Controller #2 (rev 06)
00:1d.0 USB controller: Intel Corporation C600/X79 series chipset USB2 Enhanced Host Controller #1 (rev 06)
03:00.0 USB controller: VIA Technologies, Inc. VL805 USB 3.0 Host Controller (rev 01)
```

```
chris@Server:~$ lsusbBus 002 Device 005: ID 045e:02d5 Microsoft Corp. Xbox One Digital TV Tuner
Bus 002 Device 004: ID 413c:2001 Dell Computer Corp. Keyboard HID Support
Bus 002 Device 003: ID 413c:1001 Dell Computer Corp. Keyboard Hub
Bus 002 Device 006: ID 1b1c:1b05 Corsair
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0557:2221 ATEN International Co., Ltd Winbond Hermon
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I bought the card specifically for my xbox tuners. There should be 4 listed but it only shows the one thats plugged into a mobo USB port.
I tried a mouse and a keyboard on the card but neither worked.
You can see a USB 3.0 hub is detected.

Not really sure what to try.
Any help is appreciated.
Chris

---

### Post by MartyBuntu on 2019-07-31
Is the hub powered?

---

### Post by Autodave on 2019-07-31
Have you tried it another port?  Another machine?  Maybe even try a USB 2.0 port.  You may have gotten a defective hub.

---

