---
title: "Belkin F9L1108 USB wifi adapter not working"
date: 2014-12-20
forum: Hardware
---

### Post by Jack_Marston on 2014-12-20
Hello I just installed ubuntu 14.0.4 and have been unable to use my Belkin wifi adapter any help would be appreciated. PS i am new to linux and the forums.

---

### Post by dave157 on 2014-12-20
Hi 
Since you are new this might be scarey but really it is not. The adapter you are using has the same driver as the one in the post below. I would type the code in the terminal by copy and pasting the code into the terminal to prevent typo errors  We have to install firmware for your adapter. Ok open a terminal window by pressing Ctrl + Alt + T. If this shortcut does not work search for terminal and click on it. 

First type two commands for me to post these use go advance use the number # above and copy pates the output for each one.

lspci  post output

lsusb post output

dave

---

### Post by Jack_Marston on 2014-12-20
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file




Usage: lsusb [options]...
List USB devices
  -v, --verbose
      Increase verbosity (show descriptors)
  -s [[bus]:][devnum]
      Show only devices with specified device and/or
      bus numbers (in decimal)
  -d vendor:[product]
      Show only devices with the specified vendor and
      product ID numbers (in hexadecimal)
  -D device
      Selects which device lsusb will examine
  -t, --tree
      Dump the physical USB device hierarchy as a tree
  -V, --version
      Show version of program
  -h, --help
      Show usage and help

hope this helps

---

### Post by jeremy31 on 2014-12-21
Post the output from these commands```
lspci -nnk | grep -iA2 net
``````
lsusb
```

---

### Post by Jack_Marston on 2014-12-21
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7721]
    Kernel driver in use: r8169




Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 045e:070f Microsoft Corp. 
Bus 002 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 04e8:3413 Samsung Electronics Co., Ltd SCX-4100 Scanner
Bus 004 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 050d:110a Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

here you go

---

### Post by jeremy31 on 2014-12-21
I think this will work
```
[COLOR=#333333][FONT=monospace]wget [/FONT][/COLOR][http://wielki.tk/vostro/debs/bt-bcm43142-onereic_0.0+20111116somerville2_amd64.deb](http://wielki.tk/vostro/debs/bt-bcm43142-onereic_0.0+20111116somerville2_amd64.deb)
```[COLOR=#333333][FONT=monospace]```
dpkg -i bt-bcm43142-onereic_0.0+20111116somerville2_amd64.deb bt-bcm43142
```
Then edit a file ```
gksudo gedit /etc/modprobe.d/bcm43142.conf
```

You should see this ```
[COLOR=#222222][FONT=Verdana]# Load firmware of BCM43142[/FONT][/COLOR][/FONT][/COLOR]
install btusb /sbin/modprobe --ignore-install btusb && echo '0a5c 21d3' > /sys/bus/usb/drivers/btusb/new_id && echo '0a5c 21d7' > /sys/bus/usb/drivers/btusb/new_id && echo '0a5c 21e1' > /sys/bus/usb/drivers/btusb/new_id && echo '0a5c 21e3' > /sys/bus/usb/drivers/btusb/new_id && hciconfig hci0 up && /usr/bin/brcm_patchram_plus_usb --patchram /lib/firmware/BCM43142A0_001.001.011.0028.0036.hcd hci0 &
```
Change it to this```
# Load firmware of BCM43142
install btusb /sbin/modprobe --ignore-install btusb && echo '0a5c 21d3' > /sys/bus/usb/drivers/btusb/new_id && echo '0a5c 21d7' > /sys/bus/usb/drivers/btusb/new_id && echo '0a5c 21e1' > /sys/bus/usb/drivers/btusb/new_id && echo '0a5c 21e8' > /sys/bus/usb/drivers/btusb/new_id && hciconfig hci0 up && /usr/bin/brcm_patchram_plus_usb --patchram /lib/firmware/BCM43142A0_001.001.011.0028.0036.hcd hci0 &
```
Save, exit program then ```
sudo modprobe -r btusb
``````
sudo modprobe btusb
``` ```
hcitool dev
``` And hopefully the last code returns the MAC address of your bluetooth device and ```
hcitool scan
``` will find visible bluetooth devices

---

### Post by Jack_Marston on 2014-12-21
Sorry but its my wifi adapter thats not working not bluetooth.

---

### Post by jeremy31 on 2014-12-21
Sorry, try the suggestions in this post [http://ubuntuforums.org/showthread.php?t=2176114&p=12799964#post12799964](http://ubuntuforums.org/showthread.php?t=2176114&p=12799964#post12799964)
The post is over a year old but for once I think it is relevant and some of the changes are only 11 days old

---

### Post by Jack_Marston on 2014-12-26
I have tried the instructions in the post you provided but after downloading the driver when i run "make" i get this

make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.13.0-43-generic/build M=/home/jack/rtl8192du-master  modules 
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-43-generic' 
  CC [M]  /home/jack/rtl8192du-master/core/rtw_cmd.o 
  CC [M]  /home/jack/rtl8192du-master/core/rtw_security.o 
  CC [M]  /home/jack/rtl8192du-master/core/rtw_debug.o 
  CC [M]  /home/jack/rtl8192du-master/core/rtw_io.o 
  CC [M]  /home/jack/rtl8192du-master/core/rtw_ioctl_set.o 
  CC [M]  /home/jack/rtl8192du-master/core/rtw_ieee80211.o 
  CC [M]  /home/jack/rtl8192du-master/core/rtw_mlme.o 
  CC [M]  /home/jack/rtl8192du-master/core/rtw_mlme_ext.o 
  CC [M]  /home/jack/rtl8192du-master/core/rtw_wlan_util.o 
  CC [M]  /home/jack/rtl8192du-master/core/rtw_pwrctrl.o 
  CC [M]  /home/jack/rtl8192du-master/core/rtw_rf.o 
  CC [M]  /home/jack/rtl8192du-master/core/rtw_recv.o 
  CC [M]  /home/jack/rtl8192du-master/core/rtw_sta_mgt.o 
  CC [M]  /home/jack/rtl8192du-master/core/rtw_ap.o 
  CC [M]  /home/jack/rtl8192du-master/core/rtw_xmit.o 
/home/jack/rtl8192du-master/core/rtw_xmit.c: In function ‘update_attrib’: 
/home/jack/rtl8192du-master/core/rtw_xmit.c:441:2: error: implicit declaration of function ‘ether_addr_copy’ [-Werror=implicit-function-declaration] 
  ether_addr_copy(pattrib->dst, ehdr->h_dest); 
  ^ 
cc1: some warnings being treated as errors 
make[2]: *** [/home/jack/rtl8192du-master/core/rtw_xmit.o] Error 1 
make[1]: *** [_module_/home/jack/rtl8192du-master] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-43-generic' 
make: *** [modules] Error 2

any help would be greatly appreciated

---

### Post by jeremy31 on 2014-12-27
Try the commands in terminal again, it looks like some changes were made 11 hours ago to fix errors, use this command first after cd rtl8192du ```
make clean
```

It did build and install on my laptop with 3.13.0-37 and 3.13.0-44 with a couple warnings

---

### Post by Jack_Marston on 2014-12-27
IT WORKED!!!!! Thank you so much! i have tried to make this work for so long.:lol:

---

### Post by jeremy31 on 2014-12-27
> **Jack_Marston said:**
> IT WORKED!!!!! Thank you so much! i have tried to make this work for so long.:lol:

A good thing that Larry Finger fixed some code

---

### Post by Jack_Marston on 2014-12-29
It works but every time i reboot i have to run "sudo modprobe 8192du" to get it to work any way i don't have to do that?

---

