---
title: "No automount - Hardy Heron"
date: 2008-05-11
forum: Hardware
---

### Post by oyankee on 2008-05-11
Hello,
I can't get working automount on my laptop. I installed Hardy Heron candidate and now I have all upgrades. 
When I plug any mp3 player or camera with or without memory stick, no media will appear.
For example I see 
> lsusb
Bus 001 Device 003: ID 054c:0325 Sony Corp.
Bus 001 Device 001: ID 0000:0000  
I can mount it manualy-this is not the problem. 
Some usb disks will mount automaticly but any of walkmans I've tried won't do that.
Anyone knows solution, please?

Am I only one who has this problem?

---

### Post by oyankee on 2008-05-11
This is my dmesg
> [ 5523.666728] usb-storage: device found at 6
[ 5523.666739] usb-storage: waiting for device to settle before scanning
[ 5528.662831] usb-storage: device scan complete
[ 5528.669820] scsi 4:0:0:0: Direct-Access     SONY     WALKMAN          1.00 PQ: 0 ANSI: 0 CCS
[ 5529.728554] ready
[ 5529.735567] sd 4:0:0:0: [sda] 1875968 2048-byte hardware sectors (3842 MB)
[ 5529.853439] sd 4:0:0:0: [sda] Write Protect is off
[ 5529.853456] sd 4:0:0:0: [sda] Mode Sense: 00 2a 00 00
[ 5529.853462] sd 4:0:0:0: [sda] Assuming drive cache: write through
[ 5529.872418] sd 4:0:0:0: [sda] 1875968 2048-byte hardware sectors (3842 MB)
[ 5529.983290] sd 4:0:0:0: [sda] Write Protect is off
[ 5529.983306] sd 4:0:0:0: [sda] Mode Sense: 00 2a 00 00
[ 5529.983312] sd 4:0:0:0: [sda] Assuming drive cache: write through
[ 5529.983327]  sda: sda1
[ 5529.993322]  sda: p1 exceeds device capacity
[ 5529.997348] sd 4:0:0:0: [sda] Attached SCSI removable disk
[ 5529.997446] sd 4:0:0:0: Attached scsi generic sg0 type 0
[ 5530.745565] attempt to access beyond end of device
[ 5530.745586] sda: rw=0, want=4294967044, limit=7503872
[ 5530.745592] printk: 53 messages suppressed.
[ 5530.745597] Buffer I/O error on device sda1, logical block 1073741760
[ 5530.745605] attempt to access beyond end of device
[ 5530.745610] sda: rw=0, want=4294967048, limit=7503872
[ 5530.745614] Buffer I/O error on device sda1, logical block 1073741761
[ 5530.745620] attempt to access beyond end of device
[ 5530.745624] sda: rw=0, want=4294967044, limit=7503872
[ 5530.745629] Buffer I/O error on device sda1, logical block 1073741760
[ 5530.745633] attempt to access beyond end of device
[ 5530.745638] sda: rw=0, want=4294967048, limit=7503872
[ 5530.745642] Buffer I/O error on device sda1, logical block 1073741761
[ 5530.745662] attempt to access beyond end of device
[ 5530.745668] sda: rw=0, want=4294967276, limit=7503872
[ 5530.745672] Buffer I/O error on device sda1, logical block 1073741818
[ 5530.745677] attempt to access beyond end of device
[ 5530.745682] sda: rw=0, want=4294967280, limit=7503872
[ 5530.745686] Buffer I/O error on device sda1, logical block 1073741819
[ 5530.745692] attempt to access beyond end of device
[ 5530.745696] sda: rw=0, want=4294967276, limit=7503872
[ 5530.745700] Buffer I/O error on device sda1, logical block 1073741818
[ 5530.745705] attempt to access beyond end of device
[ 5530.745709] sda: rw=0, want=4294967280, limit=7503872
[ 5530.745714] Buffer I/O error on device sda1, logical block 1073741819
[ 5530.745874] attempt to access beyond end of device
[ 5530.745880] sda: rw=0, want=4294967292, limit=7503872
[ 5530.745884] Buffer I/O error on device sda1, logical block 1073741822
[ 5530.745891] attempt to access beyond end of device
[ 5530.745895] sda: rw=0, want=4294967292, limit=7503872
[ 5530.745899] Buffer I/O error on device sda1, logical block 1073741822
[ 5530.745914] attempt to access beyond end of device
[ 5530.745919] sda: rw=0, want=4294967292, limit=7503872
[ 5530.745933] attempt to access beyond end of device
[ 5530.745938] sda: rw=0, want=4294967292, limit=7503872
[ 5530.745950] attempt to access beyond end of device
[ 5530.745955] sda: rw=0, want=4294967292, limit=7503872
[ 5530.745968] attempt to access beyond end of device
[ 5530.745973] sda: rw=0, want=4294967292, limit=7503872
[ 5530.745986] attempt to access beyond end of device
[ 5530.745991] sda: rw=0, want=4294967292, limit=7503872
[ 5530.746008] attempt to access beyond end of device
[ 5530.746013] sda: rw=0, want=4294967228, limit=7503872
[ 5530.746017] attempt to access beyond end of device
[ 5530.746022] sda: rw=0, want=4294967232, limit=7503872
[ 5530.746036] attempt to access beyond end of device
[ 5530.746041] sda: rw=0, want=4294967284, limit=7503872
[ 5530.746045] attempt to access beyond end of device
[ 5530.746050] sda: rw=0, want=4294967288, limit=7503872
[ 5530.746062] attempt to access beyond end of device
[ 5530.746067] sda: rw=0, want=4294967292, limit=7503872
[ 5530.746080] attempt to access beyond end of device
[ 5530.746085] sda: rw=0, want=4294967292, limit=7503872
[ 5530.972296] attempt to access beyond end of device
[ 5530.972316] sda: rw=0, want=4294967044, limit=7503872
[ 5530.972322] attempt to access beyond end of device
[ 5530.972327] sda: rw=0, want=4294967048, limit=7503872
[ 5530.972333] attempt to access beyond end of device
[ 5530.972337] sda: rw=0, want=4294967044, limit=7503872
[ 5530.972341] attempt to access beyond end of device
[ 5530.972346] sda: rw=0, want=4294967048, limit=7503872
[ 5530.972368] attempt to access beyond end of device
[ 5530.972373] sda: rw=0, want=4294967276, limit=7503872
[ 5530.972378] attempt to access beyond end of device
[ 5530.972383] sda: rw=0, want=4294967280, limit=7503872
[ 5530.972388] attempt to access beyond end of device
[ 5530.972392] sda: rw=0, want=4294967276, limit=7503872
[ 5530.972396] attempt to access beyond end of device
[ 5530.972401] sda: rw=0, want=4294967280, limit=7503872
[ 5530.972552] attempt to access beyond end of device
[ 5530.972557] sda: rw=0, want=4294967292, limit=7503872
[ 5530.972563] attempt to access beyond end of device
[ 5530.972568] sda: rw=0, want=4294967292, limit=7503872
[ 5530.972582] attempt to access beyond end of device
[ 5530.972587] sda: rw=0, want=4294967292, limit=7503872
[ 5530.972600] attempt to access beyond end of device
[ 5530.972605] sda: rw=0, want=4294967292, limit=7503872
[ 5530.972616] attempt to access beyond end of device
[ 5530.972621] sda: rw=0, want=4294967292, limit=7503872
[ 5530.972634] attempt to access beyond end of device
[ 5530.972639] sda: rw=0, want=4294967292, limit=7503872
[ 5530.972652] attempt to access beyond end of device
[ 5530.972656] sda: rw=0, want=4294967292, limit=7503872
[ 5530.972673] attempt to access beyond end of device
[ 5530.972677] sda: rw=0, want=4294967228, limit=7503872
[ 5530.972682] attempt to access beyond end of device
[ 5530.972687] sda: rw=0, want=4294967232, limit=7503872
[ 5530.972702] attempt to access beyond end of device
[ 5530.972707] sda: rw=0, want=4294967284, limit=7503872
[ 5530.972712] attempt to access beyond end of device
[ 5530.972716] sda: rw=0, want=4294967288, limit=7503872
[ 5530.972730] attempt to access beyond end of device
[ 5530.972735] sda: rw=0, want=4294967292, limit=7503872
[ 5530.972747] attempt to access beyond end of device
[ 5530.972752] sda: rw=0, want=4294967292, limit=7503872
[ 5531.159146] attempt to access beyond end of device
[ 5531.159167] sda: rw=0, want=4294967044, limit=7503872
[ 5531.159173] attempt to access beyond end of device
[ 5531.159179] sda: rw=0, want=4294967048, limit=7503872
[ 5531.159184] attempt to access beyond end of device
[ 5531.159189] sda: rw=0, want=4294967044, limit=7503872
[ 5531.159193] attempt to access beyond end of device
[ 5531.159198] sda: rw=0, want=4294967048, limit=7503872
[ 5531.159218] attempt to access beyond end of device
[ 5531.159223] sda: rw=0, want=4294967276, limit=7503872
[ 5531.159228] attempt to access beyond end of device
[ 5531.159232] sda: rw=0, want=4294967280, limit=7503872
[ 5531.159237] attempt to access beyond end of device
[ 5531.159242] sda: rw=0, want=4294967276, limit=7503872
[ 5531.159246] attempt to access beyond end of device
[ 5531.159251] sda: rw=0, want=4294967280, limit=7503872
[ 5531.159399] attempt to access beyond end of device
[ 5531.159405] sda: rw=0, want=4294967292, limit=7503872
[ 5531.159411] attempt to access beyond end of device
[ 5531.159416] sda: rw=0, want=4294967292, limit=7503872
[ 5531.159430] attempt to access beyond end of device
[ 5531.159435] sda: rw=0, want=4294967292, limit=7503872
[ 5531.159449] attempt to access beyond end of device
[ 5531.159454] sda: rw=0, want=4294967292, limit=7503872
[ 5531.159466] attempt to access beyond end of device
[ 5531.159471] sda: rw=0, want=4294967292, limit=7503872
[ 5531.159485] attempt to access beyond end of device
[ 5531.159490] sda: rw=0, want=4294967292, limit=7503872
[ 5531.159503] attempt to access beyond end of device
[ 5531.159508] sda: rw=0, want=4294967292, limit=7503872
[ 5531.159524] attempt to access beyond end of device
[ 5531.159529] sda: rw=0, want=4294967228, limit=7503872
[ 5531.159534] attempt to access beyond end of device
[ 5531.159538] sda: rw=0, want=4294967232, limit=7503872
[ 5531.159557] attempt to access beyond end of device
[ 5531.159562] sda: rw=0, want=4294967284, limit=7503872
[ 5531.159567] attempt to access beyond end of device
[ 5531.159571] sda: rw=0, want=4294967288, limit=7503872
[ 5531.159584] attempt to access beyond end of device
[ 5531.159589] sda: rw=0, want=4294967292, limit=7503872
[ 5531.159602] attempt to access beyond end of device
[ 5531.159607] sda: rw=0, want=4294967292, limit=7503872

udevmonitor
> udevmonitor will print the received events for:
UDEV the event which udev sends out after rule processing
UEVENT the kernel uevent

UEVENT[1210515480.699829] add      /devices/pci0000:00/0000:00:02.0/usb1/1-2 (usb)
UEVENT[1210515480.699941] add      /devices/pci0000:00/0000:00:02.0/usb1/1-2/usb_endpoint/usbdev1.8_ep00 (usb_endpoint)
UDEV  [1210515480.716549] add      /devices/pci0000:00/0000:00:02.0/usb1/1-2 (usb)
UEVENT[1210515480.717065] add      /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0 (usb)
UEVENT[1210515480.717100] add      /slab/:0000320 (slab)
UEVENT[1210515480.724651] add      /class/scsi_host/host6 (scsi_host)
UDEV  [1210515480.730914] add      /devices/pci0000:00/0000:00:02.0/usb1/1-2/usb_endpoint/usbdev1.8_ep00 (usb_endpoint)
UEVENT[1210515480.733431] add      /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/usb_endpoint/usbdev1.8_ep81 (usb_endpoint)
UEVENT[1210515480.733538] add      /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/usb_endpoint/usbdev1.8_ep02 (usb_endpoint)
UEVENT[1210515480.733563] add      /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/usb_endpoint/usbdev1.8_ep83 (usb_endpoint)
UDEV  [1210515480.767022] add      /slab/:0000320 (slab)
UDEV  [1210515481.018620] add      /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0 (usb)
UDEV  [1210515481.021098] add      /class/scsi_host/host6 (scsi_host)
UDEV  [1210515481.024227] add      /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/usb_endpoint/usbdev1.8_ep81 (usb_endpoint)
UDEV  [1210515481.036268] add      /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/usb_endpoint/usbdev1.8_ep02 (usb_endpoint)
UDEV  [1210515481.039945] add      /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/usb_endpoint/usbdev1.8_ep83 (usb_endpoint)
UEVENT[1210515485.748943] add      /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/host6/target6:0:0/6:0:0:0 (scsi)
UEVENT[1210515485.749024] add      /class/scsi_disk/6:0:0:0 (scsi_disk)
UDEV  [1210515486.061196] add      /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/host6/target6:0:0/6:0:0:0 (scsi)
UDEV  [1210515486.090678] add      /class/scsi_disk/6:0:0:0 (scsi_disk)
UEVENT[1210515487.079160] add      /block/sda (block)
UEVENT[1210515487.079238] add      /block/sda/sda1 (block)
UEVENT[1210515487.079258] add      /class/scsi_device/6:0:0:0 (scsi_device)
UEVENT[1210515487.079279] add      /class/scsi_generic/sg0 (scsi_generic)
UDEV  [1210515487.092675] add      /class/scsi_device/6:0:0:0 (scsi_device)
UDEV  [1210515487.112331] add      /class/scsi_generic/sg0 (scsi_generic)
UEVENT[1210515487.134689] add      /kernel/uids/65534 (kernel)
UDEV  [1210515487.137348] add      /kernel/uids/65534 (kernel)
UEVENT[1210515487.321655] remove   /kernel/uids/65534 (kernel)
UDEV  [1210515487.324179] remove   /kernel/uids/65534 (kernel)
UDEV  [1210515487.425327] add      /block/sda (block)
UEVENT[1210515487.520537] add      /kernel/uids/65534 (kernel)
UDEV  [1210515487.529394] add      /kernel/uids/65534 (kernel)
UEVENT[1210515487.705681] remove   /kernel/uids/65534 (kernel)
UDEV  [1210515487.708008] remove   /kernel/uids/65534 (kernel)
UEVENT[1210515487.710028] add      /kernel/uids/65534 (kernel)
UDEV  [1210515487.712272] add      /kernel/uids/65534 (kernel)
UEVENT[1210515487.901938] remove   /kernel/uids/65534 (kernel)
UDEV  [1210515487.904413] remove   /kernel/uids/65534 (kernel)
UEVENT[1210515487.928893] add      /kernel/uids/65534 (kernel)
UDEV  [1210515487.931198] add      /kernel/uids/65534 (kernel)
UDEV  [1210515488.104141] add      /block/sda/sda1 (block)
UEVENT[1210515488.113684] remove   /kernel/uids/65534 (kernel)
UDEV  [1210515488.116116] remove   /kernel/uids/65534 (kernel)
UEVENT[1210515488.163661] add      /kernel/uids/65534 (kernel)
UDEV  [1210515488.166345] add      /kernel/uids/65534 (kernel)
UEVENT[1210515488.353682] remove   /kernel/uids/65534 (kernel)
UDEV  [1210515488.356316] remove   /kernel/uids/65534 (kernel)
UEVENT[1210515488.361876] add      /kernel/uids/65534 (kernel)
UDEV  [1210515488.364060] add      /kernel/uids/65534 (kernel)
UEVENT[1210515488.557681] remove   /kernel/uids/65534 (kernel)
UDEV  [1210515488.560210] remove   /kernel/uids/65534 (kernel)



---

### Post by hoatu on 2008-06-17
Same problem here. My Dbus and HAL is running. There doesn't seem to be an option to turn on automount in System > Preferences > Removable drives and media...

Please help!

:)

---

### Post by Odrodzona-Sarmacja on 2008-06-18
The only option is to edit fstab with
"gksudo mousepad /etc/fstab"
or if you just have terminal to use
"sudo nano /etc/fstab"
The mount is one like looking like like
" /dev/sda1 [device you get from "sudo blkid"] /media/mydir [mount point you must create first with "sudo mkdir /media/mydir"] vfat [vfat, ext3, ntfs, ext2 or whatever file system it is] nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000 0 0"
After you use "sudo mount -a" to mount hard drives specified in fstab, or you just reboot your computer, so they are automatically mounted. If you connect some of hard drives after booting up, then just run "sudo mount -a" in terminal to mount them correctly.

Good luck!

---

### Post by hoatu on 2008-06-18
Thanks for your response.

Unfortunately, the mp3 player connected via USB is not listed among the devices when I use sudo blkid.

/dev/sda1 is already on use on my machine. I am running Ubuntu on an Acer Aspire 1690 which has an annoying hidden partition called PQSERVICE mounted to /dev/sda1 which is nearly impossible to get rid of.

I'm happy enough to manually mount the USB MP3 player but I have no idea how to specify the location of it! Can you help? Thanks!

---

### Post by Abu_Dayya on 2008-06-18
[QUOTE=oyankee;4932671]
I can mount it manualy-this is not the problem. 
QUOTE]

How do you do that?
Some usb sticks (only one accualy) won't mount automatically, and i don't know the commad to mount it manually

---

### Post by pickarooney on 2008-07-02
I have two different types of SD card, one for music and one for my digital camera. Kubuntu used to mount them automatically to specified places - /media/music and /media/camera (defined using mstools.

Is there any way to get around the bug that breaks automount in Hardy in an intelligent way so that everything isn't just mounted to /media/disk?

---

### Post by Rix Computer Engineer ~# on 2008-09-19
I am having a similar problem. I followed the instructions and installed pmount and the output of that command is as follows.

eronique@delici:~$ ls /dev/disk/by-label -lah
total 0
drwxr-xr-x+ 2 root root  60 2008-09-18 22:07 .
drwxr-xr-x+ 6 root root 120 2008-09-18 22:07 ..
lrwxrwxrwx+ 1 root root  10 2008-09-18 22:07 WALKMAN -> ../../sdb1
veronique@delici:~$ pmount /dev/sdb1 WALKMAN
Warning: device /dev/sdb1 is already handled by /etc/fstab, supplied label is ignored
mount: only root can mount /dev/sdb1 on /mnt/sony
veronique@delici:~$ sudo pmount /dev/sdb1 WALKMAN
[sudo] password for veronique:
Warning: device /dev/sdb1 is already handled by /etc/fstab, supplied label is ignored
veronique@delici:~$ sudo pmount /dev/sdb1
mount: /dev/sdb1 already mounted or /mnt/sony busy
mount: according to mtab, /dev/sdb1 is already mounted on /mnt/sony
veronique@delici:~$


I have navigated to the mount directory and the folder is there but no music.
Also I have no icon on my desktop. I tried assigning a mount point in 
System Settings/Advanced/Disk & Filesystems but I do not think I did it right.

I need help really bad. (Truth) --->  My wife had Vista installed on the laptop I bought her and she uses the Sony Walkman to transfer music and videos from her laptop to the embedded device. I was not supposed to wipe her winblows OS and if I cant figure out how to get this working She will make me install Pista again ;((

Any suggestions?

Rick

---

