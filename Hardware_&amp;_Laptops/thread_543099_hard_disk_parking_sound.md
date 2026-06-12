---
title: "hard disk parking sound"
date: 2007-09-04
forum: Hardware &amp; Laptops
---

### Post by anantgowerdhan on 2007-09-04
Hi,

I can hear a head parking sound once in a minute in Kubuntu.

Can anybody tell me how to get rid of it? because I tried PCLOS and HDD never sound like that.

For your information I'm using Acer Laptop, with 40GB hdd and 256 mb ram

Regards,
Anant

---

### Post by por100pre1 on 2007-09-04
That could be an issue with the current kernel, [try upgrading the kernel]("http://ubuntuforums.org/showthread.php?t=511974"). **Be sure to backup your files first, just in case it gets messy!**

---

### Post by drpaul on 2007-09-04
Which Ubuntu are you running?
It is a known problem for several versions. I run Edgy and have to boot without AC in order to suppress that problem. Even then sometimes it comes back and I have to reboot with AC unplugged.

HTH

Paul

---

### Post by anantgowerdhan on 2007-09-04
I using Kubuntu 7.04. 

I think its the latest one, Gutsy (7.10) is yet to release, I´ve upgraded the Kernel as well but the problem is still there.

This problem is not there in any other distro, do you see any solution for that?

Regards,
Anant

---

### Post by wieman01 on 2007-09-05
Don't upgrade your kernel or anything like that. A solution ist posted here:

[http://ubuntuforums.org/showthread.php?t=531866]("http://ubuntuforums.org/showthread.php?t=531866")

I am on Kubuntu 7.04 as well and had the same problem... HD spinning up & down very 10 seconds or so. But I was eventually able to resolve it.

If this link does not work for you, simply post there and I'll outline another solution. No problem.

---

### Post by anantgowerdhan on 2007-09-05
Hi Wieman,

Thanks for your reply. I saw your post and seems like you had the same problem. 

You have written a command

> hdparm -B 254 /dev/xxx

where XXX stands for the HDD, I have many partitions so what should I use exactly. Do I need to use the partition where Kubuntu is install?

Regards,
Anant

---

### Post by wieman01 on 2007-09-05
> **anantgowerdhan said:**
> Hi Wieman,

Thanks for your reply. I saw your post and seems like you had the same problem. 

You have written a command



where XXX stands for the HDD, I have many partitions so what should I use exactly. Do I need to use the partition where Kubuntu is install?

Regards,
Anant
Partitions don't really matter. Just use your HD name e.g. "/dev/sda" which stands for your entire HD no matter how many partitions you have on it. See, the 1-digit number indicating the partition ID is left out.

---

