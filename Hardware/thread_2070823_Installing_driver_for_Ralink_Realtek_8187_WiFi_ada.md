---
title: "Installing driver for Ralink Realtek 8187 WiFi adapter"
date: 2012-10-13
forum: Hardware
---

### Post by simon174 on 2012-10-13
I purchased a WiFi adapter online, and it came with an  installation CD with drivers. I installed it just fine on Windows, and  am now trying on Ubuntu 10.10. The CD came with the driver files for  Linux as well, but I have no idea why they aren't working - my guess is  that I don't properly understand what to do with them.

  I have uploaded the contents of the folder which came with the CD [here]("http://speedy.sh/7XqkP/Realtek8187L-Linux.zip"). There is a README in there, but the instructions under the installation header didn't get me anywhere unfortunately.

  The Device ID is:

  Bus 001 Device 002: ID 148f:5370 Ralink Technology, Corp.

Thanks.

---

### Post by ahallubuntu on 2012-10-13
Ralink and Realtek are different companies (like Ford and GM).

Your device ID says it is a Ralink RT5370 chipset.  This driver may work:

[https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M](https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M)

Note that you may get limited support at this point now that Ubuntu 10.10 is no longer officially supported.

---

### Post by simon174 on 2012-10-13
Cool, thanks for the reply. That encouraged me to try 12.04.1, and all is good now. Isn't it so nice when things work out in the end? :popcorn:

---

### Post by kurt18947 on 2012-10-13
> **simon174 said:**
> Cool, thanks for the reply. That encouraged me to try 12.04.1, and all is good now. Isn't it so nice when things work out in the end? :popcorn:

A very good reason to use a recent or current distro. I found my wifi adapters required work with 10.XX.  They worked OOB with 11.04.

---

