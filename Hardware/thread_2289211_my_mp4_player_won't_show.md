---
title: "my mp4 player won't show"
date: 2015-08-02
forum: Hardware
---

### Post by medyas on 2015-08-02
hello guys, so i'm trying to put some songs in my old mp4 player but ubuntu won't display it (it didn't mount it ) ,so i tried to search for a solution online but with no luck :

i tried the **lsusb** and it showed it :[B] Bus 002 Device 026: ID 10d6:ff61 Actions Semiconductor Co., Ltd MP4 Player

[/B]but the **lsblk** didn't :

 NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 698.7G  0 disk 
&#9500;&#9472;sda1   8:1    0  80.6G  0 part 
&#9500;&#9472;sda2   8:2    0 269.9G  0 part /
&#9500;&#9472;sda3   8:3    0   1.1G  0 part [SWAP]
&#9492;&#9472;sda5   8:5    0 347.1G  0 part /media/yassine/01CF96B8807C6AA0
sr0     11:0    1  1024M  0 rom  


i got ubuntu 15.04   and 3.19.0-25-generic, so please any help and thank you

---

### Post by Yellow Pasque on 2015-08-02
Can you mount it manually?

Does dmesg show anything when you plug the player in?
```
dmesg | tail -n 20
```

---

### Post by medyas on 2015-08-03
it didn't work , here's the result : 

dmesg | tail -n 20
[ 5706.642914] usb 2-1.3: new high-speed USB device number 5 using ehci-pci
[ 5706.999295] usb 2-1.3: new high-speed USB device number 6 using ehci-pci
[ 5707.279468] usb 2-1.3: new high-speed USB device number 7 using ehci-pci
[ 5707.767538] usb 2-1.3: device not accepting address 7, error -71
[ 5707.983907] usb 2-1.3: new high-speed USB device number 9 using ehci-pci
[ 5708.076412] usb 2-1.3: New USB device found, idVendor=10d6, idProduct=ff61
[ 5708.076421] usb 2-1.3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[ 5714.815200] usb 2-1.3: USB disconnect, device number 9
[ 5715.016093] usb 2-1.3: new high-speed USB device number 10 using ehci-pci
[ 5716.092750] usb 2-1.3: new high-speed USB device number 11 using ehci-pci
[ 5716.185464] usb 2-1.3: New USB device found, idVendor=10d6, idProduct=ff61
[ 5716.185472] usb 2-1.3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[ 5769.889168] usb 2-1.3: USB disconnect, device number 11
[ 5770.090034] usb 2-1.3: new high-speed USB device number 12 using ehci-pci
[ 5770.182578] usb 2-1.3: New USB device found, idVendor=10d6, idProduct=ff61
[ 5770.182587] usb 2-1.3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[ 5802.165223] usb 2-1.3: USB disconnect, device number 12
[ 5802.366172] usb 2-1.3: new high-speed USB device number 13 using ehci-pci
[ 5802.458889] usb 2-1.3: New USB device found, idVendor=10d6, idProduct=ff61
[ 5802.458899] usb 2-1.3: New USB device strings: Mfr=0, Product=0, SerialNumber=0

---

### Post by Yellow Pasque on 2015-08-03
Did you try mounting it?
Show output of:
```
sudo fdisk -l
```

---

### Post by medyas on 2015-08-04
this what is gave me : 

Disk /dev/sda: 698.7 GiB, 750156374016 bytes, 1465149168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xd2137754

Device     Boot     Start        End   Sectors   Size Id Type
/dev/sda1  *         2048  169043967 169041920  80.6G 83 Linux
/dev/sda2       169043968  734963711 565919744 269.9G 83 Linux
/dev/sda3       734963712  737286143   2322432   1.1G 82 Linux swap / Solaris
/dev/sda4       737287171 1465144064 727856894 347.1G  f W95 Ext'd (LBA)
/dev/sda5       737287173 1465144064 727856892 347.1G  7 HPFS/NTFS/exFAT

Partition 5 does not start on physical sector boundary.

Partition 6 does not start on physical sector boundary.

and nothing happened.

---

