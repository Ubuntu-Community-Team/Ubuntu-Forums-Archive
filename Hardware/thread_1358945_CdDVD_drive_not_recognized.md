---
title: "Cd/DVD drive not recognized"
date: 2009-12-19
forum: Hardware
---

### Post by flynnofnobles on 2009-12-19
After upgrading from Ubuntu 9.04 my dvd drive/burner is no longer recognized.  Im running a laptop. If I start the computer the drive doesnt even appear.  If i start the computer with a disc in the drive the drive shows up as cdrom0.  However, no cd burner software will let me burn a disc and the disks dont play.  If you click on the cdrom0 it generates an error that states: "special device dev/scd0 does not exist"  Im a total noob with ubuntu, so if someone could give me advice on what steps I should do to narrow down this problem, or if there is a fix, id greatly appreciate it.  Thanks.

---

### Post by x33a on 2009-12-19
please post the output of:
```
sudo lshw -C disk
```
and
```
cat /etc/fstab
```

---

### Post by flynnofnobles on 2009-12-19
[SIZE=2]**lshw -C disk:  **[/SIZE]

*-cdrom                 
       description: DVD-RAM writer
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=open
  *-disk
       description: ATA Disk
       product: ST9120822AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.BH
       serial: 5LZ5F6CK
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=ce5973cb
[SIZE=2][B]
cat /etc/fstab:[/B][/SIZE]

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=b52667ac-98de-446e-b109-4d1145035c90 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2fc8986d-6ef3-457a-ba27-807b1ac0c4c7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by flynnofnobles on 2009-12-19
Bump.

---

### Post by x33a on 2009-12-19
hi, the fstab entry looks ok, but the lshw output doesn't tell about the manufacturer of the drive (i don't know if it makes a difference though).

anyway, while searching the forums i found that adding the option
```
noapic acpi=off
```to the kernel parameters has solved this problem for some people.

try passing this option to grub, before booting. and if it works, you can make permanent change to your grub.cfg file.

---

### Post by flynnofnobles on 2009-12-19
That didn't fix it.  Same exact problem.  Any other suggestions?

---

### Post by flynnofnobles on 2009-12-19
Also, the drive down not work even from boot.  If i put a version of Ubuntu 9.04 in the drive, even with the highest boot priority, it doesnt boot the disk, as if the drive is not seen at all.  It worked for me to install 9.10, but once 9.10 was installed it stopped functioning completely.

---

### Post by flynnofnobles on 2009-12-19
Ok, I after hours of researching and experimenting with declared solutions, Ive found the one that worked for me.  The solution for me was to use

sudo gedit /etc/modules

after the file opens all the way at the bottom add:

libata
ata_piix
piix


Save and reboot, and viola it was fixed.

---

