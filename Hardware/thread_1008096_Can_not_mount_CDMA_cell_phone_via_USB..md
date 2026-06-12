---
title: "Can not mount CDMA cell phone via USB."
date: 2008-12-11
forum: Hardware
---

### Post by ToshibaLaptoplinux on 2008-12-11
I would like to mount my cell phone via USB and/or sync data with my Toshiba Laptop running Ubuntu Hardy Heron. I tried bitpim which seems to be a very, very nice application but either is not compatible with my phone or I am not configuring it properly.

Pertinent Details:

1) The phone is a Toshiba W47T which is a Japanese model CDMA x1 WIN phone.

2) I am running Ubuntu Hardy Heron.

lsb_release -rd:
Description: Ubuntu 8.04.1
Release: 8.04

uname -a:
Linux laptop 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux

3)dmesg:
[ 1801.987966] usb 2-2: USB disconnect, address 4
[ 1825.470893] usb 2-2: new full speed USB device using uhci_hcd and address 5
[ 1825.513299] usb 2-2: configuration #1 chosen from 1 choice
[ 1825.516514] cdc_acm 2-2:1.0: ttyACM0: USB ACM device

4)lsusb:
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 005: ID 0930:0d1c Toshiba Corp.
Bus 002 Device 003: ID 0d62:a100 Darfon Electronics Corp. Benq Mouse
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

5)mount:
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-22-generic/volatile type tmpfs (rw)
/dev/sda2 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/"deleted for privacy"/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user="deleted for privacy")

6) tail -s 3 -f /var/log/messages:
Dec 11 17:07:05 laptop -- MARK --
Dec 11 17:13:21 laptop kernel: [ 2230.775167] usb 2-2: USB disconnect, address 7
Dec 11 17:27:05 laptop -- MARK --
Dec 11 17:47:05 laptop -- MARK --
Dec 11 18:07:05 laptop -- MARK --
Dec 11 18:27:05 laptop -- MARK --
Dec 11 18:47:05 laptop -- MARK --
Dec 11 18:53:29 laptop kernel: [ 3921.742270] usb 2-2: new full speed USB device using uhci_hcd and address 8
Dec 11 18:53:29 laptop kernel: [ 3921.787053] usb 2-2: configuration #1 chosen from 1 choice
Dec 11 18:53:29 laptop kernel: [ 3921.787793] cdc_acm 2-2:1.0: ttyACM0: USB ACM device

It seems clear that the connection is being recognized but for some odd reason it won't mount. I do have the USB driver for the phone but of course it is a windows .exe file.

Anybody have any idea how I can mount this and get Bitpim or another application to recognize the device and sync with it?

Thanks

---

