---
title: "Disappearing USB drive Realtek RTL9210 with Samsung 980 NVMe"
date: 2021-08-18
forum: Hardware
---

### Post by hpuri2 on 2021-08-18
[COLOR=#555555][FONT=Roboto]Looking for help nail down a problem.
This is on a Raspberry Pi 4 booted either from SDcard or Sandisk USB ultrafit   

The drive works fine for about 20 minutes and then disappears from /sys/bus/usb/devices/ only when docker is running workloads , otherwise it hangs around forever. Not sure why Docker is tripping it up.[/FONT][/COLOR]
[COLOR=#555555][FONT=Roboto]The only way to get back the drive is to unplug , replug and remount it[/FONT][/COLOR]
[COLOR=#555555][FONT=Roboto]The problem shows up with a WD spinning drive as well connected via USB -> SATA adapter[/FONT][/COLOR]
[COLOR=#555555][FONT=Roboto]I tried a different cable , going via a unpowered USB hub etc.[/FONT][/COLOR]
Also this is a USB-C device capable of 5G but shows up only as 480M

```

ubuntu@pi4:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0781:5583 SanDisk Corp. Ultra Fit
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:9210 Realtek Semiconductor Corp. RTL9210 M.2 NVME Adapter
Bus 001 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


ubuntu@pi4:~$ lsusb -t
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=dwc2/1p, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M
    |__ Port 1: Dev 2, If 0, Class=Mass Storage, Driver=usb-storage, 5000M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/1p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/4p, 480M
        |__ Port 2: Dev 3, If 0, Class=Mass Storage, Driver=usb-storage, [COLOR=#b22222]**480M**[/COLOR]

```


[COLOR=#555555][FONT=Roboto]Configuration[/FONT][/COLOR]
[COLOR=#555555][FONT=Roboto]RPi4 B running 64bit Ubuntu hirsute[/FONT][/COLOR]
[COLOR=#555555][FONT=Roboto]USB drive is a Sabrent NVMe M.2 enclosure (Model EC-SNVE) with a Samsung SSD980 NVME 1Tb[/FONT][/COLOR]
[COLOR=#555555][FONT=Roboto]The drive is formatted to ext4 and mounted under /mnt/data[/FONT][/COLOR]
[COLOR=#555555][FONT=Roboto]A docker stack runs nextcloud[/FONT][/COLOR]

[COLOR=#555555][FONT=Roboto]Error Message[/FONT][/COLOR][COLOR=#555555][FONT=Roboto]
```
pi@pi4:~/docker$ sudo dmesg |grep 1-1.4
[    3.372900] usb 1-1.4: new high-speed USB device number 3 using xhci_hcd
[    3.479950] usb 1-1.4: New USB device found, idVendor=0bda, idProduct=9210, bcdDevice=20.01
[    3.479970] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.479978] usb 1-1.4: Product: Sabrent
[    3.479983] usb 1-1.4: Manufacturer: Sabrent
[    3.479989] usb 1-1.4: SerialNumber: 631345678940
[    3.946596] usb-storage 1-1.4:1.0: USB Mass Storage device detected
[    3.946996] scsi host0: usb-storage 1-1.4:1.0
[ 2589.772357] usb 1-1.4: reset high-speed USB device number 3 using xhci_hcd
[ 2591.444993] usb 1-1.4: Device not responding to setup address.
[ 2593.324553] usb 1-1.4: Device not responding to setup address.
[ 2593.532006] usb 1-1.4: device not accepting address 3, error -71
[ 2593.616002] usb 1-1.4: reset high-speed USB device number 3 using xhci_hcd
[ 2595.288634] usb 1-1.4: Device not responding to setup address.
[ 2597.168578] usb 1-1.4: Device not responding to setup address.
[ 2597.376168] usb 1-1.4: device not accepting address 3, error -71
```[/FONT][/COLOR]
[COLOR=#555555][FONT=Roboto]Things I tried[/FONT][/COLOR]

```
ubuntu@pi4:~$ sudo hdparm -I /dev/sdb


/dev/sdb:


ATA device, with non-removable media
        Model Number:       Samsung SSD 980 1TB
        Serial Number:      S64ANG0R528152M
        Firmware Revision:  1B4QFXO7
Standards:
        Likely used: 1
Configuration:
        soft sectored
        head switch time > 15us
        fixed drive
        disk xfer rate <= 5Mbs
        disk xfer rate > 5Mbs, <= 10Mbs
        data strobe offset option
        format speed tolerance gap reqd
        Logical         max     current
        cylinders       17218   0
        heads           8       0
        sectors/track   128     0
        --
        bytes/track: 512        bytes/sector: 0
        Logical/Physical Sector size:           512 bytes
        device size with M = 1024*1024:        8609 MBytes
        device size with M = 1000*1000:        9027 MBytes (9 GB)
        cache/buffer size  = unknown
Capabilities:
        IORDY not likely
        Cannot perform double-word IO
        R/W multiple sector transfer: not supported
        DMA: not supported
        PIO: pio0

```



[COLOR=#555555][FONT=Roboto]I tried combinations found via google search - autosuspend , use_both_schemes to no avail[/FONT][/COLOR][COLOR=#555555][FONT=Roboto]
 ```
echo Y >  /sys/module/usbcore/parameters/use_both_schemes
 echo 'on' > /sys/bus/usb/devices/1-1.4/power/control
 echo -1> /sys/module/usbcore/parameters/autosuspend

```[/FONT][/COLOR]
[COLOR=#555555][FONT=Roboto]Modprobe does not help either[/FONT][/COLOR][COLOR=#555555][FONT=Roboto]
```
modprobe usbcore autosuspend=-1
[/FONT][/COLOR]
```
[COLOR=#555555][FONT=Roboto]I tried the fixes in the following suggestions, none worked so far[/FONT][/COLOR]

[https://unix.stackexchange.com/question ... 0-or-above]("https://unix.stackexchange.com/questions/91027/how-to-disable-usb-autosuspend-on-kernel-3-7-10-or-above")
[https://urukrama.wordpress.com/2009/01/ ... -error-71/]("https://urukrama.wordpress.com/2009/01/27/usb-drive-not-recognised-error-71/")
[https://askubuntu.com/questions/1103658 ... esnt-exist]("https://askubuntu.com/questions/1103658/usb-3-4-device-descriptor-read-64-error-71-but-the-device-doesnt-exist")
[https://www.linuxquestions.org/question ... 175640937/]("https://www.linuxquestions.org/questions/linux-hardware-18/usb-5-1-device-descriptor-read-64-error-71-a-4175640937/")
[https://raspberrypi.stackexchange.com/q ... usb-device]("https://raspberrypi.stackexchange.com/questions/49856/unable-to-enumerate-usb-device")
[https://askubuntu.com/questions/992049/ ... fault-grub]("https://askubuntu.com/questions/992049/how-do-i-add-multiple-values-to-grub-cmdline-default-in-etc-default-grub")
[https://www.suse.com/support/kb/doc/?id=000016942](https://www.suse.com/support/kb/doc/?id=000016942)

---

