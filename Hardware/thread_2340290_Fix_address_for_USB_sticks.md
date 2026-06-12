---
title: "Fix address for USB sticks"
date: 2016-10-17
forum: Hardware
---

### Post by brononi on 2016-10-17
Hello,

I'm having 2 identical USB Gen 5 sticks (gateways for zwave). My server is running under VMWare Esxi.
In cli, I see the USB-stikcs nicely detected. 
```
lsusb
Bus 002 Device 005: ID 0658:0200 Sigma Designs, Inc. 
Bus 002 Device 004: ID 0658:0200 Sigma Designs, Inc.

ll /dev/ttyACM*
crw-rw---- 1 root dialout 166, 0 okt 17 13:17 /dev/ttyACM0
crw-rw---- 1 root dialout 166, 1 okt 17 13:17 /dev/ttyACM1
```

But when I now disconnected a stick and reconnect it, it's getting fe ACM3 as address.
The software I'm using (OpenHAB) doesn't like it when the address change.
Even more, it doesn't like when the sticks are being swapped (if 1 becomes 0 and 0 becomes 1).


I was looking around to create a symbolic link to fe /dev/ttyZWAVE1 and /dev/ttyZWAVE2. But I can't figure out how I can fix the sticks per address. I ended up with this:
```
/etc/udev/rules.d/50-usb-serial.rules
SUBSYSTEM=="tty", ATTRS{idVendor}=="_**0658**_", ATTRS{idProduct}=="_**0200**_", SYMLINK+="USBzwave1", GROUP="dialout", MODE="0666"
SUBSYSTEM=="tty", ATTRS{idVendor}=="_**0658**_", ATTRS{idProduct}=="**_0200_**", SYMLINK+="USBzwave2", GROUP="dialout", MODE="0666"
```

Somewhere I've read that you could use the serial, but I **_can't find the serials_** for these sticks. Not sure if this could be the solution, but the result could be then something like:
```
/etc/udev/rules.d/50-usb-serial.rules
SUBSYSTEM=="tty", ATTRS{idVendor}=="_**0658**_", ATTRS{idProduct}=="_**0200**_", ATTRS{serial}=="_**XXXXX**_", SYMLINK+="USBzwave1", GROUP="dialout", MODE="0666"
SUBSYSTEM=="tty", ATTRS{idVendor}=="_**0658**_", ATTRS{idProduct}=="**_0200_**", ATTRS{serial}=="**_YYYYY_**", SYMLINK+="USBzwave2", GROUP="dialout", MODE="0666"
```


Some additional info so far:

```
udevadm info -a -p $(udevadm info -q path -n /dev/_**ttyACM0**_)
<knip>
  looking at parent device '/devices/pci0000:00/0000:00:11.0/0000:02:02.0/usb2/2-2/2-2.1':
    KERNELS=="2-2.1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{authorized}=="1"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bDeviceClass}=="02"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{bMaxPower}=="100mA"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bNumInterfaces}==" 2"
    ATTRS{bcdDevice}=="0000"
    ATTRS{bmAttributes}=="80"
    ATTRS{busnum}=="_**2**_"
    ATTRS{configuration}==""
    ATTRS{devnum}=="_**4**_"
    ATTRS{devpath}=="2.1"
    ATTRS{idProduct}=="**_0200_**"
    ATTRS{idVendor}=="**_0658_**"
    ATTRS{ltm_capable}=="no"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{removable}=="unknown"
    ATTRS{speed}=="12"
    ATTRS{urbnum}=="3581"
    ATTRS{version}==" 2.00"
```


```
 udevadm info -a -p $(udevadm info -q path -n /dev/_**ttyACM0**_)
<knip>
  looking at parent device '/devices/pci0000:00/0000:00:11.0/0000:02:02.0/usb2/2-2/2-2.2':
    KERNELS=="2-2.2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{authorized}=="1"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bDeviceClass}=="02"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{bMaxPower}=="100mA"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bNumInterfaces}==" 2"
    ATTRS{bcdDevice}=="0000"
    ATTRS{bmAttributes}=="80"
    ATTRS{busnum}=="_**2**_"
    ATTRS{configuration}==""
    ATTRS{devnum}=="_**5**_"
    ATTRS{devpath}=="2.2"
    ATTRS{idProduct}=="_**0200**_"
    ATTRS{idVendor}=="_**0658**_"
    ATTRS{ltm_capable}=="no"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{removable}=="unknown"
    ATTRS{speed}=="12"
    ATTRS{urbnum}=="9256"
    ATTRS{version}==" 2.00"
```


Any idea how I can solve this?

---

### Post by ajgreeny on 2016-10-17
If you label the partition on each stick using, for example, gparted in Ubuntu, or if cli with commands:-
> for FAT32:
sudo mlabel -i /dev/sdxN ::"my_label"
or
sudo fatlabel /dev/sdxN my_label

for NTFS:
sudo ntfslabel /dev/sdxN my_label

for exFAT:
sudo exfatlabel /dev/sdxN my_label

for ext2/3/4:
sudo e2label /dev/sdxN my_label
each stick will then mount using that label as its mountpoint, normally as /media/<*username*>/label.

Sorry if that is not what you mean by each stick's address, but if this doesn't help you come back again and ask as it may be possible to use the UUIDs of the partitions.

---

### Post by brononi on 2016-10-18
Hey, thanks for you feedback. But sadly, these aren't USB memory sticks, but USB Dongles (gateway for zwave networks). 
So I can't format these in any way. I also don't see them.

[HTML]lsblk
NAME                    MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
fd0                       2:0    1    4K  0 disk 
sda                       8:0    0   16G  0 disk 
|-sda1                    8:1    0  487M  0 part /boot
|-sda2                    8:2    0    1K  0 part 
`-sda5                    8:5    0 15.5G  0 part 
  |-habirus2--vg-root   252:0    0 14.5G  0 lvm  /
  `-habirus2--vg-swap_1 252:1    0    1G  0 lvm  [SWAP]
sr0                      11:0    1 1024M  0 rom  [/HTML]

---

### Post by sudodus on 2016-10-18
These are special equipment. I think you should ask the vendor or manufacturer how to manage them, when using more than one in the same computer.

---

