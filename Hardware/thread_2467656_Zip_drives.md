---
title: "Zip drives"
date: 2021-10-03
forum: Hardware
---

### Post by monkey-harris on 2021-10-03
Zip drive 100 parallel. New to Ubuntu. Can some one give me an idiots guide (please tell me how to suck eggs) how to access my old zip drive. What to type and where. I know everyone will say why would you want to?? Need to access some old document / cnc instruction manuals.](*,)

---

### Post by Frogs Hair on 2021-10-03
There is a package named jazip that may help . I can only provide a [link]("https://manpages.ubuntu.com/manpages/focal/man8/jazipconfig.8.html") to the information to read before installing. Another forum may know more about using this program. 

```
sudo apt install jazip
```

---

### Post by monkey-harris on 2021-10-04
Thank you, will try that.

---

### Post by rsteinmetz70112 on 2021-10-04
Have your tried just connecting it? Often stuff just works.
I'd try that first. Shutdown, hook up the ZIP Drive and restart.
Then start Gnome Disks and see if it's recognized.
 
Then there's this:
[https://help.ubuntu.com/community/IomegaZIPDrive](https://help.ubuntu.com/community/IomegaZIPDrive)
Unfortunately it doesn't say what versions of Ubuntu it's for.

---

### Post by Dennis N on 2021-10-04
Since it's the older parallel port Zip drive model, have you looked into parallel to USB adapters? Checking for such a device on Amazon, I see them offered in a wide range of prices.

I still have an old Zip drive USB model, and it works on Linux. These drives are quite costly now to acquire from what I see.

---

### Post by monkey-harris on 2021-10-04
**cat /proc/scsi/scsi produced the folliowng report:**Attached devices:
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD400BB-00JH Rev: 1C05
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi6 Channel: 00 Id: 06 Lun: 00
  Vendor: IOMEGA   Model: ZIP 100          Rev: J.03
  Type:   Direct-Access                    ANSI  SCSI revision: 02

Gnome has now listed "Block Device /dev/sdb"   Is that my Zip drive?

---

### Post by rsteinmetz70112 on 2021-10-04
In a terminal <crtl> <alt> T 
```
$ lsblk
```

Should list all devices. If you put media in it it should tell you what it is.

---

### Post by monkey-harris on 2021-10-05
Any thoughts?

$ lsblk
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
loop0    7:0    0 55.4M  1 loop /snap/core18/2128
loop1    7:1    0 99.3M  1 loop /snap/core/11743
loop2    7:2    0 99.4M  1 loop /snap/core/11606
loop3    7:3    0    4K  1 loop /snap/bare/5
loop4    7:4    0 10.2M  1 loop /snap/canonical-livepatch/105
loop5    7:5    0  219M  1 loop /snap/gnome-3-34-1804/72
loop6    7:6    0 65.2M  1 loop /snap/gtk-common-themes/1519
loop7    7:7    0   51M  1 loop /snap/snap-store/547
loop8    7:8    0 65.1M  1 loop /snap/gtk-common-themes/1515
loop9    7:9    0 32.3M  1 loop /snap/snapd/12704
loop10   7:10   0 32.3M  1 loop /snap/snapd/13170
sda      8:0    0 37.3G  0 disk 
&#9500;&#9472;sda1   8:1    0  512M  0 part /boot/efi
&#9500;&#9472;sda2   8:2    0    1K  0 part 
&#9492;&#9472;sda5   8:5    0 36.8G  0 part /

---

### Post by rsteinmetz70112 on 2021-10-05
Don't see the zip drive. Was it connected and did it have media in it?

If tyhe parallel port on the motherboard or on a pci card?

Is the parallel port device in Ubuntu?
Open a terminal/console and check if the lp, ppdev, and parport_pc kernel modules are loaded:
$ lsmod | grep lp
$ lsmod | grep ppdev
$ lsmod | grep parport_pc

---

### Post by monkey-harris on 2021-10-06
Hope this means something to you?

paul@paul-GA-78LMT-USB3:~$ lsmod | grep lp
drm_ttm_helper         16384  1 radeon
ttm                    73728  2 radeon,drm_ttm_helper
drm_kms_helper        237568  1 radeon
cec                    53248  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
glue_helper            16384  1 aesni_intel
lp                     20480  0
drm                   548864  9 drm_kms_helper,radeon,drm_ttm_helper,ttm
parport                65536  4 parport_pc,lp,ppdev,ppa
paul@paul-GA-78LMT-USB3:~$ lsmod | grep ppdev
ppdev                  24576  0
parport                65536  4 parport_pc,lp,ppdev,ppa
paul@paul-GA-78LMT-USB3:~$ lsmod | grep parport_pc
parport_pc             45056  2
parport                65536  4 parport_pc,lp,ppdev,ppa
paul@paul-GA-78LMT-USB3:~$ 


Thanks in advance for your assistance.

---

