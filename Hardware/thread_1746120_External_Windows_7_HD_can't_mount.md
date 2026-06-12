---
title: "External Windows 7 HD can't mount"
date: 2011-05-01
forum: Hardware
---

### Post by agermanucf on 2011-05-01
Hello All,

I have a Toshiba Satellite laptop which I was running W7 on. The HD crapped out, and so I figured when I replaced the HD, I would also replace the OS (had been considering Ubunto for some time). Now I'm on the latest release and am really enjoying it in the few days I have been using it. 

I had a local shop trying to recover the old data for me and transfer it to an external HD I have, but after two days it had only copied 3GB. So I took the old HD from them and said I would just copy it at home, since I needed to get some data ASAP. Now I have the old laptop HD (in an external case), and am trying to mount it via USB, and this is what I'm getting:

**Unable to mount 158 GB Filesystem**

Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


So my question is, now that I am no longer using Windows or have access to another Windows machine, is there a way to run chkdsk from Ubuntu to an external HD?

Thanks in advance!

Andy

p.s as I said, I'm only 2 days into Ubuntu so please bare with me if I ask a stupid question :D

---

