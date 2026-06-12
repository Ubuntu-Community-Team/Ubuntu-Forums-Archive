---
title: "Integrated webcam is not detected! Dell XPS 13_Ubuntu 23.04"
date: 2023-09-15
forum: Hardware
---

### Post by oaavahid on 2023-09-15
Dear friends,

I recently returned to Ubuntu after 15 years !!! It's quite nice and I have been enjoying it in the past month.

I could manage to make everything work **except the integrated webcam**, despite searching a lot, still I could not find a solution. Please see a summary below:

Model: **Dell XPS 13 2-in-1 7390**
OS: **Ubuntu 23.04**
The output of ***lsusb***:
```
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 007: ID 0bda:1100 Realtek Semiconductor Corp. HID Device
Bus 003 Device 006: ID 0bda:5409 Realtek Semiconductor Corp. USB2.1 Hub
Bus 003 Device 005: ID 0bda:5409 Realtek Semiconductor Corp. USB2.1 Hub
Bus 003 Device 002: ID 27c6:532d Shenzhen Goodix Technology Co.,Ltd. Fingerprint
Bus 003 Device 004: ID 8087:0026 Intel Corp. AX201 Bluetooth
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 0bda:8153 Realtek Semiconductor Corp. RTL8153 Gigabit Ethernet Adapter
Bus 002 Device 003: ID 0bda:0409 Realtek Semiconductor Corp. USB3.2 Hub
Bus 002 Device 002: ID 0b00:0409 INGENICO USB3.2 Hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

As far as I see, no integrated webcam. I once connected an external webcam and Ubuntu could detect it. I would appreciate it if you could help me to solve this issue. 

Many thanks,
Vahid

---

### Post by #&amp;thj^% on 2023-09-15
It might show from inxi ie:
```
inxi -G | grep Camera
  Device-3: Generic Integrated Camera driver: uvcvideo type: USB

```
EDIT: After a little research I found this: [https://www.dell.com/community/en/conversations/linux-general/dell-xps-13-7390-camera-not-detected-on-ubuntu-1910/647f8776f4ccf8a8de6ae405](https://www.dell.com/community/en/conversations/linux-general/dell-xps-13-7390-camera-not-detected-on-ubuntu-1910/647f8776f4ccf8a8de6ae405)
Bad news>>>Not Supported

---

### Post by oaavahid on 2023-09-22
Thanks. Do you know whether my laptop's webcam is supported on other distributions, like Fedora or others? How can I check this?

---

### Post by #&amp;thj^% on 2023-09-22
> **oaavahid said:**
> Thanks. Do you know whether my laptop's webcam is supported on other distributions, like Fedora or others? How can I check this?

Have a look here: [https://askubuntu.com/questions/1428961/dell-xps-13-webcam-not-recognized-under-ubuntu-22-04-1](https://askubuntu.com/questions/1428961/dell-xps-13-webcam-not-recognized-under-ubuntu-22-04-1)
Possible solution.
If you go that route with the PPA you will need to edit it to show "jammy" and not "lunar" they support LTS release's only.

---

