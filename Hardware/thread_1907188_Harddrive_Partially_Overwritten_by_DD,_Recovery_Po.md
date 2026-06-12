---
title: "Harddrive Partially Overwritten by DD, Recovery Possible?"
date: 2012-01-10
forum: Hardware
---

### Post by japzone on 2012-01-10
I'm an idiot, I was writing an image to a USB drive using dd when instead of typing /dev/sdb I typed /dev/sdd and wrote the 135mb image to my 750gb External Hardrive full of files. Is there ANY possibility of recovering the files or did dd completely zero out the drive? Please help, as this is one of the lowest points of my life EVER.

dd finished writing the 135mb image in 5 seconds, so I didn't have a chance to stop it. By the time I knew what happened it was too late. The command was as follows:
```
sudo dd if=generic.img of=/dev/sdd bs=1M
```
The External Harddrive's filesystem was FAT32(I've had the drive for awhile and FAT32 was the most Universal FS at the time). I also have a 2TB drive I just got which I was planning on moving most of the files to from the 750gb, If needed I can use it to transfer the Recovered files to.

I posted this question on AskUbuntu([*Link*]("http://askubuntu.com/q/94421")) and was advised to use **TestDisk**, however I've been having trouble understanding how to use the Tool(I looked at it's site Wiki and Documentation and couldn't figure out what to do for my problem). If someone could help walk me through the process I'd be very greatful.

---

### Post by Double.J on 2012-01-10
> **japzone said:**
> 
dd finished writing the 135mb image in 5 seconds
Really sorry to hear this has happened - we've all been here at some point.

Good news-ish it's only deleted 135mb of data so far - zero-ing out 750GB would have taken hours. Is the drive unmounted? if not, unmount now - do nothing else at all to the drive - this risks further loss.

Dowload and run the photorec live cd - go through the wiki to get the gist of how to use it. It's the best open source data recovery tech I've used.

I'll be honest right from the off you won't get everything back, and it's always worth running the scan more than once, but given the small amount of damage done, it shouldn't be too bad :)

What ever you do dont try to further edit or write ANYthing to the disk - don't even have it mounted apart from to scan it.

All the best hope it all goes well.

---

### Post by japzone on 2012-01-11
I've tried Photorec but it only recovered 30 files out of the Tens of Thousands I have on the drive. Also the 30 files were just dumped into one folder and not their original folders. Is there anyway to Recover the Files with the Directory Structures still intact?

---

### Post by oldfred on 2012-01-11
Photorec worked well for me but it took hours on a 160GB drive. It cannot recover file names or structures as that is what was erased. Testdisk may be able to recover partition information, but with FAT32 it is even less likely as it is more basic - no journal and file size limits.

Photorec just scans drive looking for anything like a file. It will only then use extension. If drive was highly fragmented it may not be able to do much.

gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Some have recommended Windows tools for Windows files, but they are all paid and do seem to work somewhat better. You can run test recovery for free in some to see if you can get data, but actual restore is what costs.

---

