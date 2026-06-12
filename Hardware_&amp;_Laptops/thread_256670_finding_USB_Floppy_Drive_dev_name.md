---
title: "finding USB Floppy Drive dev name"
date: 2006-09-13
forum: Hardware &amp; Laptops
---

### Post by texture on 2006-09-13
noob alert, please excuse me

I trying to find the device name (/dev/f???) for a USB floppy drive.

I have ubuntu 6.06 installed on an Acer TravelMate 4020, the OS is running smoothly and I can find the USB drive and read files from in the file browser. However I'm running terminal based backup software and I want to add the USB floppy as a back up device and I'm required to enter the exact dev name. Can you advise what the name would be or where I could look it up. Thanks in advance! \\:D/

---

### Post by gsdefender on 2006-09-13
After the device has been attached, do a 

```

dmesg | tail

```

and you should see some information about it, including the device file.

HTH.

---

### Post by texture on 2006-09-13
> **gsdefender said:**
> After the device has been attached, do a 

```

dmesg | tail

```

and you should see some information about it, including the device file.

HTH.

thanks but I didn't see it listed, here is the result:

acerlaptop@acerlaptop:~$ dmesg | tail
[17179604.652000] Bluetooth: HCI device and connection manager initialized
[17179604.652000] Bluetooth: HCI socket layer initialized
[17179604.684000] Bluetooth: L2CAP ver 2.8
[17179604.684000] Bluetooth: L2CAP socket layer initialized
[17179604.716000] Bluetooth: RFCOMM socket layer initialized
[17179604.716000] Bluetooth: RFCOMM TTY layer initialized
[17179604.716000] Bluetooth: RFCOMM ver 1.7
[17179605.112000] eth1: no IPv6 routers present
[17179605.564000] eth0: no IPv6 routers present
[17195811.048000] synaptics: using relaxed packet validation
acerlaptop@acerlaptop:~$

---

### Post by gsdefender on 2006-09-19
OK. Well, if it is mountable (as you said), you'll be better off doing

```

mount

```

without any argument after the device has been recognized to have a list of currently mounted devices.

---

### Post by texture on 2006-09-20
> **gsdefender said:**
> OK. Well, if it is mountable (as you said), you'll be better off doing

```

mount

```

without any argument after the device has been recognized to have a list of currently mounted devices.

thanks for your suggestion, this was the result:

```
acerlaptop@acerlaptop:~$ mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-386/volatile type tmpfs (rw)
acerlaptop@acerlaptop:~$

```

So I tried entering "procbususb" as the device name, as well as "/proc/bus/usb" but I was not successful. Any other suggestions?

---

### Post by gsdefender on 2006-09-29
It's strange - it seems not to be detected at all. Strange.

---

