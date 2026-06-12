---
title: "kernel 2.6.20-16 and drives"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by bowmanr on 2007-05-30
Hi,

Had some issues post the kernel update applied yesterday (looking around, seem some other similar, but not exact) :

1) Suddenly, my 2nd HDD would not mount, in fact, the device entry is missing !!

2) My DVD-Burner has disappeared, and cdrecord --scanbus returns a very rude message.

First, I have solved (1) ... sdb1 had become hdb1. Therefore, a simple modification to /etc/fstab resolved that issue.

However, a solution to (2) has thus far elluded me. The rude message on cdrecord --scanbus is :
```
wodim: No such file or directory.
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup
from
the wodim documentation.
```

I guess I need to load some modules. Any idea please?

I looked at README.ATAPI.setup, but that merely claims with 2.6 kernel, the /dev/sgN entry should exist. 

I did :
```
sudo modprobe sg
```

which returned no error, but also did not create /dev/sg0 which used to exist with 2.6.20-15.

Errrmm??? Is there another module to load?

Thanks for any ideas you can suggest.

Regards
Robert

---

### Post by hardyn on 2007-05-30
this thread has allready been started:

it may not be exactly the same, but seems to have the trends of the previous posts:

[http://ubuntuforums.org/showthread.php?t=456662&page=24](http://ubuntuforums.org/showthread.php?t=456662&page=24)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314)

---

### Post by bowmanr on 2007-05-30
Yes, agreed 100% about previous threads, but .... the other threads are regarding hard disk mounting, an issue which I have resolved (see (1)). Thankfully, I can boot my box post the kernel update.

The question herein (see (2)) is regarding reinstigating /dev/sg0 which, I feel, is reasonably different -- activating the SCSI layer on top of a ATAPI/IDE CD-RW drive (not sure about terminology there). Hence, a new thread. I included the HDD issue incase that information helps trigger a thought process in someone knowledgeable -- not me!! I expect I am wrong in that assertion, linux newbie.

Anyone, please, have any idea about getting a /dev/sgN associated to a DVD-burner?

Thanks for any thoughts,
Regards
Robert

---

### Post by bowmanr on 2007-05-30
BTW, thought best mention ... the DVD-burner still works fine as a reader. There's no problem with reading files of any CD, DVD inserted.
Robert

---

