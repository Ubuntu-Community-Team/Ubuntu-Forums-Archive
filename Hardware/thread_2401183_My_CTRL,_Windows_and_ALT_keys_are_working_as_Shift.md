---
title: "My CTRL, Windows and ALT keys are working as Shift"
date: 2018-09-14
forum: Hardware
---

### Post by abdurrahman2234 on 2018-09-14
Hello everyone. I installed Ubuntu today, so I'm new. But I have a problem. My CTRL, Windows and ALT keys are working like Shift. My Keyboard is "Everest Rampage KM-R1 Gaming Set". I did the fix here:
**[https://bitbucket.org/Swoogan/aziokbd](https://bitbucket.org/Swoogan/aziokbd)**


But it didn't work. I tried to do "blacklisting" thing. It didn't work too. So, these are the things I tried:


1 - Installed **[https://bitbucket.org/Swoogan/aziokbd](https://bitbucket.org/Swoogan/aziokbd)**, used ***"sudo nano /etc/default/grub"***, Changed ***"GRUB_CMDLINE_LINUX_DEFAULT"*** like: ***"options usbhid quirks=0x0c45:0x7603:0x0004"***.


2 - Changed ***"GRUB_CMDLINE_LINUX_DEFAULT"*** like: ***"options usbhid quirks=0x0c45:0x7603:0x4"***.


3 - Changed ***"GRUB_CMDLINE_LINUX_DEFAULT"*** like: ***"options usbhid quirks=0x0c45:0x7603:0x7"***.


4 - Created a file ***"/etc/modprobe.d/usbhid.conf"*** and wrote ***"options usbhid quirks=0x0c45:0x7603:0x0004"*** in it. After, changed the ***0x0004*** to ***0x0007***.


Nothing worked. Please help me.

---

