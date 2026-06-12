---
title: "Hard drive trouble"
date: 2010-06-25
forum: Hardware
---

### Post by bbucsis on 2010-06-25
Hey everyone, needing a bit of help. My parents' computer crashed due to a power surge and now will no longer boot windows. I cannot boot in safe mode or command prompt, and restoring to last known configuration doesn't work. I decided i'd try to help by booting from an ubuntu live cd. When I try to mount their hd I getthis error:

Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

So I looked around on the forums and found a few things. I tried forcing a mount which did not work. I cannot run a chkdsk from windows because windows won't boot and they do not have a cd to which I can boot from like a livecd. So I ran fdisk and got this:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 82.0 GB, 81964302336 bytes
240 heads, 63 sectors/track, 10587 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x55054103

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         646     4883728+  12  Compaq diagnostics
/dev/sda2   *         647       10587    75153960    7  HPFS/NTFS

So I tried an ntfsfix on both sda1 and 2 and got this:

ubuntu@ubuntu:~$ sudo ntfsfix /dev/sda1
Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk

and this:

ubuntu@ubuntu:~$ sudo ntfsfix /dev/sda2
Mounting volume... pread: Input/output error
Failed to calculate number of free clusters: Input/output error.
FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
pread: Input/output error
Failed to calculate number of free clusters: Input/output error.
Remount failed: Input/output error.

sda1 wont even mount. sda2 is getting an I/O error... so I'm wondering, is this hd pooched? I'm trying to recover their business files for them, they don't even care if they have to buy a new computer, they just need some important text files that have business information.

I've tried using r-studio and running an emergency recovery cd but it can't access the drive. I'm thinking it's gone, but I just wanted to see if all the big brains in the ubuntu forums could think of any possible solution.

Thanks in advance,

Bradley

---

### Post by IcarusR on 2010-06-25
First off I suggest you clone the drive in question, so if in the process of trying stuff you fubar it you still have the origional.

Hirens boot cd has a lot of recovery & other useful programs on it. 

[http://www.hirensbootcd.net/download.html?ver=10.5]("http://www.hirensbootcd.net/download.html?ver=10.5")


Never under estimate the importance of backups.

---

### Post by bbucsis on 2010-06-25
Hey IcarusR, thanks for the tip. I know the importance of backup- I backup everything I have :P. Ill clone the drive and try the utility you provided. Ill let you all know if I have any success.

---

### Post by bbucsis on 2010-06-25
IcarusR you're a savior. That program worked perfectly. 3/4 of the harddrive was irrecoverable, but I did get the important files I was looking for, along with some family photos. Whew, I almost had to give up there. Ill keep this cd suite for future trouble. Thanks again!

---

### Post by IcarusR on 2010-06-25
No worries, glad to be of help.

Hirens cd has saved my bacon a couple of times & is worth keeping handy.

---

