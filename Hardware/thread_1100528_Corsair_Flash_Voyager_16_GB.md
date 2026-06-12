---
title: "Corsair Flash Voyager 16 GB"
date: 2009-03-19
forum: Hardware
---

### Post by Kjoller on 2009-03-19
Hi 

I just bought a Lenovo IdeaPad and installed ubuntu on it (First time ubuntu user).

I have a Corsair Voyager 16 gb (Works on OS X and Windows), but I cannot get it to work on my ubuntu dist.

Can any one help me?

---

### Post by taurus on 2009-03-19
Cannot get it to work as it wouldn't mount it you can't write to it?

Open a terminal and post the outputs of these commands?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by Kjoller on 2009-03-19
I am not able to see it, in my system.

Here it the result of the commands.

sudo fdisk -l:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19084   153292198+  83  Linux
/dev/sda2           19085       19457     2996122+   5  Extended
/dev/sda5           19085       19457     2996091   82  Linux swap / Solaris

df -h:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             144G  3.7G  133G   3% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  124K  500M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2.8M  498M   1% /dev
tmpfs                 501M  124K  500M   1% /dev/shm
lrm                   501M  2.0M  499M   1% /lib/modules/2.6.27-11-generic/volatile

Thank you in advance

---

### Post by taurus on 2009-03-19
What are the outputs of these two commands from a terminal?

```
lsusb
dmesg | tail
```

---

### Post by Kjoller on 2009-03-19
Here you go.

lsusb:
Bus 005 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 005 Device 002: ID 5986:0241 Acer, Inc 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0a5c:2150 Broadcom Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

 dmesg | tail
[ 6768.480167] usb 1-1: new full speed USB device using uhci_hcd and address 4
[ 6778.888205] usb 1-1: device not accepting address 4, error -110
[ 6779.000179] usb 1-1: new full speed USB device using uhci_hcd and address 5
[ 6789.408086] usb 1-1: device not accepting address 5, error -110
[ 6789.408164] hub 1-0:1.0: unable to enumerate USB device on port 1
[ 7521.729127] usb 1-1: new full speed USB device using uhci_hcd and address 6
[ 7536.840375] usb 1-1: device descriptor read/64, error -110
[ 7552.057135] usb 1-1: device descriptor read/64, error -110
[ 7552.273150] usb 1-1: new full speed USB device using uhci_hcd and address 7
[ 7567.384152] usb 1-1: device descriptor read/64, error -110

---

### Post by Kjoller on 2009-03-20
nothing ?

---

