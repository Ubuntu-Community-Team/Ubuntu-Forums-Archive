---
title: "invalid access to FAT after dd .img file to usb"
date: 2019-03-24
forum: Hardware
---

### Post by rodrigs on 2019-03-24
Hi.
I am trying to update the bios of a Thinkpad t400 through creating a usb with an image file of the Lenovo driver using geteltorito. No idea if this info is relevant but maybe someone will recognise it; all new to me. I thought I had a damaged usb but I am finding out that errors are resulting with another usb also. Following this tutorial, [https://www.youtube.com/watch?v=2CGrawsd_TA](https://www.youtube.com/watch?v=2CGrawsd_TA) ,
after using ```
sudo dd if=x230.img of=/dev/sdb bs=64k

``` I get ```
512+0 records in512+0 records out
33554432 bytes (34 MB, 32 MiB) copied, 3,5722 s, 9,4 MB/s
nomada@nomada-ThinkPad-T400:/$ 

```
I then ```
sudo mount /dev/sdb /media/nomada
```and get ```
mount: /media/nomada: /dev/sdb already mounted or mount point busy.
```
So I entered thre directory ```
cd /media/nomada/
```
and did a listing ```
ls
``` and got empty
```
nomada@nomada-ThinkPad-T400:/media/nomada$ 
```
contrarily to the tutorial, at 2min58s of the video.

In thunar I see 2 usb drives with the same name as if it is doubled, and whe I try to eject them they give error; one says "Error unmounting /dev/sdb1: no mount point specified" and the other says "umount: /media/nomada/CAT: No such file or directory". And both seem empty.

When I do a ```
dmesg
``` I get a huge list of invalid access to FAT which ends with ```
[70614.301320] FAT-fs (sdb): error, invalid access to FAT (entry 0x6a886b29)
[70614.301504] FAT-fs (sdb): error, invalid access to FAT (entry 0x96f01925)
[71415.450725] usb 2-1: USB disconnect, device number 3
[71422.736034] usb 2-2: new high-speed USB device number 4 using ehci-pci
[71422.893093] usb 2-2: New USB device found, idVendor=048d, idProduct=1234
[71422.893101] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[71422.893106] usb 2-2: Product: UDisk           
[71422.893111] usb 2-2: Manufacturer: General 
[71422.893116] usb 2-2: SerialNumber: &#1033;
[71422.893693] usb-storage 2-2:1.0: USB Mass Storage device detected
[71422.896768] scsi host4: usb-storage 2-2:1.0
[71423.905071] scsi 4:0:0:0: Direct-Access     General  UDisk            5.00 PQ: 0 ANSI: 2
[71423.906037] sd 4:0:0:0: Attached scsi generic sg2 type 0
[71423.910076] sd 4:0:0:0: [sdb] 15728640 512-byte logical blocks: (8.05 GB/7.50 GiB)
[71423.911249] sd 4:0:0:0: [sdb] Write Protect is off
[71423.911253] sd 4:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[71423.911821] sd 4:0:0:0: [sdb] No Caching mode page found
[71423.911828] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[71423.919151]  sdb: sdb1
[71423.921946] sd 4:0:0:0: [sdb] Attached SCSI removable disk



```

Can anyone help me understand what is going on and how can I go around this errors?

When I try to 'sudo umount /media/usb' I get 'umount: /media/usb: no mount point specified.'

---

### Post by yancek on 2019-03-24
I would shut down the system, remove the flash drive, reboot the system and navigate to either the /media or /media/user (use your actual user name here), plug in the flash drive and see if you get a new entry by UUID or Label if you have one.  If the flash drive formatted FAT32?  or do you know?  

> mount: /media/nomada: /dev/sdb already mounted or mount point busy.

You may be showing the directory as empty because it is mounted elsewhere.

---

