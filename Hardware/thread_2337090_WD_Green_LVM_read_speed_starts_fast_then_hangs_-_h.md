---
title: "WD Green LVM read speed starts fast then hangs - how can I diagnose?"
date: 2016-09-14
forum: Hardware
---

### Post by elpedr0 on 2016-09-14
Hi,

I've got a WD Green 2TB drive set up with LVM. Over the past year it has started to hang.

It stores my media while the OS is on another drive, so typically the files stored on this disk are large files. I can recreate the problem by trying to copy a large file (like a 4GB movie) from the drive to another drive. When using Ubuntu's desktop, the copy process starts at around 100MB/s but after about 20 seconds it appears to slow down rapidly and then comes to a stop before a window pops up saying that the file transfer has failed: "Error while copying "suchandsuchfile". There was an error copying the file into "suchandsuchpath". Error splicing file: File too large". The problem also occurs when I use sudo cp in a terminal, which produces the error "File too large".

I seem to be able to copy small files from the drive without a problem. I also seem to be able to copy a 3.5GB directory of many small files successfully, albeit the transfer speed fell to 35MB/s by the end.

I seem to be able to write large files onto the drive at lightning quick speeds of about 220MB/s

There's about 200GB of free space on the drive.

I have recently used wdidle3 to increase the head park time to 300 seconds, but that hasn't had any impact on the problem.

The problem started to appear when the drive was in my headless server (Ubuntu Server 14.04 from memory). Often I'd find that the server had crashed. Sometimes movie playback on a remote client would stop and most often not be recoverable, but very occasionally playback would start up again. When I tried to copy a large file from my server to another machine on the network it would also cause the server to crash.

I put the drive into my desktop (Ubuntu 16.04) with a different SATA cable to see if it was the server hardware. For clarity, I didn't reformat or anything - I just stuck the drive in. But the problem still exists when I try to copy a large file. In the desktop, the OS continues to run even when the copy process fails (unlike the server, where this would cause the server to crash).

I've run the full Western Digital diagnostics scan in a Windows environment and it reports that the drive has passed.

Ultimately I would like to copy my data onto a different drive. And also see if I can solve the problem and keep using the drive.

Any suggestions as to what I should try would be gratefully accepted.

---

### Post by elpedr0 on 2016-09-16
Bump!

Happy to provide any other info if required. Just don't know where to start figuring this out.

---

