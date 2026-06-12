---
title: "nvidia driver"
date: 2010-01-07
forum: Hardware
---

### Post by hirohitosan on 2010-01-07
Hi there. I installed 9.10 on one of my desktops at work. I want to activate the driver for nvidia and "Downloading and installing driver" failed. I connect to IN through proxy server. I set up the proxy server System > Preferences > Network Proxy and I could update my system but I cannot download the driver.

There is a way to manual download the driver?
or another way to install the driver?

Thanks

---

### Post by unmole on 2010-01-07
-Download the linux driver from the nvidia website.
-Hit Alt+Ctrl+F2
-Login to the virtual terminal
-Do a ```
sudo stop gdm
```
-Then finally do a ```
 sudo sh /location/of/the/downloaded/driver 
```
-Reboot.

---

