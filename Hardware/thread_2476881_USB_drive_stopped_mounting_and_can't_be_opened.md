---
title: "USB drive stopped mounting and can't be opened"
date: 2022-07-10
forum: Hardware
---

### Post by smith73 on 2022-07-10
There's 5TB Seagate portable USB hard drive and ~a year ago notifications for its operations stopped
appearing in the task bar, but it was still functional and had a desktop icon upon plugging in.
Though after "Safely remove drive", its led indicator often was still blinking.
Recently upon copying relatively large amounts of data into it, it took ~1 hour to copy 
~60GB, then upon copying ~7GB it began to slow down showing 2hour left.
So I disconnected it and reconnected several times. Then it began to fail mounting.
(I also tried it on old Windows 8, which didin't even recognize it name)

Here's syslog exerpt:

```
Jul 10 22:37:24 amts kernel: [ 5517.419929] usb 2-2: new SuperSpeed Gen 1 USB device number 5 using xhci_hcd
Jul 10 22:37:24 amts kernel: [ 5517.440735] usb 2-2: New USB device found, idVendor=0bc2, idProduct=aa14, bcdDevice= 0.00
Jul 10 22:37:24 amts kernel: [ 5517.440744] usb 2-2: New USB device strings: Mfr=2, Product=3, SerialNumber=1
Jul 10 22:37:24 amts kernel: [ 5517.440749] usb 2-2: Product: Basic
Jul 10 22:37:24 amts kernel: [ 5517.440753] usb 2-2: Manufacturer: Seagate
Jul 10 22:37:24 amts kernel: [ 5517.440758] usb 2-2: SerialNumber: 00000000NABC3S05
Jul 10 22:37:24 amts kernel: [ 5517.446051] scsi host3: uas
Jul 10 22:37:24 amts kernel: [ 5517.446946] scsi 3:0:0:0: Direct-Access     Seagate  Basic            9340 PQ: 0 ANSI: 6
Jul 10 22:37:24 amts kernel: [ 5517.448133] sd 3:0:0:0: Attached scsi generic sg2 type 0
Jul 10 22:37:24 amts kernel: [ 5517.448633] sd 3:0:0:0: [sdb] Spinning up disk...
Jul 10 22:37:24 amts mtp-probe: checking bus 2, device 5: "/sys/devices/pci0000:00/0000:00:14.0/usb2/2-2"
Jul 10 22:37:24 amts mtp-probe: bus: 2, device: 5 was not an MTP device
Jul 10 22:37:25 amts mtp-probe: checking bus 2, device 5: "/sys/devices/pci0000:00/0000:00:14.0/usb2/2-2"
Jul 10 22:37:25 amts mtp-probe: bus: 2, device: 5 was not an MTP device
Jul 10 22:37:32 amts kernel: [ 5518.475384] .......ready
Jul 10 22:37:32 amts kernel: [ 5524.620728] sd 3:0:0:0: [sdb] 9767541167 512-byte logical blocks: (5.00 TB/4.55 TiB)
Jul 10 22:37:32 amts kernel: [ 5524.762240] sd 3:0:0:0: [sdb] Write Protect is off
Jul 10 22:37:32 amts kernel: [ 5524.762249] sd 3:0:0:0: [sdb] Mode Sense: 4f 00 00 00
Jul 10 22:37:32 amts kernel: [ 5524.762436] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 10 22:37:32 amts kernel: [ 5524.762688] sd 3:0:0:0: [sdb] Optimal transfer size 33553920 bytes
Jul 10 22:37:32 amts kernel: [ 5524.865246]  sdb: sdb1 sdb2
Jul 10 22:37:32 amts kernel: [ 5524.892819] sd 3:0:0:0: [sdb] Attached SCSI disk
Jul 10 22:37:33 amts udisksd[18569]: $MFTMirr does not match $MFT (record 0).
Jul 10 22:37:33 amts udisksd[18569]: Failed to mount '/dev/sdb2': Input/output error
Jul 10 22:37:33 amts udisksd[18569]: NTFS is either inconsistent, or there is a hardware fault, or it's a
Jul 10 22:37:33 amts udisksd[18569]: SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
Jul 10 22:37:33 amts udisksd[18569]: then reboot into Windows twice. The usage of the /f parameter is very
Jul 10 22:37:33 amts udisksd[18569]: important! If the device is a SoftRAID/FakeRAID then first activate
Jul 10 22:37:33 amts udisksd[18569]: it and mount a different device under the /dev/mapper/ directory, (e.g.
Jul 10 22:37:33 amts udisksd[18569]: /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
Jul 10 22:37:33 amts udisksd[18569]: for more details.
Jul 10 22:37:51 amts udisksd[18594]: $MFTMirr does not match $MFT (record 0).
Jul 10 22:37:51 amts udisksd[18594]: Failed to mount '/dev/sdb2': Input/output error
Jul 10 22:37:51 amts udisksd[18594]: NTFS is either inconsistent, or there is a hardware fault, or it's a
Jul 10 22:37:51 amts udisksd[18594]: SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
Jul 10 22:37:51 amts udisksd[18594]: then reboot into Windows twice. The usage of the /f parameter is very
Jul 10 22:37:51 amts udisksd[18594]: important! If the device is a SoftRAID/FakeRAID then first activate
Jul 10 22:37:51 amts udisksd[18594]: it and mount a different device under the /dev/mapper/ directory, (e.g.
Jul 10 22:37:51 amts udisksd[18594]: /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
Jul 10 22:37:51 amts udisksd[18594]: for more details.

```

Also another 2TB brand new USB drive began to drastically slow down upon copying data into it even via USB 3
connection.
And in all these cases memory usage jumped to 2% free memory (from 8GB total).

I cleaned the USB ports with isopropyl alcohol, but it seemed to not matter. I was preparing for
thermal paste replacement and cleaning of the cooler fan etc on this laptop.

Also on both USB disks I did not use any preformatting for file systems, just plugged them in
and copied files.

What can be done to optimally restore or remount the 5TB Seagate USB drive??? (at least to get it be opened and copy files,
even at low speeds)

I'd be eternally grateful, informationally and otherways

---

### Post by smith73 on 2022-07-11
I checked the filesystems on both USB drives via *sudo fdisk -l *and here the output:

For 5TB drive (which is failing to be mounted and can't be opened):
```
Disk /dev/sdb: 4.56 TiB, 5000981077504 bytes, 9767541167 sectors
Disk model: Basic           
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 2C22E4B2-0227-46E7-B654-E992A9E99830

Device      Start        End    Sectors  Size Type
/dev/sdb1      34     262177     262144  128M Microsoft reserved
/dev/sdb2  264192 9767540735 9767276544  4.6T Microsoft basic data

Partition 1 does not start on physical sector boundary.

```

For 2TB USB drive (which functional, but is copying slowly):
```
Disk /dev/sdb: 1.84 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: Transcend       
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf21ebc23

Device     Boot Start        End    Sectors  Size Id Type
/dev/sdb1  *     2048 3907026943 3907024896  1.8T  7 HPFS/NTFS/exFAT
```

As suggested here [1] a command *ntfsfix* from *ntfs-3g* can be used to fix the NTFS file
system. I have libntfs-3g883 and ntfs-3g installed automatically on Ubuntu 20.04.
But as *fdisk -l *shows*, *the file system in this 5TB USB drive is gpt.

And here [2] it is mentioned that this ntfs util can damage your file systems or hard disk.

I almost never used this disk on WIndows, but didn't format it before usage, and it came
with some Windows disk utils in several folders, which I never used.

I can try to format the 2TB disk, but [B]what can be done to safely and optimally 
recover the mounting of the 5TB disk[/B]?
I have several fresh 32/64GB USB disks to probe first if the utility is safe, but it's cumbersome,
as the same error will be required to reproduce on these empty USB disks.

Or can I backup-copy the 1TB of data from this 5TB disk while it's failing to mount
directly to another USB drive via terminal, and try these ntfs fixes afterwards?

[1]https://unix.stackexchange.com/questions/440841/ntfs-mftmirr-does-not-match-mft
[2] [https://askubuntu.com/questions/727218/cannot-mount-usb-stick-errors-out-with-mftmirr-does-not-match-mft](https://askubuntu.com/questions/727218/cannot-mount-usb-stick-errors-out-with-mftmirr-does-not-match-mft)

---

### Post by yancek on 2022-07-11
> But as *fdisk -l *shows*, *the file system in this 5TB USB drive is gpt 

GPT is a standard for layout of partition tables (explained at the link below) and not a filesystem type.

[https://en.wikipedia.org/wiki/GUID_Partition_Table](https://en.wikipedia.org/wiki/GUID_Partition_Table)

Your problems are on windows filesystems and ntfsfix and such software has very limited capability to fix them.  If you're using windows filesystems, you will likely need to repair them with windows tools such as chkdsk.

---

### Post by smith73 on 2022-07-11
The unupdated, cracked and probably infected Windows 8 I have currently (check disk util)
 can't access the disk (at least in GUI).

Here [1] it is mentioned that *sudo ntfsfix /dev/sdb1 *fixed the problem.

[1] [https://unix.stackexchange.com/questions/440841/ntfs-mftmirr-does-not-match-mft](https://unix.stackexchange.com/questions/440841/ntfs-mftmirr-does-not-match-mft)

[SIZE=1]Maybe Github Copilot alternatives [2] could be used to generate Windows functionality for 
necessary utils
[2] [https://alternativeto.net/software/github-copilot/](https://alternativeto.net/software/github-copilot/)[/SIZE]

---

