---
title: "Linux cannot detect SATA ssd"
date: 2019-11-20
forum: Hardware
---

### Post by dushyant28 on 2019-11-20
hello,
i have a pcb board in which there is a slot for M.2 SATA ssd. when I connect this board to linux system, it cannot detect.
however, when I type
 fdisk -l it shows that /dev/sda 119 gb( sata ssd is 128 gb)

but when i type 
parted -l it shows "error: /dev/sda: unrecognized disk label
model : ata lenovo ssd
disk /dev/sda: 128gb
partition table: unknown

not able to understand this issue, since I am new to linus. I am using ubuntu.
if it requires any driver to install to detect the sata ssd or need to do some setting?

please help me about this.

Thanks

---

### Post by VMC on 2019-11-20
In BIOS settings. Is settings for Intel RST or AHCI.

---

### Post by dushyant28 on 2019-11-20
Hello VMS,
i cannot see the settings for intel RST or AHCi in the the bios settings

---

### Post by oldfred on 2019-11-20
There are multiple labels.
One is how drive is partitioned old MBR or newer gpt.

This often shows a label error. Not to be confused with partition or format labels (names).
partition table: unknown

Also many SSD need firmware update to be correctly seen.

This does not mention changing to gpt which you need to do first.
Select gpt under device, advanced over msdos(MBR) default partitioning before starting.
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by dushyant28 on 2019-11-21
Hello oldFred,
thanks for the reply.
the thing is it is not able to detected by the BIOS. and BIPS not showing any settings related to the AHCI.
is gparted necessary or like you said SSD need firmware update to be correctly seen?
if it needs any firmware, let me know about it.
and by gparted if it not happened then what;s the process?

thanks

---

### Post by VMC on 2019-11-21
The output of the fdisk has the info regarding type, for ex. "Disklabel type: gpt"

---

### Post by dushyant28 on 2019-11-21
after doing fdisk, it is showing 
available columns (for -0)
gpt: deice start end sectors size type type-UUID
and some other abbreviations like -l, -o, -t.

and also in bios setting, there are three options: 
UEFI mode 
 Legacy mode
uefi & legacy mode
now my linux running on uefi mode and not able to detect the sata ssd

---

### Post by oldfred on 2019-11-21
If UEFI sees SSD, but Linux tools do not, that is often the firmware update.
You need to see if Lenovo has firmware for the brand SSD you have.

If not seen in UEFI, then double check connections and how installed. No operating system will see a drive that is not correctly seen in UEFI/BIOS.

---

### Post by dushyant28 on 2019-11-21
in uefi mode by doing fdisk -l it shows, /dev/sda 119 gb but not able to detect.
can I intall ahci driver for sata? i have read somewhere about it but I have less information.
i want to use gparted at the end by trying other options.

so can you give some links for ahci driver information or how to install in linux that will be a great help.

---

### Post by oldfred on 2019-11-21
AHCI is default with Linux.
You can install AHCI drivers into Windows.
And AHCI is just a drive setting in UEFI/BIOS. It may show RAID/Intel RST even when one drive.

---

### Post by dushyant28 on 2019-11-22
hello,
thanks for the help.
the query is solved.

firstly i make a seperate folder in the linux and then mount the ssd
first i mounted by the command 'mount dev/sda/folder name and then
by using 'mkfs.ext4' command it can make the space for the new drive.
and after that i did df -hT command to check the space.

thank you so much for the help

---

### Post by VMC on 2019-11-22
Something is amiss here. m.2 ssd's are nvme not dev's. 
My ssd is 'dev' mount '/dev/sdaX'. Can leave RST in BIOS
 My m.2 ssd is nvme as in /nvme/sdaX which need AHCI in BIOS if dual boot.

You show m.2 ssd as 'dev' mounted and not 'nvme'

---

### Post by CatKiller on 2019-11-22
> **VMC said:**
> Something is amiss here. m.2 ssd's are nvme not dev's. 

Not necessarily. M.2 is just the form factor: the drives themselves could be using SATA, PCIe/AHCI or PCIe/NVMe, depending on the capabilities and configuration of both the drive and the host.

---

### Post by dushyant28 on 2019-11-22
ssd's are different type. mine is not NVMe, just sata ssd. NVME's are other kind and they are faster than sata ssd.
so it creeates /dev/sda. and i have to mount to the system inside some folder.
so i first created a folder and then mounted 
/dev/sda/<foldername>

---

### Post by VMC on 2019-11-22
I've never seen an m.2 that wasn't nvme. I'll have to find one. I do know mine plainly states on the box nvme. I mistakenly thought they all were.

---

### Post by oldfred on 2019-11-22
My motherboard says this:
> The M.2 connector supports M.2 SATA SSDs and M.2 PCIe SSDs
When I built system several years ago NVMe drives were expensive, so I have a SATA drive plugged into the M.2.

```
fred@Bionic-Z170N:~$ sudo lshw -C disk -short
[sudo] password for fred: 
H/W path           Device     Class          Description
========================================================
/0/1/0.0.0         /dev/sda   disk           250GB Samsung SSD 850
/0/2/0.0.0         /dev/sdb   disk           1TB HGST HTS721010A9

```

---

### Post by VMC on 2019-11-23
Fred, does you m.2 have "1" slot or "2" slots on the connector side?
I just read the "1" is NVME, and the "2" is SATA

---

### Post by oldfred on 2019-11-23
I think mine only has one. Do not remember and manual only says connector.
Also if I use M.2 as SATA, then first SATA port (SATA3_0)is taken or not usable.

My Motherboard:
Gigabyte LGA1151 Intel Z170 Mini-ITX DDR4 Motherboards GA-Z170N-Gaming 5

---

### Post by dushyant28 on 2019-11-25
sata slots are different kind. they have B key, M key and B&M key. what I am using is B&M key. and motherboard have eithe B slot or M slot. nvme is different. when you buy ssd, it is cleasrly mention what kind you want to buy either key version or nvme version.

---

### Post by dushyant28 on 2019-11-25
how do you check this H/W path ? and also after switching on the system i have to again mount my ssd by using command in linux.
is there any command by which i dont have to mount again after i switched on the system?

---

