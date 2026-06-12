---
title: "unable to mount Seagate freeagent 2TB USB hard drive"
date: 2011-06-23
forum: Hardware
---

### Post by brianthefolksinger on 2011-06-23
Have found many posts on this issue, no solutions work or match just what I get, maybe my experience will help figure it out.

failed with this error: repeating endlessly, as it kept trying endlessly

Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

disk utility could see drive as /dev/sdc1 and had specs, can't check or format though shows volume.. Gparted cant act on it, will try and fail with same message above

edited ftstab to add
/dev/sdc1	/media/E-1	ntfs	defaults	0 0 2

didn't add a ID number line

then ran 
sudo mkdir /media/E-1
sudo chown -R brian:brian /media/E-1

retry
now error message
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdc1 on /media/Ext-1

tried sudo mount /media/E-1
got first error message again
then second on top of that

reboot, splashscreen message to S skip mount of media/E-1 or M manual, pick S
try disk utility
can check the disk, is clean, 
but not mount
can safe remove

tried mount dev/sdc1 /media/E-1
error only root can do that
sudo mount says special device does not exist

comment out fstab line, back to beginning
and disk utilty can't remove
uncomment fstab line and back to can't mount.. "not root" error exit code 1
also in term, same
fdisk sees disk and ids
disk utility works, can safely remove.

tried
sudo mount -t ntfs-3g /dev/sdb1 /media/external (from "mount/USB" thread)


get exit code 13 message in terminal then
Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)
outside terminal in error box

change fstab line to
ntfs-3g defaults,user,locale=en_US.utf8 0 0
nope, back to beginning
back to as before and comment out for now

hooked up to Windows machine (had to find one) only Windows I run is W98 for legacy. All Linux since then.
but in XP it mounted fine, all there, ran checkdisk, no problems, disconnected normal.

back to linux machine, error code 13 still,
uncomment fstab (using original line), changes to error code 1 again, but can use disk utility to safely remove drive

oh used the sudo nautilus to delete the dir I created in case it was getting in the way.. though seems the problem is something else all together. Anyway, should plug and play like other USB drives."should" oh well.

? Expect I missed something simple and as I still don't really understand how it all works under the hood.. perhaps a chmod on the directory if I use fstab, or the fstab line..though seems I shouldn't need it as a usb device. Though it seems to help. or maybe the chown command I used was wrong, for a usb device? 
will try the power down issue using windows, as suggested, tho they didn't say what to do, set standby to "0"? still not sure what I am supposed to adjust to what. power saving mode to "never" I think, and keep trying.. but thought I'd post this in case.

---

### Post by oldfred on 2011-06-24
You changed ownership of your mount to you. It is saying it must be root.

this is my shared NTFS mounted from fstab (it is linked from /mnt):

fred@fred-MavericDT:~$ ls -l sh*
lrwxrwxrwx 1 root root 11 2010-11-04 19:26 shared -> /mnt/shared

my fstab entry:
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657 /mnt/shared ntfs-3g defaults 0 0

---

### Post by brianthefolksinger on 2011-06-24
I used sudo nautilus to erase all the folders I made there.
do I need to do anything else to clear out possible commands?

ok, don;t understand the middle part,
red@fred-MavericDT:~$ ls -l sh*
lrwxrwxrwx 1 root root 11 2010-11-04 19:26 shared -> /mnt/shared

do I need to create this or is this auto when something is plugged in
and usb is mounted in /mnt/shared not /media/whatever?

try to find the UUID for fstab though only have the drive and shows as sdc1

might be that this computer only has USB 1.1, not 2.0?
lsusb shows drive
lsusb -v shows everything

odd bit more strange, tried plugging the seagate into a laptop running same LTS ubuntu and it popped right up no problem, so problem is specific to this computer, setup, or installation. Am using a USB hub on this computer. The other is a laptop and I plugged in direct. that make me think of checking above, laptop is newer with USB 2.0
 Try that here and don't get anything. will try again.
Also did use windows to set the lowpower mode to never on the drive.

---

### Post by oldfred on 2011-06-24
I think you need to change Brian back to root.

then ran 
sudo mkdir /media/E-1
sudo chown -R brian:brian /media/E-1

Your mount of /media/E-1 is ok. It is just equivalent to my mount of /mnt/shared.  Advantages & disadvantages of either. A /mnt does not show twice in Nautilus, but you either have to link like I do or search in / for /mnt to find your files.

---

### Post by brianthefolksinger on 2011-06-25
tried many things
deleted directories in /media made before
made new without using chown
did do chmod 777

no luck

ntsf-config wasn't installed, so did that, and used it to add external drives! thought I had it. but no luck there

checked user permissions and external drives are checked/allowed

even installed mountmanager didn't do anything  and crashed
though it got rid of /dev/sdc1 line in my fstab file, had to rewrite that to stop constant error 13 messages
present fstab
 /dev/sdc1 /media/usb-Seagate ntfs-3g defaults 0 0
but get error 1 message if I try mounting from disk utility or places

have gone through wiki on mount and usb mount trying suggested steps

tried sudo mount -t ntfs-3g /dev/sdc1/ /media/usb-Seagate
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

 and then error 1 window pops up outside the terminal (as before)

though don't understand output, here's
dmesg:

[ 3959.996260] usb 1-2: new full speed USB device using uhci_hcd and address 68
[ 3960.159610] usb 1-2: configuration #1 chosen from 1 choice
[ 3960.163332] hub 1-2:1.0: USB hub found
[ 3960.165154] hub 1-2:1.0: 4 ports detected
[ 3960.458142] usb 1-2.4: new full speed USB device using uhci_hcd and address 69
[ 3960.682968] usb 1-2.4: configuration #1 chosen from 1 choice
[ 3960.696419] scsi35 : SCSI emulation for USB Mass Storage devices
[ 3960.701070] usb-storage: device found at 69
[ 3960.701081] usb-storage: waiting for device to settle before scanning
[ 3965.701442] usb-storage: device scan complete
[ 3965.704990] scsi 35:0:0:0: Direct-Access     Seagate  FA GoFlex Desk   0D0B PQ: 0 ANSI: 0
[ 3965.710172] sd 35:0:0:0: Attached scsi generic sg3 type 0
[ 3965.715251] sd 35:0:0:0: [sdc] 3907029167 512-byte logical blocks: (2.00 TB/1.81 TiB)
[ 3965.720265] sd 35:0:0:0: [sdc] Write Protect is off
[ 3965.720281] sd 35:0:0:0: [sdc] Mode Sense: 0f 00 00 00
[ 3965.720291] sd 35:0:0:0: [sdc] Assuming drive cache: write through
[ 3965.751128] sd 35:0:0:0: [sdc] Assuming drive cache: write through
[ 3965.751164]  sdc: sdc1
[ 3965.797388] sd 35:0:0:0: [sdc] Assuming drive cache: write through
[ 3965.797421] sd 35:0:0:0: [sdc] Attached SCSI disk
[ 3966.384133] sd 35:0:0:0: [sdc] Sense Key : Recovered Error [current] [descriptor]
[ 3966.384163] Descriptor sense data with sense descriptors (in hex):
[ 3966.384173]         72 01 04 1d 00 00 00 0a 09 0c 00 00 00 00 00 07 
[ 3966.384203]         00 00 
[ 3966.384213] sd 35:0:0:0: [sdc] ASC=0x4 ASCQ=0x1d
[ 3996.959033] sd 35:0:0:0: [sdc] Sense Key : Recovered Error [current] [descriptor]
[ 3996.959065] Descriptor sense data with sense descriptors (in hex):
[ 3996.959074]         72 01 04 1d 00 00 00 0e 09 0c 00 00 00 00 00 07 
[ 3996.959105]         00 00 00 00 40 50 
[ 3996.959121] sd 35:0:0:0: [sdc] ASC=0x4 ASCQ=0x1d
[ 3997.054992] sd 35:0:0:0: [sdc] Sense Key : Recovered Error [current] [descriptor]
[ 3997.055025] Descriptor sense data with sense descriptors (in hex):
[ 3997.055033]         72 01 04 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
[ 3997.055063]         00 4f 00 c2 40 50 
[ 3997.055080] sd 35:0:0:0: [sdc] ASC=0x4 ASCQ=0x1d
[ 4380.473070] hub 1-2:1.0: cannot reset port 4 (err = -71)
[ 4380.474042] hub 1-2:1.0: cannot reset port 4 (err = -71)
[ 4380.475039] hub 1-2:1.0: cannot reset port 4 (err = -71)
[ 4380.477262] hub 1-2:1.0: cannot reset port 4 (err = -71)
[ 4380.478079] hub 1-2:1.0: cannot reset port 4 (err = -71)
[ 4380.478089] hub 1-2:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 4380.479039] hub 1-2:1.0: cannot disable port 4 (err = -71)
[ 4380.480094] hub 1-2:1.0: cannot reset port 4 (err = -71)
[ 4380.481053] hub 1-2:1.0: cannot reset port 4 (err = -71)
[ 4380.482037] hub 1-2:1.0: cannot reset port 4 (err = -71)
[ 4380.483038] hub 1-2:1.0: cannot reset port 4 (err = -71)
[ 4380.484068] hub 1-2:1.0: cannot reset port 4 (err = -71)
[ 4380.484077] hub 1-2:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 4380.485059] hub 1-2:1.0: cannot disable port 4 (err = -71)
[ 4380.486038] hub 1-2:1.0: cannot reset port 4 (err = -71)
[ 4380.487036] hub 1-2:1.0: cannot reset port 4 (err = -71)
[ 4380.488073] hub 1-2:1.0: cannot reset port 4 (err = -71)
[ 4380.489048] hub 1-2:1.0: cannot reset port 4 (err = -71)
[ 4380.490035] hub 1-2:1.0: cannot reset port 4 (err = -71)
[ 4380.490044] hub 1-2:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 4380.491036] hub 1-2:1.0: cannot disable port 4 (err = -71)
[ 4380.492068] hub 1-2:1.0: cannot reset port 4 (err = -71)
[ 4380.493051] hub 1-2:1.0: cannot reset port 4 (err = -71)
[ 4380.494035] hub 1-2:1.0: cannot reset port 4 (err = -71)
[ 4380.495035] hub 1-2:1.0: cannot reset port 4 (err = -71)
[ 4380.496066] hub 1-2:1.0: cannot reset port 4 (err = -71)
[ 4380.496076] hub 1-2:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 4380.497055] hub 1-2:1.0: cannot disable port 4 (err = -71)
[ 4380.498034] hub 1-2:1.0: cannot disable port 4 (err = -71)
[ 4380.498389] sd 35:0:0:0: [sdc] Unhandled error code
[ 4380.498399] sd 35:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 4380.498414] sd 35:0:0:0: [sdc] CDB: Read(10): 28 00 74 71 08 87 00 00 80 00
[ 4380.498445] end_request: I/O error, dev sdc, sector 1953564807
[ 4380.498461] __ratelimit: 382 callbacks suppressed
[ 4380.498473] Buffer I/O error on device sdc1, logical block 1953564744
[ 4380.498488] Buffer I/O error on device sdc1, logical block 1953564745
[ 4380.498500] Buffer I/O error on device sdc1, logical block 1953564746
[ 4380.498511] Buffer I/O error on device sdc1, logical block 1953564747
[ 4380.498521] Buffer I/O error on device sdc1, logical block 1953564748
[ 4380.498532] Buffer I/O error on device sdc1, logical block 1953564749
[ 4380.498542] Buffer I/O error on device sdc1, logical block 1953564750
[ 4380.498553] Buffer I/O error on device sdc1, logical block 1953564751
[ 4380.498575] Buffer I/O error on device sdc1, logical block 1953564752
[ 4380.498587] Buffer I/O error on device sdc1, logical block 1953564753
[ 4380.499053] hub 1-2:1.0: hub_port_status failed (err = -71)
[ 4380.499220] sd 35:0:0:0: [sdc] Unhandled error code
[ 4380.499228] sd 35:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 4380.499239] sd 35:0:0:0: [sdc] CDB: Read(10): 28 00 74 71 09 07 00 00 80 00
[ 4380.499267] end_request: I/O error, dev sdc, sector 1953564935
[ 4380.499746] sd 35:0:0:0: [sdc] Unhandled error code
[ 4380.499755] sd 35:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 4380.499767] sd 35:0:0:0: [sdc] CDB: Read(10): 28 00 74 71 09 87 00 00 80 00
[ 4380.499794] end_request: I/O error, dev sdc, sector 1953565063
[ 4380.500793] sd 35:0:0:0: [sdc] Unhandled error code
[ 4380.500806] sd 35:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 4380.500817] sd 35:0:0:0: [sdc] CDB: Read(10): 28 00 74 71 0a 07 00 00 80 00
[ 4380.500844] end_request: I/O error, dev sdc, sector 1953565191
[ 4380.502146] sd 35:0:0:0: [sdc] Unhandled error code
[ 4380.502158] sd 35:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 4380.502170] sd 35:0:0:0: [sdc] CDB: Read(10): 28 00 74 71 08 87 00 00 08 00
[ 4380.502197] end_request: I/O error, dev sdc, sector 1953564807
[ 4380.592301] hub 1-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[ 4380.592330] usb 1-2: USB disconnect, address 68
[ 4380.592339] usb 1-2.4: USB disconnect, address 69

maybe it has to do with the usb hub still, since it works fine on the ubuntu laptop. too tired, been trying different things for hours, take a break. eat.

---

### Post by oldfred on 2011-06-25
Have you tried chkdsk on the drive. Ubuntu does not mount NTFS partitions that it sees need chkdsk to prevent damage that chkdsk may not then be able to fix.

I was able to boot my XP, but when using gparted on my PC it would not even see the sda drive at all. Then I ran chkdsk and then gparted worked just fine. XP never saw the error, but Ubuntu did.

If a large drive chkdsk can take a very long time and you have to rerun it until there are no errors as it does not fix everything on one pass.

chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by brianthefolksinger on 2011-06-26
At this point I think the problem is hardware vs software, though don;t know enough except to guess

reasons
drive is usb 3.0/2.0
drive works fine on laptop (usb 2.0) either in XP or in linux (same install as on desktop), run check disk multiple times, no problems found.

desktop is old (I run linux because it runs on old machines) and has usb 1 on the MB looks like, if I plug the drive in back there I get nothing, can't find the drive on fdisk or lsusb, no response anywhere. The hub is a 2.0 but is 1 "compliant", but something must not translate as I still have all the problems as above.. have to fstab and still can't mount.

think I'll have to get a different drive that is usb 2 or firewire (have a firewire card installed) or a usb 3.0 pci card maybe.. am trying to upgrade, that's why  want to load the old PCs data onto a external drive, easy to shift to a newer computer. oh well

---

### Post by oldfred on 2011-06-26
Most computers that are so old to have just USB1 ports are not a  bootable USB port. Only computers in about the last 4 to 5 years started to have bootable USB 2.0 ports. And right now many USB 3 ports do not seem to be bootable.

---

### Post by brianthefolksinger on 2011-07-04
So! it was a hardware problem. 
I bought an Ultra USB 2.0-firewire port PCI card and installed it, replacing my firewire PCI card and it worked, the drive appears on the desktop and I can get into it, just like the laptop.

I haven't tried doing anything but think it won;t be a problem. So I assume the problem was the usb ports on this old computer are 1.0, and thouhg I have a 2.o hub plugged into it, something isn't quite right, so I could do everything but mount the drive.

So don't know why, for certian, but problem solved. Good enough.

---

