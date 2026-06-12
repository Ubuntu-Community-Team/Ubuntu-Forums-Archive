---
title: "External HDD Error ( Unable to Mount )"
date: 2012-02-27
forum: Hardware
---

### Post by Rebel Yellow on 2012-02-27
I've dropped my HDD on the ground by accident while it was plugged in and now I get this message. The weird thing is that I had two partitions : A FAT32 and an NTFS one, and while the former works perfectly fine, the later refuses to mount ( Yes you have guessed, all my important files are on yhe partition that doesn't work properly anymore.).

I don't have windows on my laptop, therefore there is no way for me to verify if the problem persists on another OS. Furthermore since I am new to Ubuntu I don't really kno how to interpret the prompt.

Here is the message I get :

Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read vcn 0x4: Input/output error
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

---

### Post by ahallubuntu on 2012-02-27
Get access to a Windows system and run chkdsk ("error checking") on the NTFS partition and hope the filesystem is intact so you can get most of your files off.  You may be able to do the same by booting a Windows disc (without installing).  I doubt an XP CD would detect an external drive, but a Windows 7 disc might.  Or maybe a Bart PE CD might work - google for more info.

You can also try checking S.M.A.R.T. on the drive (GSmartControl in Ubuntu - install it) to see if any errors have been reported and if so, how severe they are.

Obviously, dropping a hard drive while it is operating is very bad for it and can damage it and you could lose some or all of your data.  But, portable/external drives can be dropped - we are human.  That's why it's crucial to have backup copies of all of your files on a second device.

I personally wouldn't use Windows filesystems for data storage if I didn't have a windows operating system installed for regular use.

---

### Post by Rebel Yellow on 2012-02-27
Thanks for the quick and informative reply. I will have a look at the solutions you mentionned and cross my fingers.

As I stated in my previous post, I am new to Ubuntu so I didn't have the chance yet to get rid of my Windows file systems. If I buy a new external HDD, I will do it the right way this time (However I'm not sure how to format in a Linux file system in the first place.).

---

