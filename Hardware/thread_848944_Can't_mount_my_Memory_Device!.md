---
title: "Can't mount my Memory Device!"
date: 2008-07-04
forum: Hardware
---

### Post by ~sHyLoCk~ on 2008-07-04
Plz help! When i plug in my device its not mounting, 
I installed moto4lin. Then opened moto4lin and clicked on Connect/Disconnect it showed:
[info] Phone is unpluged. Please connect it
Try to connect
[error] No phone found. Check preferences for AT Vendor/Product ID
[error] Unable to connect

My phone was plugged in and I am using it as Memory storage and my phone is MotoRazr2 V8. Its detecting when I 'dmesg' 

[ 462.469675] usb 5-5: new high speed USB device using ehci_hcd and address 2
[ 462.604548] usb 5-5: configuration #1 chosen from 1 choice
[ 462.710434] usbcore: registered new interface driver libusual
[ 462.719172] Initializing USB Mass Storage driver...
[ 462.720007] scsi4 : SCSI emulation for USB Mass Storage devices
[ 462.720429] usbcore: registered new interface driver usb-storage
[ 462.720433] USB Mass Storage support registered.
[ 462.720979] usb-storage: device found at 2
[ 462.720981] usb-storage: waiting for device to settle before scanning
[ 467.717995] usb-storage: device scan complete
[ 467.718949] scsi 4:0:0:0: Direct-Access Motorola MSnc. PQ: 1 ANSI: 4 CCS
[ 467.719714] scsi 4:0:0:1: Direct-Access Motorola MSnc. PQ: 1 ANSI: 4 CCS
[ 467.720147] scsi 4:0:0:0: Attached scsi generic sg2 type 0
[ 467.720196] scsi 4:0:0:1: Attached scsi generic sg3 type 0 
I also checked lsusb:
root@ubuntu:~# lsusb
Bus 005 Device 002: ID 22b8:6426 Motorola PCS
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000 

However On fdisk-l I get this:
Disk /dev/sda: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00e100e0

Device Boot Start End Blocks Id System
/dev/sda1 * 1 1306 10490413+ 7 HPFS/NTFS
/dev/sda2 1307 7301 48154837+ 5 Extended
/dev/sda5 1307 7050 46138648+ 83 Linux
/dev/sda6 7051 7301 2016126 82 Linux swap / Solaris

---

### Post by smo0th on 2008-07-04
I think this is related with other posts, it is basically the same problem, USB drives won't mount although they get partially recognized by the system. The painless and effortless workaround for this is restarting your PC and keep a USB drive always plugged because it seems to be an spontaneous delay which triggers some kind of USB bus DoS :( I have tried several things but none of them worked as good as keeping a drive always in.

---

### Post by ~sHyLoCk~ on 2008-07-04
Hmm ... I'll plug in my device and boot my system and check if it gets detected.


EDIT: Still nothing! :( Its not detecting.

---

### Post by ~sHyLoCk~ on 2008-07-05
Sorry for bringing this up again, but I really really need help with this! I cant switch back to windows just for this USB issue. :(

---

### Post by smo0th on 2008-07-05
hi there ~sHyLoCk~, lets see what we can do..

please post your output of the following commands:

```
sudo fdisk -l
cat /etc/fstab
df -h
lsmod|grep usb
lsusb
dmesg|grep scsi

```

this way we'll be able to have a picture of your computer's configuration

---

### Post by ~sHyLoCk~ on 2008-07-05
shylock@ubuntu:~$ sudo fdisk -l
[sudo] password for shylock: 

Disk /dev/sda: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00e100e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1306    10490413+   7  HPFS/NTFS
/dev/sda2            1307        7301    48154837+   5  Extended
/dev/sda5            1307        7050    46138648+  83  Linux
/dev/sda6            7051        7301     2016126   82  Linux swap / Solaris

shylock@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=3eec250c-8347-48a9-91e0-527663255d66 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=751e9942-1818-4cd6-9687-216f15007b60 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

shylock@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              44G  6.2G   36G  15% /
varrun                501M   96K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M   48K  501M   1% /dev
devshm                501M   12K  501M   1% /dev/shm
lrm                   501M   38M  463M   8% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       44G  6.2G   36G  15% /home/shylock/.gvfs

shylock@ubuntu:~$ lsmod|grep usb
usb_storage            73664  0 
libusual               19108  1 usb_storage
scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata
usbcore               146028  5 usb_storage,libusual,ehci_hcd,uhci_hcd

shylock@ubuntu:~$ lsusb
Bus 005 Device 002: ID 22b8:6426 Motorola PCS 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

shylock@ubuntu:~$ dmesg|grep scsi
[   28.801016] scsi0 : ata_piix
[   28.801053] scsi1 : ata_piix
[   29.307710] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SV0602H  RH10 PQ: 0 ANSI: 5
[   29.311465] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-H10A  JL02 PQ: 0 ANSI: 5
[   29.311612] scsi2 : ata_piix
[   29.311645] scsi3 : ata_piix
[   29.724379] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   29.724395] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   29.740210] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   29.740277] sr 0:0:1:0: Attached scsi CD-ROM sr0
[  863.447546] scsi4 : SCSI emulation for USB Mass Storage devices
[  868.443377] scsi 4:0:0:0: Direct-Access     Motorola MSnc.                 PQ: 1 ANSI: 4 CCS
[  868.444245] scsi 4:0:0:1: Direct-Access     Motorola MSnc.                 PQ: 1 ANSI: 4 CCS
[  868.444603] scsi 4:0:0:0: Attached scsi generic sg2 type 0
[  868.444653] scsi 4:0:0:1: Attached scsi generic sg3 type 0

---

### Post by smo0th on 2008-07-05
lol... sorry for my sleepyness.. I saw you already posted some of the commands, okay..
> shylock@ubuntu:~$ lsmod|grep usb
usb_storage            73664  0 
libusual               19108  1 usb_storage
scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata
usbcore               146028  5 usb_storage,libusual,ehci_hcd,uhci_hcd


right now I have my 4GB usb memory attached and working, comparing your output with mine:
```
smo0th@ubuntu:~$ lsmod|grep usb
usb_storage            81728  2 
libusual               22824  1 usb_storage
usbhid                 32576  1 
hid                    33408  1 usbhid
ide_core              141200  4 usb_storage,ide_disk,ide_cd,atiixp
scsi_mod              172856  4 sg,usb_storage,sd_mod,libata
usbcore               161584  8 xpad,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd

```
there are some differences like:
```

[COLOR="SeaGreen"]scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata[/COLOR]
[COLOR="DarkOrange"]scsi_mod              172856  4 sg,usb_storage,sd_mod,libata[/COLOR]
[COLOR="SeaGreen"]usbcore               146028  5 usb_storage,libusual,ehci_hcd,uhci_hcd[/COLOR]
[COLOR="DarkOrange"]usbcore               161584  8 xpad,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
[/COLOR]
```
and you don't have the following:
```
usbhid                 32576  1 
hid                    33408  1 usbhid
ide_core              141200  4 usb_storage,ide_disk,ide_cd,atiixp

```

let's try the following:

type 

```
sudo modprobe hid
sudo modprobe usbhid
```

and you could also try reloading the modules

```

sudo modprobe -r usb_storage
sudo modprobe -r usbcore
sudo modprobe usbcore
sudo modprobe usb_storage

```

the -r option removes the module, please try that and post back the results :)

---

### Post by ~sHyLoCk~ on 2008-07-05
shylock@ubuntu:~$ sudo modprobe -r usbcore
FATAL: Module usbcore is in use.

The rest were ok.
EVen after this when I connect my phone:
shylock@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00e100e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1306    10490413+   7  HPFS/NTFS
/dev/sda2            1307        7301    48154837+   5  Extended
/dev/sda5            1307        7050    46138648+  83  Linux
/dev/sda6            7051        7301     2016126   82  Linux swap / Solaris

:|

---

### Post by smo0th on 2008-07-05
hmmm ok... should I suppose you already restarted your PC with the USB drive connected and```
 /dev/sda1 * 1 1306 10490413+ 7 HPFS/NTFS
``` is your USB drive device?

---

### Post by rosegarden78 on 2008-07-16
KRZR has a hidden Micro-SD slot right on top of the SIM card.  Insert up to 2GB into here and voila!  Your MOTOKRZR will show up in Hardy when placed in Memory Card mode.

I spent hours trying to mount it w/o the MicroSD because I couldn't see the slot!  Luckily I hit a website showing me where to put it.  I think it's impossible to mount without a card inside.

---

