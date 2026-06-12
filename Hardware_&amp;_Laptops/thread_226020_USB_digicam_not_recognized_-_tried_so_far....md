---
title: "USB digicam not recognized - tried so far..."
date: 2006-07-30
forum: Hardware &amp; Laptops
---

### Post by DirkP on 2006-07-30
A (genericish) "VuPoint" that previously mounted under Hoary (with DCIM folders, IIRC).

lsusb > camera-unplugged

Bus 001 Device 002: ID 045e:0025
Microsoft Corp. IntelliEye Mouse
Bus 001 Device 001: ID 0000:0000

--

Nothing shows with
dmesg |tail -n 20

--

lsmod

uhci_hcd               33680  0
usbcore               129668  3 usbhid,uhci_hcd

--

Device Manager

USB Raw Device Access
usbraw.device strlist /dev/bus/usb/001/001
usbraw.device strlist /dev/bus/usb/001/002

--

@dapper:~$ mount
/dev/hde1 on / type reiserfs (rw,noatime,notail)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-23-386/volatile type tmpfs (rw)
/dev/hde3 on /home type reiserfs (rw,noatime,notail)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

/proc/bus/usb/001 Dir has two files

/proc/bus/usb/001/001 shows an 43B  Type application/octet-stream file

/proc/bus/usb/001/002 has a 52B  Type application/octet-stream file

/proc/bus/usb/devices is empty

--

gtkam and digikam USB PTP class can not initialize

gthumb cannot import

--

gnome-volume-properties    appears set properly

--

I've tried finding the device manually - no luck

Appreciate any help, as my Ubuntu knowledge is fairly fragmented

---

