---
title: "Sandisk cruzer micro 4gb drive will not mount."
date: 2008-08-23
forum: General Help
---

### Post by icecloud on 2008-08-23
hey i've tried right clicking my usb removable disk and mounting it or opening and it wont allow me to mount it (which i'm guessing mount means to format) so is there a way to force mount this device?

---

### Post by qstraza on 2008-08-23
try mounting it from the command line, so if there is any error you can paste it and maybe we can help you.

plug your usb in, type this in terminal
```
sudo dmesg | tail -c 2000
```
Check which device is your usb and than mount it like this:
```
sudo mkdir /mnt/usb
sudo mount /dev/sda1 /mnt/usb
```
replace sda with your device name which you got from dmesg

---

### Post by icecloud on 2008-08-23
[ 1433.500104] usb 5-2: new high speed USB device using ehci_hcd and address 4
[ 1433.632867] usb 5-2: configuration #1 chosen from 1 choice
[ 1433.633450] scsi3 : SCSI emulation for USB Mass Storage devices
[ 1433.633939] usb-storage: device found at 4
[ 1433.633948] usb-storage: waiting for device to settle before scanning
[ 1438.623319] usb-storage: device scan complete
[ 1438.623899] scsi 3:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  4.05 PQ: 0 ANSI: 2
[ 1438.624679] scsi 3:0:0:1: CD-ROM            SanDisk  U3 Cruzer Micro  4.05 PQ: 0 ANSI: 2
[ 1438.635159] sd 3:0:0:0: [sde] Attached SCSI removable disk
[ 1438.635233] sd 3:0:0:0: Attached scsi generic sg6 type 0
[ 1438.640019] sr2: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[ 1438.640121] sr 3:0:0:1: Attached scsi CD-ROM sr2
[ 1438.640185] sr 3:0:0:1: Attached scsi generic sg7 type 5
[ 1517.412256] usb 5-1: new high speed USB device using ehci_hcd and address 5
[ 1517.545320] usb 5-1: configuration #1 chosen from 1 choice
[ 1517.545763] scsi4 : SCSI emulation for USB Mass Storage devices
[ 1517.546329] usb-storage: device found at 5
[ 1517.546336] usb-storage: waiting for device to settle before scanning
[ 1522.535507] usb-storage: device scan complete
[ 1522.536129] scsi 4:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 1522.540608] sd 4:0:0:0: [sdf] 7999487 512-byte hardware sectors (4096 MB)
[ 1522.541722] sd 4:0:0:0: [sdf] Write Protect is off
[ 1522.541731] sd 4:0:0:0: [sdf] Mode Sense: 64 00 00 08
[ 1522.541736] sd 4:0:0:0: [sdf] Assuming drive cache: write through
[ 1522.544088] sd 4:0:0:0: [sdf] 7999487 512-byte hardware sectors (4096 MB)
[ 1522.545089] sd 4:0:0:0: [sdf] Write Protect is off
[ 1522.545096] sd 4:0:0:0: [sdf] Mode Sense: 64 00 00 08
[ 1522.545101] sd 4:0:0:0: [sdf] Assuming drive cache: write through
[ 1522.545108]  sdf: sdf1 sdf2
[ 1522.941432] sd 4:0:0:0: [sdf] Attached SCSI removable disk
[ 1522.941512] sd 4:0:0:0: Attached scsi generic sg8 type 0
william@icecloud-desktop:~$ ew high speed USB device using ehci_hcd and address 4
bash: ew: command not found
william@icecloud-desktop:~$ [ 1433.632867] usb 5-2: configuration #1 chosen from 1 choice
bash: [: missing `]'
william@icecloud-desktop:~$ [ 1433.633450] scsi3 : SCSI emulation for USB Mass Storage devices
bash: [: missing `]'
william@icecloud-desktop:~$ [ 1433.633939] usb-storage: device found at 4
bash: [: missing `]'
william@icecloud-desktop:~$ [ 1433.633948] usb-storage: waiting for device to settle before scanning
bash: [: missing `]'
william@icecloud-desktop:~$ [ 1438.623319] usb-storage: device scan complete
bash: [: missing `]'
william@icecloud-desktop:~$ [ 1438.623899] scsi 3:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  4.05 PQ: 0 ANSI: 2
bash: [: missing `]'

ok so wheres the name i'm using? i'm kind of confused.

---

### Post by qstraza on 2008-08-23
well your usb has 2 partitions
```
[ 1522.545108] sdf: sdf1 sdf2
```

so type
```
sudo fdisk /dev/sdf -l
```

than mount the bigger one:
```
sudo mount /dev/sdf# /mnt/usb
```

make sure u make the /mnt/usb dir before mounting. Replace # with 1 or 2, whichever is bigger

---

### Post by icecloud on 2008-08-23
william@icecloud-desktop:~$ sudo mount /dev/sdf2 /mnt/usb
mount: /dev/sdf2 already mounted or /mnt/usb busy
mount: according to mtab, /dev/sdf2 is already mounted on /mnt/usb
william@icecloud-desktop:~$ 

but i cannot open the drive...? it still says drive not mounted

---

### Post by qstraza on 2008-08-23
type in 
```
nautilus /mnt/usb
```

now can you see your data?

or 
```
konqueror /mnt/usb
```
if you have kubuntu... did not check what are you using

---

### Post by icecloud on 2008-08-23
it opened yes but it was my ipod and not my scan disk all it had in there was ipd info and itunes folders...i had none of that on the scandisk...0.o

---

### Post by qstraza on 2008-08-23
so this is what you want, right?
to unmount the usb type in
```
sudo umount /mnt/usb
```
make sure that usb is not in use, otherwise you will get that "drive busy" error.
Drive is in use if you are in its directory, in this case /mnt/usb

---

### Post by icecloud on 2008-08-23
william@icecloud-desktop:~$ sudo unmount /mnt/usb
sudo: unmount: command not found
william@icecloud-desktop:~$

---

### Post by qstraza on 2008-08-23
well check what i wrote.

umount not unmount

---

### Post by icecloud on 2008-08-23
william@icecloud-desktop:~$ sudo umount /mnt/usb
umount: /mnt/usb: not mounted
william@icecloud-desktop:~$ sudo dmesg | tail -c 2000
AT: Directory bread(block 15556) failed
[ 5549.686127] FAT: Directory bread(block 15557) failed
[ 5549.686139] FAT: Directory bread(block 15558) failed
[ 5549.686150] FAT: Directory bread(block 15559) failed
[ 5549.688142] FAT: Directory bread(block 15560) failed
[ 5549.688157] FAT: Directory bread(block 15561) failed
[ 5549.688168] FAT: Directory bread(block 15562) failed
[ 5549.688179] FAT: Directory bread(block 15563) failed
[ 5549.688190] FAT: Directory bread(block 15564) failed
[ 5549.688201] FAT: Directory bread(block 15565) failed
[ 5549.688212] FAT: Directory bread(block 15566) failed
[ 5549.688224] FAT: Directory bread(block 15567) failed
[ 5549.688303] FAT: Directory bread(block 15480) failed
[ 5549.688314] FAT: Directory bread(block 15481) failed
[ 5549.688326] FAT: Directory bread(block 15482) failed
[ 5549.688338] FAT: Directory bread(block 15483) failed
[ 5549.688351] FAT: Directory bread(block 15484) failed
[ 5549.688363] FAT: Directory bread(block 15485) failed
[ 5549.688374] FAT: Directory bread(block 15486) failed
[ 5549.688386] FAT: Directory bread(block 15487) failed
[ 5886.030220] FAT: Directory bread(block 15456) failed
[ 5886.030508] FAT: Directory bread(block 15457) failed
[ 5886.030820] FAT: Directory bread(block 15458) failed
[ 5886.031137] FAT: Directory bread(block 15459) failed
[ 5886.031483] FAT: Directory bread(block 15460) failed
[ 5886.031872] FAT: Directory bread(block 15461) failed
[ 5886.032200] FAT: Directory bread(block 15462) failed
[ 5886.032535] FAT: Directory bread(block 15463) failed
[ 5886.115819] FAT: Directory bread(block 15456) failed
[ 5886.115841] FAT: Directory bread(block 15457) failed
[ 5886.115854] FAT: Directory bread(block 15458) failed
[ 5886.115866] FAT: Directory bread(block 15459) failed
[ 5886.115878] FAT: Directory bread(block 15460) failed
[ 5886.115889] FAT: Directory bread(block 15461) failed
[ 5886.115901] FAT: Directory bread(block 15462) failed
[ 5886.115914] FAT: Directory bread(block 15463) failed
william@icecloud-desktop:~$

---

### Post by qstraza on 2008-08-23
Did you see your data when u typed nautalius /mnt/usb ?

mount it again, can u even mount it?

---

### Post by Fastjack77 on 2008-08-23
This worked out for me using an 8gig Sandisk Cruser Contour, on Ubuntu 7.10.

Thanks a lot!

> **qstraza said:**
> try mounting it from the command line, so if there is any error you can paste it and maybe we can help you.

plug your usb in, type this in terminal
```
sudo dmesg | tail -c 2000
```
Check which device is your usb and than mount it like this:
```
sudo mkdir /mnt/usb
sudo mount /dev/sda1 /mnt/usb
```
replace sda with your device name which you got from dmesg

---

### Post by StephSD3 on 2008-11-22
hmm, I have the same problem. Also an Sandisk Cruzer 4Go.
the thing that I get back when I try the above mensioned stuff:
```
dries@LP-UB:~$ sudo dmesg | tail -c 2000
[sudo] password for dries: 
2.868200]   groups: 1 0
[   82.868209]   domain 1: span 0-1 level CPU
[   82.868214]    groups: 0-1
[   95.098632] NET: Registered protocol family 10
[   95.100225] lo: Disabled Privacy Extensions
[   95.102704] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  150.564756] ppdev0: registered pardevice
[  150.613407] ppdev0: unregistered pardevice
[  151.570891] ppdev0: registered pardevice
[  151.620889] ppdev0: unregistered pardevice
[  152.941174] ppdev0: registered pardevice
[  152.989062] ppdev0: unregistered pardevice
[ 1710.440198] usb 7-5: new high speed USB device using ehci_hcd and address 3
[ 1710.574311] usb 7-5: configuration #1 chosen from 1 choice
[ 1710.691538] usbcore: registered new interface driver libusual
[ 1710.700240] Initializing USB Mass Storage driver...
[ 1710.700375] scsi6 : SCSI emulation for USB Mass Storage devices
[ 1710.701118] usbcore: registered new interface driver usb-storage
[ 1710.701125] USB Mass Storage support registered.
[ 1710.701495] usb-storage: device found at 3
[ 1710.701501] usb-storage: waiting for device to settle before scanning
[ 1715.701220] usb-storage: device scan complete
[ 1715.702951] scsi 6:0:0:0: Direct-Access     SanDisk  Cruzer Contour   4.08 PQ: 0 ANSI: 2
[ 1715.705052] sd 6:0:0:0: [sdb] 7905280 512-byte hardware sectors (4048 MB)
[ 1715.709996] sd 6:0:0:0: [sdb] Write Protect is off
[ 1715.710003] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1715.710006] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1715.739268] sd 6:0:0:0: [sdb] 7905280 512-byte hardware sectors (4048 MB)
[ 1715.739789] sd 6:0:0:0: [sdb] Write Protect is off
[ 1715.739793] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1715.739796] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1715.739801]  sdb: sdb1
[ 1715.751012] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 1715.751145] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 1716.234953] UDF-fs: No partition found (1)
[ 1716.380563] ISOFS: Unable to identify CD-ROM format.
dries@LP-UB:~$ sudo su
root@LP-UB:/home/dries# sudo mkdir /mnt/usb
root@LP-UB:/home/dries# mount dev/sdb1 /mnt/usb
mount: special device dev/sdb1 does not exist
root@LP-UB:/home/dries# mount dev/sdb /mnt/usb
mount: special device dev/sdb does not exist

```
I also get this when I try to read an other hard drive or so. Didn't had this problem with earlier versions of Ubuntu...
any help please? =D>
[edit] srry, didn't mension that I allready deleted the irritating U3 partition...[/edit]

---

### Post by qstraza on 2008-11-23
> **StephSD3 said:**
> hmm, I have the same problem. Also an Sandisk Cruzer 4Go.
the thing that I get back when I try the above mensioned stuff:
```
dries@LP-UB:~$ sudo dmesg | tail -c 2000
[sudo] password for dries: 
2.868200]   groups: 1 0
[   82.868209]   domain 1: span 0-1 level CPU
[   82.868214]    groups: 0-1
[   95.098632] NET: Registered protocol family 10
[   95.100225] lo: Disabled Privacy Extensions
[   95.102704] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  150.564756] ppdev0: registered pardevice
[  150.613407] ppdev0: unregistered pardevice
[  151.570891] ppdev0: registered pardevice
[  151.620889] ppdev0: unregistered pardevice
[  152.941174] ppdev0: registered pardevice
[  152.989062] ppdev0: unregistered pardevice
[ 1710.440198] usb 7-5: new high speed USB device using ehci_hcd and address 3
[ 1710.574311] usb 7-5: configuration #1 chosen from 1 choice
[ 1710.691538] usbcore: registered new interface driver libusual
[ 1710.700240] Initializing USB Mass Storage driver...
[ 1710.700375] scsi6 : SCSI emulation for USB Mass Storage devices
[ 1710.701118] usbcore: registered new interface driver usb-storage
[ 1710.701125] USB Mass Storage support registered.
[ 1710.701495] usb-storage: device found at 3
[ 1710.701501] usb-storage: waiting for device to settle before scanning
[ 1715.701220] usb-storage: device scan complete
[ 1715.702951] scsi 6:0:0:0: Direct-Access     SanDisk  Cruzer Contour   4.08 PQ: 0 ANSI: 2
[ 1715.705052] sd 6:0:0:0: [sdb] 7905280 512-byte hardware sectors (4048 MB)
[ 1715.709996] sd 6:0:0:0: [sdb] Write Protect is off
[ 1715.710003] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1715.710006] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1715.739268] sd 6:0:0:0: [sdb] 7905280 512-byte hardware sectors (4048 MB)
[ 1715.739789] sd 6:0:0:0: [sdb] Write Protect is off
[ 1715.739793] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1715.739796] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1715.739801]  sdb: sdb1
[ 1715.751012] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 1715.751145] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 1716.234953] UDF-fs: No partition found (1)
[ 1716.380563] ISOFS: Unable to identify CD-ROM format.
dries@LP-UB:~$ sudo su
root@LP-UB:/home/dries# sudo mkdir /mnt/usb
root@LP-UB:/home/dries# mount dev/sdb1 /mnt/usb
mount: special device dev/sdb1 does not exist
root@LP-UB:/home/dries# mount dev/sdb /mnt/usb
mount: special device dev/sdb does not exist

```
I also get this when I try to read an other hard drive or so. Didn't had this problem with earlier versions of Ubuntu...
any help please? =D>
[edit] srry, didn't mension that I allready deleted the irritating U3 partition...[/edit]

well what seems to be the problem here? I dont see any. Your system detects usb, so just mount it and it should work. To do so, mkdir, sth like /mnt/usb, than do sudo mount /dev/sdb1 /mnt/usb

---

### Post by StephSD3 on 2008-11-23
hey, thank you for the reply.
as you can see I tried what you say, but it refuses to do so...
```
root@LP-UB:/home/dries# sudo mkdir /mnt/usb
root@LP-UB:/home/dries# mount dev/sdb1 /mnt/usb
**mount: special device dev/sdb1 does not exist**
root@LP-UB:/home/dries# mount dev/sdb /mnt/usb
mount: special device dev/sdb does not exist
```
I managed to get my windows partition mounted when I boot (in Ubuntu offc) with [**this**](http://www.arsgeek.com/2006/11/01/ubuntu-tricks-how-to-mount-your-windows-partition-and-make-it-readwritable-with-ntfs-3g/#comment-56281) but it doesn't work for USB sticks.. :D
Oh yes, before I forget: Once in a while it gives me an error message which means to say I didn't properly closed or retrieved the USB under Windows.

---

### Post by mc4man on 2008-11-23
i not really sure why it doesn't automount but in any event the command your using is slightly wrong.

> mount dev/sdb1 /mnt/usb

should be

mount /dev/sdb1 /mnt/usb

notice the / before dev

Edit:

Why don't you make sure it's been safely removed in windows (just insert into windows box and then safely remove.

Then run this and check that media_automount and media_automount-open boxes are checked and that media_autorun_never isn't.  (see screen

```
gconf-editor
```

Your drive should auto mount to /media/volume name (probably /media/disk

browse there and ck.

---

### Post by StephSD3 on 2008-11-23
thank you so much, will try it right away :D
EDIT: Thanx, it works now

---

