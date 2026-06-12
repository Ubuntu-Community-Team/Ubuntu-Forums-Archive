---
title: "Really Weird, and i need to Solve.  no CDrom or USB"
date: 2008-02-22
forum: Hardware &amp; Laptops
---

### Post by btole79 on 2008-02-22
This is so strange.  i installed a fresh copy of 7.10 and everything works great.  then i went to burn a CD yesterday and nothing shows up.  i have tried multiple CDs and still nothing.  i know the CDrom works becuase i used it to load the system. :confused: GREAT, just Perfect.  so i thought i would just transfer the files to my thumb drive and go to another computer and guess what, nothing happens when i plug in the thumb drive.:mad:

so now i have this awsome machine and the only way to get anything off of it is to email it to myself or to send it across my network to another machine.

can you please help me:KS

thanks
bt

---

### Post by xeth_delta on 2008-02-22
That is strange. Please try the following:
Place the CD in the drive, then:
```
sudo mkdir /mnt/cdrom
sudo mount /dev/cdrom /mnt/cdrom
```
Also, connect the USB drive to the computer and run:
```
lsusb
dmesg
```
What is the output?

---

### Post by btole79 on 2008-02-22
this is what happens wh i try the commands for the CDRom.  

bt@bt-desktop:~$ sudo mkdir /mnt/cdrom
mkdir: cannot create directory `/mnt/cdrom': File exists
bt@bt-desktop:~$ sudo mount /dev/cdrom /mnt/cdrom
mount: No medium found


the weird thing is under /media i show cdrom0 and cdrom1 

also the usb commands come back with this

bt@bt-desktop:~$ lsusb
Bus 007 Device 004: ID 0781:5406 SanDisk Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 005: ID 045e:009d Microsoft Corp. 
Bus 004 Device 004: ID 0557:7000 ATEN International Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 03f0:0211 Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  

the san disk is my external USB

and the other command came back with so much i could only get part of it

[171948.753818] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[172034.039737] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[172034.039743] ata3.00: (BMDMA stat 0x26)
[172034.039750] ata3.00: cmd 35/00:70:bf:a2:ce/00:03:00:00:00/e0 tag 0 cdb 0x0 data 450560 out
[172034.039752]          res 51/84:70:bf:a2:ce/84:03:00:00:00/e0 Emask 0x30 (host bus error)
[172034.039760] ata3: soft resetting port
[172034.220769] ata3.00: configured for UDMA/133
[172034.220783] ata3: EH complete
[172034.231277] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[172034.231668] sd 2:0:0:0: [sda] Write Protect is off
[172034.231672] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[172034.231815] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[172073.312049] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[172197.870884] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[172322.959846] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[172447.798160] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[172572.355930] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[172696.916003] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[172821.475175] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[172945.811511] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[173070.447822] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[173195.008691] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[173317.966052] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[173440.928587] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[173565.487175] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[173690.045835] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[173814.602008] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[173939.160178] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[174063.717007] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[174186.677667] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[174309.634954] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[174432.590543] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[174557.148141] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[174615.712892] end_request: I/O error, dev fd0, sector 0
[174627.871333] end_request: I/O error, dev fd0, sector 0
[174627.871341] Buffer I/O error on device fd0, logical block 0
[174640.042095] end_request: I/O error, dev fd0, sector 0
[174640.042103] Buffer I/O error on device fd0, logical block 0
[174652.200609] end_request: I/O error, dev fd0, sector 0
[174652.200617] Buffer I/O error on device fd0, logical block 0
[174664.358765] end_request: I/O error, dev fd0, sector 0
[174664.358773] Buffer I/O error on device fd0, logical block 0
[174676.509726] end_request: I/O error, dev fd0, sector 0
[174676.509733] Buffer I/O error on device fd0, logical block 0
[174681.359773] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[174688.720324] end_request: I/O error, dev fd0, sector 0
[174688.720331] Buffer I/O error on device fd0, logical block 0
[174700.919358] end_request: I/O error, dev fd0, sector 0
[174700.919366] Buffer I/O error on device fd0, logical block 0
[174713.097953] end_request: I/O error, dev fd0, sector 0
[174713.097961] Buffer I/O error on device fd0, logical block 0
[174725.269028] end_request: I/O error, dev fd0, sector 0
[174725.269036] Buffer I/O error on device fd0, logical block 0
[174737.428547] end_request: I/O error, dev fd0, sector 0
[174737.428555] Buffer I/O error on device fd0, logical block 0
[174749.587014] end_request: I/O error, dev fd0, sector 0
[174749.587021] Buffer I/O error on device fd0, logical block 0
[174761.743138] end_request: I/O error, dev fd0, sector 0
[174761.743146] Buffer I/O error on device fd0, logical block 0
[174773.959846] end_request: I/O error, dev fd0, sector 0
[174773.959854] Buffer I/O error on device fd0, logical block 0
[174786.158866] end_request: I/O error, dev fd0, sector 0
[174786.158873] Buffer I/O error on device fd0, logical block 0
[174798.341223] end_request: I/O error, dev fd0, sector 0
[174798.341230] Buffer I/O error on device fd0, logical block 0
[174805.921756] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[174810.513354] end_request: I/O error, dev fd0, sector 0
[174810.513361] Buffer I/O error on device fd0, logical block 0
[174822.661295] end_request: I/O error, dev fd0, sector 0
[174822.661303] Buffer I/O error on device fd0, logical block 0
[174834.847704] end_request: I/O error, dev fd0, sector 0
[174834.847712] Buffer I/O error on device fd0, logical block 0
[174847.046698] end_request: I/O error, dev fd0, sector 0
[174847.046706] Buffer I/O error on device fd0, logical block 0
[174859.233461] end_request: I/O error, dev fd0, sector 0
[174859.233469] Buffer I/O error on device fd0, logical block 0
[174871.400466] end_request: I/O error, dev fd0, sector 0
[174871.400473] Buffer I/O error on device fd0, logical block 0
[174883.559970] end_request: I/O error, dev fd0, sector 0
[174883.559977] Buffer I/O error on device fd0, logical block 0
[174895.718167] end_request: I/O error, dev fd0, sector 0
[174895.718175] Buffer I/O error on device fd0, logical block 0
[174907.869229] end_request: I/O error, dev fd0, sector 0
[174907.869236] Buffer I/O error on device fd0, logical block 0
[174920.030230] end_request: I/O error, dev fd0, sector 0
[174920.030237] Buffer I/O error on device fd0, logical block 0
[174931.008116] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[174932.186010] end_request: I/O error, dev fd0, sector 0
[174932.186017] Buffer I/O error on device fd0, logical block 0
[174944.359763] end_request: I/O error, dev fd0, sector 0
[174944.359770] Buffer I/O error on device fd0, logical block 0
[174956.616512] end_request: I/O error, dev fd0, sector 0
[174956.616520] Buffer I/O error on device fd0, logical block 0
[174968.807586] end_request: I/O error, dev fd0, sector 0
[174980.999100] end_request: I/O error, dev fd0, sector 0
[174993.177438] end_request: I/O error, dev fd0, sector 0
[174993.177446] Buffer I/O error on device fd0, logical block 0
[175005.344368] end_request: I/O error, dev fd0, sector 0
[175005.344376] Buffer I/O error on device fd0, logical block 0
[175016.576513] usb 7-5: new high speed USB device using ehci_hcd and address 4
[175016.709265] usb 7-5: configuration #1 chosen from 1 choice
[175016.709490] scsi10 : SCSI emulation for USB Mass Storage devices
[175016.709629] usb-storage: device found at 4
[175016.709632] usb-storage: waiting for device to settle before scanning
[175017.503516] end_request: I/O error, dev fd0, sector 0
[175017.503524] Buffer I/O error on device fd0, logical block 0
[175021.700377] usb-storage: device scan complete
[175021.700767] scsi 10:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  3.21 PQ: 0 ANSI: 2
[175021.702016] sd 10:0:0:0: [sdc] 4001425 512-byte hardware sectors (2049 MB)
[175021.702619] sd 10:0:0:0: [sdc] Write Protect is off
[175021.702623] sd 10:0:0:0: [sdc] Mode Sense: 03 00 00 00
[175021.702626] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[175021.704739] sd 10:0:0:0: [sdc] 4001425 512-byte hardware sectors (2049 MB)
[175021.705362] sd 10:0:0:0: [sdc] Write Protect is off
[175021.705366] sd 10:0:0:0: [sdc] Mode Sense: 03 00 00 00
[175021.705370] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[175021.705374]  sdc: sdc1
[175021.709577] sd 10:0:0:0: [sdc] Attached SCSI removable disk
[175021.709628] sd 10:0:0:0: Attached scsi generic sg4 type 0
[175029.691709] end_request: I/O error, dev fd0, sector 0
[175029.691716] Buffer I/O error on device fd0, logical block 0
[175041.870912] end_request: I/O error, dev fd0, sector 0
[175041.870919] Buffer I/O error on device fd0, logical block 0
[175054.035573] end_request: I/O error, dev fd0, sector 0
[175054.035581] Buffer I/O error on device fd0, logical block 0
[175054.318654] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[175066.206381] end_request: I/O error, dev fd0, sector 0
[175066.206388] Buffer I/O error on device fd0, logical block 0
[175078.368499] end_request: I/O error, dev fd0, sector 0
[175078.368506] Buffer I/O error on device fd0, logical block 0
[175090.552750] end_request: I/O error, dev fd0, sector 0
[175090.552756] Buffer I/O error on device fd0, logical block 0
[175102.735558] end_request: I/O error, dev fd0, sector 0
[175102.735572] Buffer I/O error on device fd0, logical block 0
[175114.899980] end_request: I/O error, dev fd0, sector 0
[175114.899987] Buffer I/O error on device fd0, logical block 0
[175127.122178] end_request: I/O error, dev fd0, sector 0
[175127.122185] Buffer I/O error on device fd0, logical block 0
[175139.313846] end_request: I/O error, dev fd0, sector 0
[175139.313853] Buffer I/O error on device fd0, logical block 0
[175151.491033] end_request: I/O error, dev fd0, sector 0
[175151.491039] Buffer I/O error on device fd0, logical block 0
[175163.652962] end_request: I/O error, dev fd0, sector 0
[175163.652970] Buffer I/O error on device fd0, logical block 0
[175175.827480] end_request: I/O error, dev fd0, sector 0
[175175.827486] Buffer I/O error on device fd0, logical block 0
[175177.284383] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[175188.004045] end_request: I/O error, dev fd0, sector 0
[175188.004053] Buffer I/O error on device fd0, logical block 0
[175200.155069] end_request: I/O error, dev fd0, sector 0
[175200.155077] Buffer I/O error on device fd0, logical block 0
[175212.341844] end_request: I/O error, dev fd0, sector 0
[175212.341852] Buffer I/O error on device fd0, logical block 0
[175224.548296] end_request: I/O error, dev fd0, sector 0
[175224.548303] Buffer I/O error on device fd0, logical block 0
[175236.739200] end_request: I/O error, dev fd0, sector 0
[175236.739207] Buffer I/O error on device fd0, logical block 0
[175248.910291] end_request: I/O error, dev fd0, sector 0
[175248.910298] Buffer I/O error on device fd0, logical block 0
[175261.078937] end_request: I/O error, dev fd0, sector 0
[175261.078944] Buffer I/O error on device fd0, logical block 0
[175273.250350] end_request: I/O error, dev fd0, sector 0
[175273.250357] Buffer I/O error on device fd0, logical block 0
[175285.413611] end_request: I/O error, dev fd0, sector 0
[175285.413618] Buffer I/O error on device fd0, logical block 0

---

### Post by xeth_delta on 2008-02-22
From the cd mount command it would seem like the CD is empty.
From lsusb I can see that the system recognizes your USB drive, I think as /dev/sdc, it is not mounting the partition automatically, though. Try mounting it yourself:
```
sudo mkdir /mnt/usbdisk
sudo mount /dev/sdc1 /mnt/usbdisk
```

One more observation. Do you have a floppy disk in the computer? It seems to be giving a lot of errors in dmesg.

---

### Post by btole79 on 2008-02-22
ok i ran the usbdisk commands and it mounted the usb drive.  it doesnt show on the desktop but it is available in the /mnt/usbdisk folder.:)

  should it show on the desktop?

i do not have a floppy drive on the machine at all.  i think alot of the errors are from a buffalo wireless PCI card.

---

### Post by xeth_delta on 2008-02-22
> **btole79 said:**
> ok i ran the usbdisk commands and it mounted the usb drive.  it doesnt show on the desktop but it is available in the /mnt/usbdisk folder.:)

  should it show on the desktop?

i do not have a floppy drive on the machine at all.  i think alot of the errors are from a buffalo wireless PCI card.

Ok, at least the drive can be mounted. Normally it should show do it automatically. Have you perchance disabled any services or daemons? I don't exactly recall the name of the daemon that checkes whether there is new media connected to the computer. Hopefully another user will come with this information, or I will remember it a bit later. In any case, this might be the reason for the problem you have.

Please remember to unmount the drive before removing it.Make sure you are not using the drive with any program and type:
```
sudo umount /dev/sdc1
```

dmesg really seems to indicate some sort of problem with fd0, what this problem is, I am not sure, though. If you don't have any floppy drive, may I suggest disabling the floppy controller from the BIOS?

---

### Post by btole79 on 2008-02-22
ill do that right now and see what happens.  this all seemed to start when i added a second hard drive.  but ill give it a shot.

---

