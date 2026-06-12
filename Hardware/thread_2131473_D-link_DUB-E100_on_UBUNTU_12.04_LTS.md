---
title: "D-link DUB-E100 on UBUNTU 12.04 LTS"
date: 2013-04-01
forum: Hardware
---

### Post by bobx on 2013-04-01
I am trying to get a D-Link DUN-E100 USB to RJ45 converter to work. I am running 12.04 LTS Kernel 3.2.0-21.

I first just plugged in the device but it did not "plug & play"

I loaded the supplied driver and then tried to "make" it. I got the following.

root@XXXX:/usr/local/LINUX2.6.14_REV101# make
make -C /lib/modules/3.2.0-31-generic-pae/build SUBDIRS=/usr/local/LINUX2.6.14_REV101 modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-31-generic-pae'
  CC [M]  /usr/local/LINUX2.6.14_REV101/asix.o
/usr/local/LINUX2.6.14_REV101/asix.c:840:2: error: unknown field \u2018ndo_set_multicast_list\u2019 specified in initializer
/usr/local/LINUX2.6.14_REV101/asix.c:840:2: warning: initialization from incompatible pointer type [enabled by default]
/usr/local/LINUX2.6.14_REV101/asix.c:840:2: warning: (near initialization for \u2018ax88x72_netdev_ops.ndo_do_ioctl\u2019) [enabled by default]
/usr/local/LINUX2.6.14_REV101/asix.c:1533:2: error: unknown field \u2018ndo_set_multicast_list\u2019 specified in initializer
/usr/local/LINUX2.6.14_REV101/asix.c:1533:2: warning: initialization from incompatible pointer type [enabled by default]
/usr/local/LINUX2.6.14_REV101/asix.c:1533:2: warning: (near initialization for \u2018ax88772b_netdev_ops.ndo_do_ioctl\u2019) [enabled by default]
make[2]: *** [/usr/local/LINUX2.6.14_REV101/asix.o] Error 1
make[1]: *** [_module_/usr/local/LINUX2.6.14_REV101] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-31-generic-pae'
make: *** [default] Error 2

What Now ???

Bob

---

### Post by ahallubuntu on 2013-04-01
~

---

### Post by bobx on 2013-04-01
Ok that one did compile and load but the device does not show up.

---

### Post by ahallubuntu on 2013-04-01
~

---

### Post by bobx on 2013-04-02
Yes I did a make install

It is rev C1

lshw -C network only shows my other ethernet card and my wireless card.

lsusb show following

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 006 Device 002: ID 13ba:0017 Unknown PS/2 Keyboard+Mouse Adapter
Bus 007 Device 002: ID 046d:c52a Logitech, Inc.

---

### Post by bobx on 2013-04-02
Do I need to have usbnet module installed ? 

here are the lsusb results
root@XXX:/lib/modules# lsmod | grep usb
usbnet                 25214  0 
usbhid                 41937  0 
hid                    77428  1 usbhid
usb_storage            39683  1 ums_realtek

---

