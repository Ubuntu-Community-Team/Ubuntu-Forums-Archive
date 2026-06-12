---
title: "Embedded Micro SD Card Reader not working on Ubuntu 16.04"
date: 2017-10-28
forum: Hardware
---

### Post by funicorn on 2017-10-28
[SIZE=2]I have a HP Envy 13 notepad running Ubuntu 16.04 which has a micro SD card reader (slot) . However the system seems to have no awareness of its exsistence.  

In fact there is no response at all when I insert or remove a micro SD Card of both a 16GB FAT-formatted one and a 128GB EXFAT-formatted one. 

I checked all the devices in /dev and found no sign of the SD reader, and  there is no device prefixed by 'sd' or 'mmc', etc. In terms of PCI assignment,[/SIZE]
```
$ lspci
```
It seems that the SD CARD Reader is recognized as the 'Alcor Micro Device 6625', as listed in following outputs (the bold line).
> 00:00.0 Host bridge: Intel Corporation Device 5914 (rev 08)
00:02.0 VGA compatible controller: Intel Corporation Device 5917 (rev 07)
00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 08)
00:08.0 System peripheral: Intel Corporation Sky Lake Gaussian Mixture Model
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller (rev 21)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
00:1d.0 PCI bridge: Intel Corporation Device 9d18 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Device 9d4e (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
**01:00.0 Unassigned class [ff00]: Alcor Micro Device 6625**
02:00.0 Network controller: Intel Corporation Wireless 7265 (rev 59)
03:00.0 Non-Volatile memory controller: Intel Corporation Device f1a5 (rev 03)
[SIZE=2]What I have also tried is to monitor the udev and kernel action when inserting and removing a SD CARD, although nothing is recorded except some 'thermal' activity.

So what should I do now to make the card reader work? Or what else can I do to further identify where the problem is?[/SIZE]

---

### Post by sudodus on 2017-10-28
Have you tried to 'see' the micro SD card via a USB adapter? That might be a first step: When you know that it can be seen that way, you know that Ubuntu in your computer can see it.

[hr][/hr]
There might be some particular problem, that disturbs the communication between the computer and the card. You can get useful tips from the following link,

[Can't format my usb drive. I have already tried with mkdosfs and gparted - Analysis of the problem](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

Let us hope that there is 'only confusion' :-)

---

### Post by funicorn on 2017-10-28
Yes. I forgot to mention that I have tried putting the 1GB or 256GB micro SD Card in a USB adapter. they both work normally on Ubuntu 16.04. 

I went through some posts discussing similar issues regarding the embedded sd card reader, and noted the particular case that the sd card has certain 'abnormal' partition structure. 

In my case, the 16GB sd card is formatted in FAT with a Live Ubuntu 16.04 on it. The 256GB one is formatted in EXFAT with plain files. 

The Ubuntu Live cd surely wrote some booting segment (UEFI Info) to the head of the 16GB disk, while the 256GB disk has merely a partition for storage.

The 16GB disk info via a USB adapter:
> /dev/sda1: UUID="2017-08-01-11-51-33-00" LABEL="Ubuntu 16.04.3 LTS amd64" TYPE="iso9660" PTUUID="0d66cd15" PTTYPE="dos" PARTUUID="0d66cd15-01"
/dev/sda2: SEC_TYPE="msdos" UUID="398E-230F" TYPE="vfat" PARTUUID="0d66cd15-02"
The 256GB disk info:
> /dev/sda1: UUID="F4E4-D8FD" TYPE="exfat" PARTUUID="3f116c89-01"

More info about the unassigned sd card reader:
> 01:00.0 Unassigned class [ff00]: Alcor Micro Device 6625
    Subsystem: Hewlett-Packard Company Device 83a8
    Flags: fast devsel, IRQ 255
    Memory at a1200000 (64-bit, non-prefetchable) [disabled] [size=4K]
    Capabilities: <access denied>

> **sudodus said:**
> Have you tried to 'see' the micro SD card via a USB adapter? That might be a first step: When you know that it can be seen that way, you know that Ubuntu in your computer can see it.

[HR][/HR]
There might be some particular problem, that disturbs the communication between the computer and the card. You can get useful tips from the following link,

[Can't format my usb drive. I have already tried with mkdosfs and gparted - Analysis of the problem]("https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035")

Let us hope that there is 'only confusion' :-)

---

### Post by funicorn on 2017-10-28
The dmesg message:

> [68387.524564] usb-storage 1-1:1.0: USB Mass Storage device detected
[68387.525556] scsi host2: usb-storage 1-1:1.0
[68388.543761] scsi 2:0:0:0: Direct-Access     Mass     Storage Device   1.00 PQ: 0 ANSI: 0 CCS
[68388.544988] sd 2:0:0:0: Attached scsi generic sg0 type 0
[68388.991821] sd 2:0:0:0: [sda] 245415936 512-byte logical blocks: (126 GB/117 GiB)
[68388.992154] sd 2:0:0:0: [sda] Write Protect is off
[68388.992158] sd 2:0:0:0: [sda] Mode Sense: 03 00 00 00
[68388.992423] sd 2:0:0:0: [sda] No Caching mode page found
[68388.992431] sd 2:0:0:0: [sda] Assuming drive cache: write through
[68388.994675]  sda: sda1
[68388.995883] sd 2:0:0:0: [sda] Attached SCSI removable disk
[68408.122297] sd 2:0:0:0: [sda] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[68408.122299] sd 2:0:0:0: [sda] tag#0 Sense Key : Not Ready [current] 
[68408.122301] sd 2:0:0:0: [sda] tag#0 Add. Sense: Medium not present
[68408.122304] sd 2:0:0:0: [sda] tag#0 CDB: Read(10) 28 00 00 00 08 80 00 00 90 00
[68408.122305] blk_update_request: I/O error, dev sda, sector 2176
[68408.122627] sd 2:0:0:0: [sda] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[68408.122629] sd 2:0:0:0: [sda] tag#0 Sense Key : Not Ready [current] 
[68408.122632] sd 2:0:0:0: [sda] tag#0 Add. Sense: Medium not present
[68408.122633] sd 2:0:0:0: [sda] tag#0 CDB: Read(10) 28 00 00 00 08 40 00 00 38 00
[68408.122635] blk_update_request: I/O error, dev sda, sector 2112
[68408.123001] sd 2:0:0:0: [sda] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[68408.123002] sd 2:0:0:0: [sda] tag#0 Sense Key : Not Ready [current] 
[68408.123004] sd 2:0:0:0: [sda] tag#0 Add. Sense: Medium not present
[68408.123005] sd 2:0:0:0: [sda] tag#0 CDB: Read(10) 28 00 00 00 08 20 00 00 18 00
[68408.123006] blk_update_request: I/O error, dev sda, sector 2080
[68408.123335] sd 2:0:0:0: [sda] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[68408.123337] sd 2:0:0:0: [sda] tag#0 Sense Key : Not Ready [current] 
[68408.123338] sd 2:0:0:0: [sda] tag#0 Add. Sense: Medium not present
[68408.123339] sd 2:0:0:0: [sda] tag#0 CDB: Read(10) 28 00 00 00 08 10 00 00 08 00
[68408.123340] blk_update_request: I/O error, dev sda, sector 2064
[68408.123663] sd 2:0:0:0: [sda] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[68408.123664] sd 2:0:0:0: [sda] tag#0 Sense Key : Not Ready [current] 
[68408.123665] sd 2:0:0:0: [sda] tag#0 Add. Sense: Medium not present
[68408.123666] sd 2:0:0:0: [sda] tag#0 CDB: Read(10) 28 00 00 00 08 10 00 00 08 00
[68408.123667] blk_update_request: I/O error, dev sda, sector 2064
[68408.123669] Buffer I/O error on dev sda1, logical block 2, async page read
[68408.123994] sd 2:0:0:0: [sda] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[68408.123995] sd 2:0:0:0: [sda] tag#0 Sense Key : Not Ready [current] 
[68408.123996] sd 2:0:0:0: [sda] tag#0 Add. Sense: Medium not present
[68408.123997] sd 2:0:0:0: [sda] tag#0 CDB: Read(10) 28 00 00 00 08 10 00 00 08 00
[68408.123998] blk_update_request: I/O error, dev sda, sector 2064
[68408.124000] Buffer I/O error on dev sda1, logical block 2, async page read
[68409.013965] usb 1-1: USB disconnect, device number 10


---

### Post by sudodus on 2017-10-28
I am glad, that you can connect to the micro SD cards via a USB adapter :-)

So the problem is that

- either there is something wrong with the built in card reader (it is damaged) or the electric connection to it is damaged,

- or the built in card reader cannot cooperate with Ubuntu (there is no suitable driver in Ubuntu 16.04 LTS). If this is the case it might work better in another version of Ubuntu which has another version of the linux kernel, which has other versions of hardware drivers. So it is worthwhile trying with Ubuntu 17.04 and Ubuntu 17.10. Try them live (without installing). You might even try the older 14.04 LTS version of Ubuntu but it is less likely to work.

---

### Post by funicorn on 2017-10-29
I can be sure the built-in reader itself works fine, which I checked on Windows 10. Thus it should be related to the hardware driver or the kernel modules. There are few such issues reported due to certain built-in multimedia readers, but none of them have been resolved in the later official release.  I'll keep searching for possible solutions. Thank you for the kind advice.

> **sudodus said:**
> I am glad, that you can connect to the micro SD cards via a USB adapter :-)

So the problem is that

- either there is something wrong with the built in card reader (it is damaged) or the electric connection to it is damaged,

- or the built in card reader cannot cooperate with Ubuntu (there is no suitable driver in Ubuntu 16.04 LTS). If this is the case it might work better in another version of Ubuntu which has another version of the linux kernel, which has other versions of hardware drivers. So it is worthwhile trying with Ubuntu 17.04 and Ubuntu 17.10. Try them live (without installing). You might even try the older 14.04 LTS version of Ubuntu but it is less likely to work.

---

### Post by Ng Oon-Ee on 2017-11-05
I can confirm on Arch Linux that even the latest stable kernel would not help. Looks like there's neither no such kernel module [https://wikidevi.com/wiki/Alcor_Micro_AU6601](https://wikidevi.com/wiki/Alcor_Micro_AU6601) (although mine reports as 6625) or it's not compiled in. Regardless, I don't care enough about it to recompile my kernel.

---

### Post by efflandt on 2017-11-07
Card readers in laptops or notebooks are either PCI in which case they would be listed in lspci and would typically be an mmcblk device, or internally USB connected in which case they or would be listed in lsusb (not lspci). And it is odd that dmesg does not show its USB ID (idVendor and idProduct). So we cannot tell what type of USB card reader that built-in slot is from the information provided.

This may be a different device than yours, but is related dmesg output and corresponding line of lsusb after inserting 16GB SD card that contains an installed version of Ubuntu 16.04 (BIOS boot, no swap) into the apparently internally USB connected slot of an HP laptop:```
[  278.367039] usb 1-4: new high-speed USB device number 6 using xhci_hcd
[  278.564183] usb 1-4: New USB device found, idVendor=0bda, idProduct=0177
[  278.564198] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  278.564206] usb 1-4: Product: USB2.0-CRW
[  278.564215] usb 1-4: Manufacturer: Generic
[  278.564222] usb 1-4: SerialNumber: 20121112761000000
[  278.941308] usb-storage 1-4:1.0: USB Mass Storage device detected
[  278.941592] scsi host2: usb-storage 1-4:1.0
[  278.941914] usbcore: registered new interface driver usb-storage
[  278.961745] usbcore: registered new interface driver uas
[  279.962876] scsi 2:0:0:0: Direct-Access     Generic- SD/MMC/MS PRO    1.00 PQ: 0 ANSI: 4
[  279.964831] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  280.687457] sd 2:0:0:0: [sdb] 31537152 512-byte logical blocks: (16.1 GB/15.0 GiB)
[  280.688373] sd 2:0:0:0: [sdb] Write Protect is off
[  280.688386] sd 2:0:0:0: [sdb] Mode Sense: 2f 00 00 00
[  280.689044] sd 2:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  280.774089]  sdb: sdb1
[  280.788119] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[  281.673182] EXT4-fs (sdb1): mounting ext2 file system using the ext4 subsystem
[  281.712118] EXT4-fs (sdb1): mounted filesystem without journal. Opts: (null)

~$ lsusb | grep 0177
Bus 001 Device 006: ID 0bda:0177 Realtek Semiconductor Corp.
```So do you have an example of the beginning of the dmesg output that identifies the USB ID and how that is listed in lsusb?

---

### Post by Ng Oon-Ee on 2017-12-28
> **efflandt said:**
> Card readers in laptops or notebooks are either PCI in which case they would be listed in lspci and would typically be an mmcblk device, or internally USB connected in which case they or would be listed in lsusb (not lspci). And it is odd that dmesg does not show its USB ID (idVendor and idProduct). So we cannot tell what type of USB card reader that built-in slot is from the information provided

This laptop's card (I have the same laptop) is PCI. Driver doesn't exist as far as I can tell. Here's the bug OP submitted [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1730152/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1730152/)

---

