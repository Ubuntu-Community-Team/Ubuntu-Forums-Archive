---
title: "WIFI not working : Broadcom :Dell Ispiron 1520"
date: 2009-08-08
forum: Hardware
---

### Post by ajprince on 2009-08-08
I have a problem in connecting to internet via WIFI.
I am using the ubunto 9.04 in Dell Inspiron 1520

```
lspci | grep -i broadcom
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
```

I ran these command and black listed  as per the steps in  [http://www.linuxforums.org/forum/wireless-internet/74258-wireless-network-not-working-dell-laptop-ubuntu.html](http://www.linuxforums.org/forum/wireless-internet/74258-wireless-network-not-working-dell-laptop-ubuntu.html)
```

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

```

sudo apt-get install ndiswrapper-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndiswrapper-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ndiswrapper-common
E: Package ndiswrapper-utils has no installation candidate
```

```

 sudo ndiswrapper -i windows_driver_INF_file 
install argument must be .inf file
```

but i couldnt find the inf file.Please help me out.

---

### Post by sergiom99 on 2009-08-08
Hi. I have the same card, BCM4328 and it works out of the box since Hardy. No need for ndiswrapper and Window$ INF files.
You are following instructions from an old 2006 post! Newer kernels already have support for Broadcom chipsets.

Just do a:
```
sudo apt-get update && sudo apt-get upgrade
```
to update your system. Reboot. Then go System > Administration > Hardware Drivers and check "Broadcom STA Wireless Driver."

Check for a detailed explanation: [http://ubuntuforums.org/showthread.php?t=870575](http://ubuntuforums.org/showthread.php?t=870575)

Good luck!

---

### Post by ajprince on 2009-08-09
Hi ..
Thx a lot . My issue is solved and im able to connect to wireless access point.
 
and also the below link was helpful to do the rest.
[http://www.linux.com/community/blogs/Managing-Network-Connections-in-Ubuntu.html](http://www.linux.com/community/blogs/Managing-Network-Connections-in-Ubuntu.html)

---

### Post by rithvik on 2010-01-23
Best answer for this problem. In 5 minutes the issue is resolved. Thanks for the great tip

---

