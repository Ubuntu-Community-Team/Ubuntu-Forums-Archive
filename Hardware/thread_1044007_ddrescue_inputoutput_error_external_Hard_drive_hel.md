---
title: "ddrescue input/output error external Hard drive help!"
date: 2009-01-19
forum: Hardware
---

### Post by strid3r on 2009-01-19
I've been having a load of trouble trying to recover my data from my
external HD.
Background info:
Hard drive: Western Digital 1TB MyBook formatted to NTFS
Problem started when: I think I didn't shut down windows properly or
didn't "Safely Remove Hardware"
I tried force mounting it in Ubuntu and that only made matters worse.

So now I'm stuck trying to get chunks off of it (b/c I don't have an extra 1TB hd laying around) onto an image with
ddrescue

sudo ddrescue -s 32000000000 -d -v /dev/sdb1 /media/disk-1/rescue/backup.img

This finished without any errors.

Output:
    Starting positions: infile = 0 B,  outfile = 0 B
    Copy block size: 128 hard blocks
Hard block size: 512 bytes
Max_retries: 0    
Direct: yes    Sparse: no    Split: yes    Truncate: no

Press Ctrl-C to interrupt
rescued:    32000 MB,  errsize:       0 B,  current rate:   14745 kB/s
   ipos:    31999 MB,   errors:       0,    average rate:   13109 kB/s
   opos:    31999 MB
Finished

But when I try to mount it:
 sudo mount -t ntfs3g /media/disk-1/rescue/backup.img /mnt/

I get this Output:

ntfs_attr_pread: ntfs_pread failed: Input/output error
Failed to read $MFTMirr: Input/output error
Failed to mount '/media/disk-1/rescue/backup.img': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

EDIT: here's what 'dmsg|grep sdb' shows
[ 6501.758524] sd 2:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[ 6501.759551] sd 2:0:0:0: [sdb] Write Protect is off
[ 6501.759555] sd 2:0:0:0: [sdb] Mode Sense: 21 00 00 00
[ 6501.759558] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 6501.760655] sd 2:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[ 6501.761532] sd 2:0:0:0: [sdb] Write Protect is off
[ 6501.761535] sd 2:0:0:0: [sdb] Mode Sense: 21 00 00 00
[ 6501.761537] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 6501.761543]  sdb: sdb1
[ 6501.767269] sd 2:0:0:0: [sdb] Attached SCSI disk
[ 6509.079506] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 6509.079518] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[ 6513.174368] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 6513.174380] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[ 6899.105522] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 6899.105535] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[ 9368.937361] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 9368.937374] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[12330.481570] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
[12330.481584] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[14395.905479] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
[14395.905491] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information


This is along the same thing that it had told me when I tried to force mount the hard drive.
It is irritating the freaking crap out of me, someone please help!

---

### Post by davidynamic on 2010-10-26
Did you ever figure out the solution.

---

