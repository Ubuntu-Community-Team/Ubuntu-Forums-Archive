---
title: "error mounting drive"
date: 2016-10-16
forum: Hardware
---

### Post by freeworld4 on 2016-10-16
[IMG]http://oi63.tinypic.com/28i9e7r.jpg[/IMG]

sudo ntfsfix /dev/sdb2
[sudo] password for tyler: 
Mounting volume... ntfs_mapping_pairs_decompress() failed: Input/output error
Failed to load $MFT: Input/output error
FAILED
Attempting to correct errors... ntfs_mapping_pairs_decompress() failed: Input/output error
Failed to load $MFT: Input/output error
FAILED
Failed to startup volume: Input/output error
Checking for self-located MFT segment... OK
Unrecoverable error
Volume is corrupt. You should run chkdsk.

How can I do any of what it suggests if I don't have a machine with windows on it?
I tried to make a bootable windows usb stick and also burned a copy of hiren's bootcd and that didn't work either. :(

Lubuntu 16.10
My book Western Digital 4tb drive formatted in ntfs.

---

### Post by T.J. on 2016-10-17
What kind of device is /dev/sdb?  Is it a formatted hard drive or USB stick?

I need more information, please.  Please include the type of hardware, how the drive has been formatted, and what version of Ubuntu you are using.

---

### Post by freeworld4 on 2016-10-17
[COLOR=#000000]Lubuntu 16.10[/COLOR]
[COLOR=#000000]My book Western Digital 4tb hard drive usb 2 formatted in ntfs.[/COLOR]

---

### Post by T.J. on 2016-10-18
> **freeworld4 said:**
> [COLOR=#000000]Lubuntu 16.10[/COLOR]
[COLOR=#000000]My book Western Digital 4tb hard drive usb 2 formatted in ntfs.[/COLOR]

Have you tried a mount command using "ntfs-3g" rather than "ntfs"?  Ntfs-3g is better maintained.

---

### Post by freeworld4 on 2016-10-18
sudo mount -t ntfs-3g /dev/sdb2 /mnt/ntfs/ 
[sudo] password for tyler: 
ntfs_mapping_pairs_decompress() failed: Input/output error
Failed to load $MFT: Input/output error
Failed to mount '/dev/sdb2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

---

### Post by freeworld4 on 2016-10-18
[COLOR=#000000]What do I do now?[/COLOR]

---

### Post by freeworld4 on 2016-10-20
What should I do now?

---

### Post by coldfuzin on 2016-10-21
Do you have a windows install disk laying around? I've used UBCD4WIN before with good results. Lets ya run chkdsk /f which sorts out most issues that aren't from a dying drive.

---

### Post by freeworld4 on 2016-11-06
I installed windows 10 32bit on my old laptop and ran chkdsk -R or it was -r that fixed it. chkdsk -f or -F didn't check anything. It took like two days to fix it but now it works again but some files are missing tho.

---

