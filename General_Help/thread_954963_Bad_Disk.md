---
title: "Bad Disk?"
date: 2008-10-21
forum: General Help
---

### Post by belfasttim on 2008-10-21
Hi-- I tried to install the beta of 8.1 on an extra desktop I had, and almost immediately it started getting very unstable and crashing. I could ctrl-F1 into a prompt, but after typing my username I'd immediately get I/O errors.

I tried dmesg, got output, too long to post since I can't use the machine I got the message on, but it ended with a lot of 

[ 1116.53222 ] end_request: I/O error, dev sda sector xxxxxx
[ 1116.42424 ] Buffer I/O error on device sda1, logical block xxxxx
[ 1116.23324 ] lost page write due to I/O error on sda1
[ 1207.69778 ] sd 2:0:0:0 [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK

Here's the output of fsck:

JDB: Failed to read block at offset 2596 
fsck.ext3: Input/output error while recovering ext3 journal of /dev/sda1

I can't shutdown the machine since it just gives endless strings of I/O errors.

Is this a bad hard drive? Any help diagnosing or fixing this is much appreciated. The machine is running 8.1 beta 64 bit desktop, has two brand new 500 GB HDs in RAID1 configuration. 

Thanks!

---

### Post by phidia on 2008-10-21
Try restarting/shutting down using [this method]("http://txt.binnyva.com/2007/09/reboot-linux-when-hung/")

You could use a live cd to check or try and [repair your filesystem]("https://help.ubuntu.com/community/SystemAdministration/Fsck?highlight=%28e2fsck%29")

---

### Post by belfasttim on 2008-10-21
Thanks Phidia, that shutdown sequence worked, and I was able to reboot. However, then my panel applets started crashing, so I disabled the restricted Nvidia driver. Now when I run dmesg I get this about a hundred times-- 

```
[ 2929.377524] ata5: EH pending after 5 tries, giving up
[ 2929.377532] ata5: EH complete
[ 2930.944022] ata5: EH pending after 5 tries, giving up
[ 2930.944029] ata5: EH complete
[ 2932.508022] ata5: EH pending after 5 tries, giving up
[ 2932.508029] ata5: EH complete
[ 2934.068020] ata5: EH pending after 5 tries, giving up
[ 2934.068026] ata5: EH complete
[ 2935.629521] ata5: EH pending after 5 tries, giving up
[ 2935.629528] ata5: EH complete
[ 2937.189519] ata5: EH pending after 5 tries, giving up
[ 2937.189526] ata5: EH complete
[ 2938.753523] ata5: EH pending after 5 tries, giving up
[ 2938.753530] ata5: EH complete
[ 2940.312019] ata5: EH pending after 5 tries, giving up
[ 2940.312025] ata5: EH complete
[ 2941.876021] ata5: EH pending after 5 tries, giving up
[ 2941.876028] ata5: EH complete
[ 2943.437523] ata5: EH pending after 5 tries, giving up
[ 2943.437529] ata5: EH complete
[ 2944.996018] ata5: EH pending after 5 tries, giving up
[ 2944.996024] ata5: EH complete
[ 2946.556013] ata5: EH pending after 5 tries, giving up
[ 2946.556019] ata5: EH complete
```

Anyone have any clues for me or can I provide more information?

thanks

---

### Post by ghost_ryder35 on 2008-10-21
> **belfasttim said:**
> Hi-- I tried to install the beta of 8.1 on an extra desktop I had, and almost immediately it started getting very unstable and crashing. I could ctrl-F1 into a prompt, but after typing my username I'd immediately get I/O errors.

I tried dmesg, got output, too long to post since I can't use the machine I got the message on, but it ended with a lot of 

[ 1116.53222 ] end_request: I/O error, dev sda sector xxxxxx
[ 1116.42424 ] Buffer I/O error on device sda1, logical block xxxxx
[ 1116.23324 ] lost page write due to I/O error on sda1
[ 1207.69778 ] sd 2:0:0:0 [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK

Here's the output of fsck:

JDB: Failed to read block at offset 2596 
fsck.ext3: Input/output error while recovering ext3 journal of /dev/sda1

I can't shutdown the machine since it just gives endless strings of I/O errors.

Is this a bad hard drive? Any help diagnosing or fixing this is much appreciated. The machine is running 8.1 beta 64 bit desktop, has two brand new 500 GB HDs in RAID1 configuration. 

Thanks!
Make sure your raid configuration is correct.  If it is, then those I/O errors point to dieing hard drive.  You will need to replace it.

---

### Post by belfasttim on 2008-10-21
Ok guys, I disabled RAID, removed the primary drive from the two disk array, and reinstalled 8.1.

Same basic errors. So what's the verdict? Bad motherboard sata controllers?

---

### Post by phidia on 2008-10-22
> **belfasttim said:**
> Ok guys, I disabled RAID, removed the primary drive from the two disk array, and reinstalled 8.1.

Same basic errors. So what's the verdict? Bad motherboard sata controllers?

You're using 8.10? I should have noticed that in the 1st post here. 8.10 is still in development.


Try using 8.04 either live cd or install and see what happens.
A test release is only for those willing to check for and report bugs.

---

### Post by belfasttim on 2008-10-22
Hi Phidia-- yeah, I realize 8.1 is not the ideal platform to be doing troubleshooting on. . .

It seems to have stabilized a bit since I swapped out the old primary disk, so maybe it was just that disk was bad. . .

Thanks for the help.

---

