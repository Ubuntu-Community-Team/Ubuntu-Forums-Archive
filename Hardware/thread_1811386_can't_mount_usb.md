---
title: "can't mount usb"
date: 2011-07-24
forum: Hardware
---

### Post by jason verrastro on 2011-07-24
I cant mount any usb drives. I am using 11.04 i have tried everything i can think of but have had no luck. dmesg looks fine 
```

[   43.206265] wlan0: associated
[   43.207753] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   54.032093] wlan0: no IPv6 routers present
[  609.993649] usb 1-7: USB disconnect, address 4
[  630.852200] usb 1-7: new high speed USB device using ehci_hcd and address 5
[  630.988503] scsi7 : usb-storage 1-7:1.0
[ 1492.971597] usb 1-7: USB disconnect, address 5
[ 1587.788185] usb 1-7: new high speed USB device using ehci_hcd and address 6
[ 1587.927175] scsi8 : usb-storage 1-7:1.0
```

(last few lines)

lsusb looks fine 


```
jason@jasons-laptop:~$ lsusb 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 04e8:f000 Samsung Electronics Co., Ltd 
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
jason@jasons-laptop:~$ 
```

(samsung is the usb drive in this case)

but there is nothing in fdisk

```
jason@jasons-laptop:~$ sudo fdisk -l
[sudo] password for jason: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x495d01ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10240001    5  Extended
/dev/sda2           18528       19458     7471104   82  Linux swap / Solaris
/dev/sda4            1276       18527   138576690   83  Linux
/dev/sda5               1        1275    10240000   83  Linux

Partition table entries are not in disk order
jason@jasons-laptop:~$ 
```

(just the hard drive)

when i try unplugging and running 

```
sudo tail -f /var/log/messages
```

and plugging it back in nothing happens. this is happening with all usb drives. all other usb devices work fine. 

I also tried plugging in to a M$ box and it works fine and yes i unplugged it safely. i am at a complete loss as what to do next.

---

### Post by temporary88 on 2011-09-27
check this [https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch/+bug/755342]("http://ubuntuforums.org/This%20is%20known%20bug:%20https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch/+bug/755342%20%20This%20is%20a%20problem%20with%20the%20usb-modeswitch,%20if%20you%20disable%20it%20in%20/etc/usb_modeswitch.conf%20=%3E%20DisableSwitching=1%20then%20it%20works")
or this [http://ubuntuforums.org/showthread.php?p=11289252#post11289252](http://ubuntuforums.org/showthread.php?p=11289252#post11289252)

---

