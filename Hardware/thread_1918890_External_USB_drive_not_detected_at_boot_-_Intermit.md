---
title: "External USB drive not detected at boot - Intermittent Problem"
date: 2012-02-01
forum: Hardware
---

### Post by bruban on 2012-02-01
Hello,

I have an intermittent problem that has been annoying me since 11.04. I have not been able to find a resolution despite numerous searches via fora and the internet.

I mount an external USB 3 drive via /etc/fstab at boot and use it for backups. 

The drive is only recognised at boot time if I start the computer from a cold boot after the power has been turned off at the wall.

The drive is never recognised at boot if I do a reboot or if I shutdown and then restart, leaving the power turned on at the wall.

I'm running Ubuntu 11.10. This instance was upgraded from 11.04. It is not a new install.

The external drive is a Western Digital MyBook Essential USB 3.0, 2TB drive. The motherboard supports USB3.

This is becoming annoying. Does anyone have any hints as to how to resolve this issue?

lsusb readouts below:

cold boot, from power off start.

[HTML]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 003 Device 002: ID 2040:5200 Hauppauge 
Bus 004 Device 002: ID 1058:1130 Western Digital Technologies, Inc. 
Bus 001 Device 004: ID 046d:c526 Logitech, Inc. Nano Receiver
Bus 001 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver[/HTML]

The associated dmesg message is:

[HTML][    3.669837] scsi6 : usb-storage 4-2:1.0
[    3.669988] usbcore: registered new interface driver usb-storage
[/HTML]

lsusb after reboot:

[HTML]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 004: ID 046d:c526 Logitech, Inc. Nano Receiver
Bus 001 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver[/HTML]

lsusb after cold boot, without turning power off at wall at start

[HTML]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 004: ID 046d:c526 Logitech, Inc. Nano Receiver
Bus 001 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
[/HTML]

---

### Post by madvinegar on 2012-02-02
When your drive is not recognised (*never recognised at boot if I do a reboot or if I shutdown and then restart, leaving the power turned on at the wall*) open up a terminal, log in as root and write

```
modprope usb-storage
```

and tell me if after that it is recognized.


If it is, I will tell you what to do next.

---

### Post by bruban on 2012-02-02
From 2 out of 6 boots as per options above, I found the following:

```
modprobe --verbose usb-storage
insmod /lib/modules/3.0.0-15-generic/kernel/drivers/usb/storage/usb-storage.ko 

```

---

### Post by madvinegar on 2012-02-02
Was your drive mounted after you wrote at terminal as root **modprobe usb-storage**???

---

### Post by bruban on 2012-02-02
Thanks for following up on this.

One thing that I haven't mentioned is that I've configured the external drive with lvm.

Cold boot, power on before boot:

External drive not mounted after boot.

> root@mythtv:/tmp# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 004: ID 046d:c526 Logitech, Inc. Nano Receiver
Bus 001 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
root@mythtv:/tmp# 
root@mythtv:/tmp# modprobe --verbose usb-storage
insmod /lib/modules/3.0.0-15-generic/kernel/drivers/usb/storage/usb-storage.ko 
root@mythtv:/tmp# 
root@mythtv:/tmp# mount -t ext4 /dev/vgbackup/lvbackup /backup
mount: special device /dev/vgbackup/lvbackup does not exist
root@mythtv:/tmp# 


=====

Warm boot, power on before boot:

External drive not mounted after boot.


```
root@mythtv:/tmp# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 004: ID 046d:c526 Logitech, Inc. Nano Receiver
Bus 001 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
root@mythtv:/tmp# 
root@mythtv:/tmp# modprobe --verbose usb-storage
insmod /lib/modules/3.0.0-15-generic/kernel/drivers/usb/storage/usb-storage.ko 
root@mythtv:/tmp# 
root@mythtv:/tmp# mount -t ext4 /dev/vgbackup/lvbackup /backup
mount: special device /dev/vgbackup/lvbackup does not exist
root@mythtv:/tmp# 

```

=====

Cold boot, power off before boot:

External drive not mounted after boot.

> root@mythtv:/tmp# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 003 Device 002: ID 2040:5200 Hauppauge 
Bus 004 Device 002: ID 1058:1130 Western Digital Technologies, Inc. 
Bus 001 Device 004: ID 046d:c526 Logitech, Inc. Nano Receiver
Bus 001 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
root@mythtv:/tmp# 
root@mythtv:/tmp# modprobe --verbose usb-storage
root@mythtv:/tmp# 
root@mythtv:/tmp# mount -t ext4 /dev/vgbackup/lvbackup /backup
mount: special device /dev/vgbackup/lvbackup does not exist
root@mythtv:/tmp# 


---

### Post by LarsO on 2012-02-11
> **madvinegar said:**
> When your drive is not recognised (*never recognised at boot if I do a reboot or if I shutdown and then restart, leaving the power turned on at the wall*) open up a terminal, log in as root and write

```
modprope usb-storage
```

and tell me if after that it is recognized.


If it is, I will tell you what to do next.

I have been watching this post for a couple of days waiting with anticipation for your answer on what to do next...
I have the exact same problem with 11.10 and a Seagate USB3 2TB HDD.
When I run sudo modprobe usb-storage   moments later the drive is mounted.

---

### Post by madvinegar on 2012-02-11
> **LarsO said:**
> I have been watching this post for a couple of days waiting with anticipation for your answer on what to do next...
I have the exact same problem with 11.10 and a Seagate USB3 2TB HDD.
When I run sudo modprobe usb-storage   moments later the drive is mounted.


Sorry my friend. Bruban has not replied clearly if this helped him or not so I have not responded.

As regards your problem do the following:

As root (i.e. write in terminal gksudo nautilus) and navigate to /etc/modules.

Open the file "modules" and add the line

```
usb_storage
```

i.e. the file "modules" should look something like this:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

usb_storage
lp
lp
lp
lp

```

Save the file and exit.

From now on, the usb_storage module will be loaded at each start-up.
Check it and let me know if everything worked out fine.;)

---

### Post by bruban on 2012-02-11
LarsO and Madvinegar,

Many thanks for following up on this.

Sorry, on re-reading my replies they do appear a bit cryptic.

I have just re-tested this after a reboot with 'modprobe usb-storage'.

After 20 minutes, the drive is still not mounted automatically. I cannot mount it manually either as the drive is not recognised.

I then unplugged the USB cable to the external drive and replugged it in 20 seconds later. On checking several minutes later the drive was not recognised.

I did the same with the power cable to the drive with the same result.


Just to be clear, the external drive is configured with lvm2. The filesystem that I'm trying to mount is ext4 that is within a logical volume in a volume group (similar to my other filesystems on two internal drives. I don't have this problem with the internal drives).

Perhaps this is adding to the issue?

---

### Post by LarsO on 2012-02-11
Thanks so much MadVinegar. Adding usb-storage to /etc/modules now gives me consistent mount every time!
I'm using the UUID of the external HDD to mount on /mnt/Backup in fstab. It's working great now. (btw, Bruban, Im using ext4 also)
I found the external drive with:
```
sudo blkid
```

---

### Post by bruban on 2012-02-12
Thanks for the pointer LarsO,

However, using the UUID did not make a difference.

Bruce

---

### Post by madvinegar on 2012-02-12
> **LarsO said:**
> Thanks so much MadVinegar. Adding usb-storage to /etc/modules now gives me consistent mount every time!
 It's working great now. 


Glad I helped you my friend !!!:D

---

### Post by bruban on 2012-02-12
Madvinegar,

I also tested adding usb_storage to /etc/modules.

It did not make a difference.

I still have the original problem.

---

### Post by bruban on 2012-06-15
This issue still exists after upgrade to Ubuntu 12.04.

In summary:


[LIST]
[*]External USB 3 drive is recognised on cold boot.
[/LIST]

[LIST]
[*]External USB 3 drive is not recognised on warm boot.
[*]After a warm boot, if I type (as root) modprobe usb-storage, the drive is still not recognised.
[/LIST]
I'm at a loss on how to proceed with this. Any thoughts will be appreciated.

---

