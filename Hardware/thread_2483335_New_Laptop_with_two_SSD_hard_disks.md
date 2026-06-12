---
title: "New Laptop with two SSD hard disks"
date: 2023-01-27
forum: Hardware
---

### Post by pautorras on 2023-01-27
Hi folks,

After recieve my new lenovo laptop with Windows 11 22H2 and having heavy problems with vmware virtualization, I've decided to install (clean install) Ubuntu (bye bye Windows 11).
As I said, there are two SSD hard disks on my laptop. All needed applications was installed on Ubuntu, like Vmware Workstation Pro,...

The problem is that, if I save my virtual machines on user folder (new folder VM on main HD), virtual machines are running very very well.
Otherwise, if I put the virtual machines in the second hard disk, it works very bad. It seems like hard disk number two it's not mounted by default. When I open Vmware, virtual machines located on second hard disk are unable for vmware. I need to browse on that disk manually and then vmware find the virtual machines stored in the second disk.

Maybe, when virtual machines in second hard disk are running, the bad working issue is for that reason.

What can I do to solve it?

Thanks in advance.

Pau Torras

---

### Post by TheFu on 2023-01-27
A) hard disks aren't mounted.  File systems are mounted.  Typically, the file system is mapped to a partition, but that isn't the only way.
B) You can mount a file system during the boot process by adding 1 line per file system to the /etc/fstab file.
C) Slowness can be related to the performance of the storage, the controller, the interface used.  I've seen systems with 1 NVMe (fast) SSD and with another SATA SSD (5-10x slower).  Also, file-based VMs (vdi/vdmk/qcow2/etc...) will be slower than block-based VM storage.

The model of each SSD can tell you if they are SATA or NVMe with a quick google.  Even SATA SSDs should be fast, but it is possible to have really cheap SSDs with no onboard caching and poor controllers, which can make for an SSD that is slower than a spinning HDD. The models and size for each connected storage device should be shown with inxi.  For example:
```
$ inxi -d
Drives:    HDD Total Size: 1012.2GB (24.1% used)
           ID-1: /dev/sda model: Hitachi_HDP72505 size: 500.1GB
           ID-2: /dev/sdb model: Micron_1100_MTFD size: 512.1GB
           Optical: No optical drives detected.

```
Then google the models.  I know the Hitachi is a spinning SATA HDD and the Micron is a SATA SSD.  If you see nvme in the device filename, that's a good hint that it uses NVMe and should be much faster. For example:
```
$ inxi -d
Drives:    Local Storage: total: 37.13 TiB used: 21.86 TiB (58.9%) 
           ID-1: /dev/**nvme0n1** vendor: Samsung model: SSD 970 EVO 500GB size: 465.76 GiB 
           ID-2: /dev/sda vendor: HGST (Hitachi) model: HUS726T4TALA6L4 size: 3.64 TiB 
```
I also know that Samsung 9xx series are NVMe and Samsung 8xx series are SATA. SATA/SCSI device names will have 'sd' at the start.  IDE device names will start with 'hd'.

---

