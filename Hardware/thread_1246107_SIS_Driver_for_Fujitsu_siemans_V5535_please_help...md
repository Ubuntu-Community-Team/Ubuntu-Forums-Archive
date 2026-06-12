---
title: "SIS Driver for Fujitsu siemans V5535 please help..."
date: 2009-08-21
forum: Hardware
---

### Post by richwainers on 2009-08-21
Hi I have recently decided to put Ubuntu on my Fujitsu laptop, however the screen resolution is incorrect and I can't adjust it. In the display is show the monitor as been 'unknown'. As the laptop is wide screen and the default resolution is 4:3 it is very annoying. I believe the problem is the driver is wrong, I understand from reading other forums SIS don't support Ubuntu.

I have tried to install drivers recommended by others but can not install them. I am complete beginner and would welcome any help, but if someone could give me a step by step guide on this it would be great.

I am running Ubuntu 9.04

---

### Post by Yellow Pasque on 2009-08-21
Which chipset do you have? (I think there are different drivers)
```
lspci | grep VGA
```

---

### Post by richwainers on 2009-08-21
When I run the command above it displays the following:

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

However Fujitsu say it is 672.

I am completely confused and don't really want to go back to windows pls pls pls help.

---

