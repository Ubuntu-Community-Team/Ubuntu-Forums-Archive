---
title: "Trying to get the Realtek rtl8812au wireless adapter to work in Ubuntu 22.04"
date: 2022-02-25
forum: Hardware
---

### Post by Joe_Linux on 2022-02-25
I am trying to get the Realtek rtl8812au wireless adapter to work in Ubuntu 22.04, I tried following this post.
```
https://tutorialforlinux.com/2022/01/11/realtek-rtl8812au-driver-ubuntu-22-04-installation-step-by-step/
```
This is my result 
```
ubuntu@ubuntu:~/Desktop$ sudo apt-get update
Ign:1 cdrom://Ubuntu 22.04 LTS _Jammy Jellyfish_ - Alpha amd64 (20220202) jammy InRelease
Hit:2 cdrom://Ubuntu 22.04 LTS _Jammy Jellyfish_ - Alpha amd64 (20220202) jammy Release
Hit:4 http://archive.ubuntu.com/ubuntu jammy InRelease                         
Hit:5 http://security.ubuntu.com/ubuntu jammy-security InRelease               
Hit:6 http://archive.ubuntu.com/ubuntu jammy-updates InRelease
Reading package lists... Done
ubuntu@ubuntu:~/Desktop$ sudo apt remove rtl8812au-dkms
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package rtl8812au-dkms
```

Also FYI the dongle does show up in the lsusb command 
```
ubuntu@ubuntu:~/Desktop$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 011: ID 0bda:0811 Realtek Semiconductor Corp. Realtek 8812AU/8821AU 802.11ac WLAN Adapter [USB Wireless Dual-Band Adapter 2.4/5Ghz]
Bus 001 Device 007: ID 1f75:0917 Innostor Technology Corporation IS917 Mass storage
Bus 001 Device 006: ID 07b8:3071 AboCom Systems Inc 802.11n/b/g Mini Wireless LAN USB2.0 Adapter
Bus 001 Device 004: ID 05e3:0610 Genesys Logic, Inc. Hub
Bus 001 Device 002: ID 05e3:0610 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0e8f:0022 GreenAsia Inc. multimedia keyboard controller
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ubuntu@ubuntu:~/Desktop$ 





```

BTW the dongle works in Ubuntu 18.04 
I realize that 22.04 is not ready yet.
Thank you in advance

---

### Post by coffeecat on 2022-02-25
Duplicate of [https://ubuntuforums.org/showthread.php?t=2472362](https://ubuntuforums.org/showthread.php?t=2472362)

Closed.

---

