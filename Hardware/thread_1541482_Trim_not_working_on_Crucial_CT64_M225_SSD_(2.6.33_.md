---
title: "Trim not working on Crucial CT64_M225 SSD (2.6.33 and 2.6.34 kernels)"
date: 2010-07-29
forum: Hardware
---

### Post by PippoPippo on 2010-07-29
Hi,

I am running Lucid amd64 on a Thinkpad X201T with a Crucial m225, 64GB ssd, firmware 1916. 

Trim, both automatic and manual does not seem to work with either kernel 2.6.33-02063305 or 2.6.34 and hdparm 9.29.

hdparm -I /dev/sda reports (among other stuff)

	   *	Data Set Management TRIM supported
	   *	Deterministic read data after TRIM

which should indicate that the ssd supports trim.

mount reports

/dev/sda5 on / type ext4 (rw,noatime,discard,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,noatime,mode=1777)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
tmpfs on /var/tmp type tmpfs (rw,noatime,mode=1777)
/dev/sda2 on /media/Windows7_OS type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

I have followed these instructions 
[http://go.overclockers.com/?id=1132X509988&xs=1&url=http%3A%2F%2Fforums.gentoo.org%2Fviewtopic-t-812509.html&sref=http%3A%2F%2Fwww.overclockers.com%2Fforums%2Fshowthread.php%3Ft%3D647868](http://go.overclockers.com/?id=1132X509988&xs=1&url=http%3A%2F%2Fforums.gentoo.org%2Fviewtopic-t-812509.html&sref=http%3A%2F%2Fwww.overclockers.com%2Fforums%2Fshowthread.php%3Ft%3D647868) 

to verify whether trim is working. The sector examined stays unchanged. The same if I execute

sudo hdparm --please-destroy-my-drive --trim-sector-ranges 88322304:1 /dev/sda

where 88322304 is the sector LBA detected with the previous method.

If I run wiper v2.7 it reports e.g.

Creating temporary file (7284725 KB).. 
Syncing disks.. 
Beginning TRIM operations..

/dev/sda:
trimming 3817471 sectors from 64 ranges
succeeded
trimming 3833856 sectors from 64 ranges
succeeded
trimming 3866625 sectors from 64 ranges
succeeded
trimming 2277376 sectors from 64 ranges
succeeded
trimming 774128 sectors from 18 ranges
succeeded
Removing temporary file..
Syncing disks.. 
Done.

but the sector in question remain intact, even after a reboot.

I am stumped.

Any help most appreciated.

giulio

---

### Post by PippoPippo on 2010-07-29
bump

---

### Post by Celoxocis on 2010-10-08
yes im having the same issue but with an super talent SSD

Model Number:       STT_FTM16GL25V
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    DOWNLOAD_MICROCODE
                SET_MAX security extension
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART self-test
           *    General Purpose Logging feature set
           *    Gen1 signaling speed (1.5Gb/s)
           *    Gen2 signaling speed (3.0Gb/s)
           *    Native Command Queueing (NCQ)
           *    Phy event counters
                DMA Setup Auto-Activate optimization
           *    Software settings preservation
           *    Data Set Management indeterminate TRIM supported

running ext4 with "discard" in fstab.
verified with this test

[http://forums.gentoo.org/viewtopic-t-812509.html](http://forums.gentoo.org/viewtopic-t-812509.html)

---

