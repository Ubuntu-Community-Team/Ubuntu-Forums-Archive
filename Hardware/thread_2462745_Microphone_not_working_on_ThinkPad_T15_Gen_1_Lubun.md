---
title: "Microphone not working on ThinkPad T15 Gen 1 Lubuntu 18.04 LTS"
date: 2021-05-27
forum: Hardware
---

### Post by bug5 on 2021-05-27
Hello,

the Microphone is not detected on Lubuntu 18.04, pulseaudio only showing **Microphone (unplugged)**, no other device.

System:
OS: Ubuntu 18.04.5 LTS x86_64
Host: 20S7S5G600 ThinkPad T15 Gen 1
Kernel: 5.4.0-72-generic
CPU: Intel i5-10310U (8) @ 4.400GHz
GPU: Intel Device 9b41
Memory: 383MiB / 15640MiB

What could be wrong here?, maybe a missing driver?


Thanks in advance!

---

### Post by guiverc on 2021-05-27
Are you aware that flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors), so you're asking about a release that is now EOL.

- [https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/](https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/)
- [https://lubuntu.me/bionic-5-released/](https://lubuntu.me/bionic-5-released/)
- [https://lubuntu.me/bionic-eol/](https://lubuntu.me/bionic-eol/)

A recent Ubuntu Weekly Newsletter
- [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue681#Lubuntu_18.04_LTS_End_of_Life_and_Current_Support_Statuses](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue681#Lubuntu_18.04_LTS_End_of_Life_and_Current_Support_Statuses)
(or on this forum see [https://ubuntuforums.org/showthread.php?t=2461582](https://ubuntuforums.org/showthread.php?t=2461582)) highlighted flavors are now EOL.

---

### Post by bug5 on 2021-05-27
Yes, but unfortunately upgrading is not an option at the moment because we have about 100 Devices that would need to be upgraded, and not much time avaliable...

---

### Post by bug5 on 2021-05-31
Solved, upgrading linux-firmware package fixed the issue:
linux-firmware (1.173.20) over (1.173.14) ...

---

