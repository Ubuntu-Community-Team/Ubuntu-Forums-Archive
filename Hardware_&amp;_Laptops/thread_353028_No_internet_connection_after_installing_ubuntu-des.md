---
title: "No internet connection after installing ubuntu-desktop"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by Matodo on 2007-02-04
Hello everyone
The installation of Ubuntu 6.10 Server and the ueagle-atm driver have finished successfully. Then I've installed ubuntu-desktop.
After rebooting, the diode of ADSL of the modem (Sagem f@st 800) does not ignite, and no internet connection.
Here are the outputs of these commands
```

$ uname -r
2.6.17-10-server
$ dmesg | grep ueagle
[42949390.290000] ueagle_atm: Unknown symbol usbatm_usb_disconnect
[42949390.290000] ueagle_atm: Unknown symbol usbatm_usb_probe
...

```
I would like to fix this problem, Please help.

---

### Post by Matodo on 2007-02-04
I am connected now :)
I've downloaded and installed [linux-headers-2.6.17-10-server_2.6.17.1-10.34_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-headers-2.6.17-10-server_2.6.17.1-10.34_i386.deb)
then I uninstalled and insalled the driver.

---

