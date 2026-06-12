---
title: "Screen brightness keys do not work!"
date: 2010-10-23
forum: Hardware
---

### Post by rcasiano on 2010-10-23
Hello everybody, I am new to linux and to this forum. I come here today asking for help. I recently purchased an HP G42-232NR and dual booted Ubuntu 10.10 64 bit and updated everything via the update command line code. My dedicated screen brightness buttons do not function in Ubuntu and this is very problematic as it drains the battery quickly and hurts my eyes. The dedicated volume buttons function in Ubuntu as does the wireless button. Everything works in Windows 7. How can I fix this problem? Once again, I am new, so please let me know what anybody needs to help me. Thank you very much in advance.

---

### Post by zeroseven0183 on 2010-10-24
Hi rcasiano, chances are your Ubuntu is suffering from a kernel bug. I have HP Pavilion dv3-2106tu (Intel) and cannot adjust the brightness. I did almost everything but still no success.

I stumbled on several thread in the forum, some people were able to fix it though.

Check out this [bug report #568611]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611") and see if there's something there help you fix the brightness issue. I downloaded the PPA and added acpi_backlight=vendor in my grub.cfg.

---

### Post by zeroseven0183 on 2010-10-24
Just an update, my screen brightness control is now working. 

Here's what I did after installing Ubuntu 10.10,
1. added this [PPA by Kamal Mustafa]("https://launchpad.net/%7Ekamalmostafa/+archive/linux-kamal-mjgbacklight").
2. ran ```
sudo apt-get update
```
3. installed the latest linux kernel
4. edited my /etc/default/grub by adding ```
GRUB_CMDLINE_LINUX=acpi_backlight=vendor
```
5. then ```
sudo update-grub
```
6. reboot

---

