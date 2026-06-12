---
title: "Logical volume space is not detected"
date: 2009-11-02
forum: Hardware
---

### Post by MaheshChowta on 2009-11-02
We installed Ubuntu Server 9.04 on following machine.

HP ProLiant ML350G6(Tower Model) / Hot Plug LFF Model/
(1) Quad-Core Intel Xeon E5504Processor (2.0GHz, 80 Watts, )
/ 4MB Level 3 cache / 4GB (2 x 2 GB) PC3-10600R (DDR3-1333) 
Registered DIMMS /Embedded NC326i Dual port Gigabit Server Adapter / 
Smart Array P410i with no memory/ DVD ROM Drive/
460 Watt Power Supply/ 4TB sata hard disks.

This server used for storing images of the scanned medical records.

The system is set for RAID 5. 
While installing ubuntu we made Logical Volume Group 
with 2.59 TB space as FAT32 system.
We made 4 logical volumes from that group.

we mounted that drive in fstab.
But if we give df –h command, 
we will not get complete storage space of 2.59TB. 

How we can extend logical volume? 

Kindly help us.

We listed some command outputs here. 

Uname –a
Linux ubuntu 2.6.28-11-generic #42 – ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i68 GNU/Linux

------------------------------------------------------------------------------------------------

df

Filesystem Size Used	 Avail Use% Mounted on

/dev/cciss/c0d0p1 138G 992M 130G 1% 
/tmpfs 1.8G 0 1.8G 0% 
/lib/init/rwvarrun	 1.8G 660K 1.8G 1% 
/var/runvarlock 1.8G 0 1.8G 0% 
/var/lockudev 1.8G 168K 1.8G 1% 
/devtmpfs 1.8G 0 1.8G 0% 
/dev/shm/dev/mapper/mrd-disk1	 466G 13G 454G 3% /mnt

------------------------------------------------------------------------------------------------

pvscan

PV /dev/cciss/c0d0p3
VG mrd
lvm2 [2.59 TB / 0 free]
Total: 1 [604.88 GB] / in use: 1 [604.88 GB] / in no VG: 0 [0 ]
------------------------------------------------------------------------------------------------

pvdisplay

--- Physical volume ---

PV Name /dev/cciss/c0d0p3
VG Name mrd
PV Size 2.59 TB / not usable 2.18 MB
Allocatable yes (but full)
PE Size (KByte) 4096
Total PE 679138
Free PE 0
Allocated PE 679138
PV UUID 4nmtwG-o3Aj-YvFQ-Zp6F-DfTW-n377-JkOL8a

------------------------------------------------------------------------------------------------
vgscan

Reading all physical volumes. This may take a while...
Found volume group "mrd" using metadata type lvm2

------------------------------------------------------------------------------------------------

vgdisplay

--- Volume group ---

VG Name mrd
System ID 
Format lvm2
Metadata Areas 1
Metadata Sequence No 7
VG Access read/write
VG Status resizable
MAX LV 0
Cur LV 4
Open LV 1
Max PV 0
Cur PV 1
Act PV 1
VG Size 2.59 TB
PE Size 4.00 MB
Total PE 679138
Alloc PE / Size 679138 / 2.59 TB
Free PE / Size 0 / 0 
VG UUID GA3UdC-fRz1-Aozs-i3ZV-LPki-hkVi-mHjemr

------------------------------------------------------------------------------------------------
lvscan

ACTIVE '/dev/mrd/disk1' [465.66 GB] inherit
ACTIVE '/dev/mrd/disk2' [651.93 GB] inherit
ACTIVE '/dev/mrd/disk3' [651.93 GB] inherit
ACTIVE '/dev/mrd/disk4' [883.37 GB] inherit

------------------------------------------------------------------------------------------------

lvdisplay

--- Logical volume ---

LV Name /dev/mrd/disk1
VG Name mrd
LV UUID IqD6hX-D3KW-ydOT-9o9y-rCVc-Mepq-1olSXl
LV Write Access read/write
LV Status available # open 1
LV Size 465.66 GB
Current LE 119209
Segments 1
Allocation inherit
Read ahead sectors auto
currently set to 256
Block device 252:0


--- Logical volume ---

LV Name /dev/mrd/disk2
VG Name mrd
LV UUID kC3JUU-SiQH-cQ6k-L4tK-Iup7-id16-Nkx4wa
LV Write Access read/write
LV Status available # open 0
LV Size 651.93 GB
Current LE 166893
Segments 1
Allocation inherit
Read ahead sectors auto
currently set to 256
Block device 252:1



--- Logical volume ---

LV Name /dev/mrd/disk3
VG Name mrd
LV UUID 0HYyHG-OJdH-VYmG-DNmA-BlrL-jiPX-vFVEpz
LV Write Access read/write
LV Status available	# open 0
LV Size 651.93 GB
Current LE 166893
Segments 1
Allocation inherit
Read ahead sectors auto
currently set to 256
Block device 252:2


--- Logical volume ---

LV Name /dev/mrd/disk4
VG Name mrd
LV UUID rdOF33-32et-E70J-vrob-iN9w-H25o-qbiy12
LV Write Access read/write
LV Status available	# open 0
LV Size 883.37 GB
Current LE 226143
Segments 1
Allocation inherit
Read ahead sectors auto
currently set to 256
Block device 252:3

------------------------------------------------------------------------------------------------

---

