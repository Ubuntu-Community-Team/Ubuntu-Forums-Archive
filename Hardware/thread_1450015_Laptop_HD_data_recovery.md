---
title: "Laptop HD data recovery"
date: 2010-04-08
forum: Hardware
---

### Post by K3l3v on 2010-04-08
My laptop HD died a couple of days ago (on the same day that both of my HDs in the desktop died - not my week). I was dual booting windoze and Ubuntu on the laptop. So far, I have had no problem seeing/copying/transfering all the files from the Ubuntu partition.

But... I have not been able to access the windoze partition since the hd died. I have the disk mounted in an 'externalizer'. The partition resides at /dev/sdc1 on my machine. When I attempt to mount the ntfs partition, I get:


ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

After following the instructions listed [here]("http://www.arsgeek.com/2006/09/25/ubuntu-tricks-how-to-mount-your-windows-partition-and-make-it-readwritable/"), I get the following error (at least it's different from before...):

pread: Input/output error
Failed to calculate number of free clusters: Input/output error.
Failed to mount '/dev/sdc1': Input/output error.
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
made to NTFS by this software.
Mount failed.

I know the drive is D-E-D, dead. I have a couple of files I'd like to recover (I know... backup, backup, backup). Any help would be appreciated.

---

### Post by ajgreeny on 2010-04-08
If the NTFS partition was mounted when the laptop died, it will appear to still be in use, as far as any linux distro is concerned, and will have to be force mounted.

---

### Post by K3l3v on 2010-04-09
Update...

So I tried to use dd-rescue as per [this]("http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html") tutorial. Got an image successfully made (I think), but when I tried to fsck the *.img file as instructed, I get this error message:

$ sudo fsck -y [Path to img file]/windoze.img 

fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open windoze.img

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

Hmmm...  looks like fsck is looking for an ext file system. Did some digging and looks like fsck does not work with ntfs file systems.

Tried [this]("http://www.linuxjournal.com/article/8661#comment-126648") with no dice. Also tried ntfsresize and gparted. Also no luck. Any helpful comments/suggestions would be appreciated.

Thank you.

---

### Post by srs5694 on 2010-04-09
To fix it, you *must* use Windows. AFAIK, no Linux utility can really fix NTFS problems; at best, ntfsfix does very minor checks and then marks the disk for further checking by CHKDSK in Windows.

That said, if you just want to recover files from the disk, you may be able to do so using ntfscp (check its man page for details; also check ntfsls).

---

