---
title: "Linksys WUSB660N not working on Ubuntu 10.10 64 bit"
date: 2010-11-05
forum: Hardware
---

### Post by ltpg97 on 2010-11-05
Hello,

I'm having issues connecting to my wireless network. I have a Linksys WUSB600N V.1 connected to Ubuntu 10.10 64 bit. The issue is it see the network but when I try to connect after entering the wireless key it just continues to search for an IP address and never establishes a connection. I'd like to point out that it works just fine on my Windows 7 64 bit. If anyone has any solutions please feel free to share. Thanks.

---

### Post by ltpg97 on 2010-11-05
Problem solved. 

1. Log in as root user

2. Open a terminal and type: 

sudo gedit /etc/modprobe.d/blacklist.conf 

At the end of the file, add three lines
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib 

Proofread carefully, save and close gedit. Reboot.

---

