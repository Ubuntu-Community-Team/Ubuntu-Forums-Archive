---
title: "Extreme Unstability in Ubuntu!"
date: 2008-10-18
forum: General Help
---

### Post by linuxisevolution on 2008-10-18
I have been using Ubuntu on this machine for a year now. All went well up until one day when i booted and "fsck has died with exit status 3. Rebooting"
So, I did a fsck /dev/sda1 and answered yes to all. Now, pidgin crashes randomly, nothing will launch, except through wine at times, and sometimes all my programs just lock up! I installed Debian 4 on another partition and I am very happy with it, It never crashes. Unless you guys can help me, I'm gonna switch to Mint/Debian. I will miss the Ubuntu world, but I want to get my work done!

Any help is appreciated. Thanks for all your help in the past, and hopefully, the future.

EDIT: This is what system monitor says about my system: 

winrid-desktop

Releasee 8.03 (hardy)
GNOME 2.22.3

Hardware
  Memory: 3.2GiB
  Processor 0: Intel(R) Core(TM)2 Duo CPU E4500 @ 2.20ghz
  Processor 1: Intel(R) Core(TM)2 Duo CPU E4500 @ 2.20ghz

System Status
 Available disk space:59.5 GiB

---

### Post by bDerrly on 2008-10-18
According to the fsck manpage:

>  The exit code returned by fsck is the sum of the following conditions:
            0    - No errors
            1    - File system errors corrected
            2    - System should be rebooted
...

So your exit code of 3 means that it found errors and corrected them, and the system should be rebooted. I'm assuming you've since rebooted the machine? Did you run fsck manually with the drive unmounted or mounted read-only? Were there errors? Are there other drives that may have been corrupted and also need fsck? What caused this to happen, a power event?

---

### Post by linuxisevolution on 2008-10-18
> **bDerrly said:**
> According to the fsck manpage:



So your exit code of 3 means that it found errors and corrected them, and the system should be rebooted. I'm assuming you've since rebooted the machine? Did you run fsck manually with the drive unmounted or mounted read-only? Were there errors? Are there other drives that may have been corrupted and also need fsck? What caused this to happen, a power event?

I ran fsck when the drive was mounted ( its my root filesystem ) i typed fsck /dev/sda1 . Yes i did it manually.My sister likes to hit the power button instead of shutting down properly. Thanks.

---

### Post by MasterNetra on 2008-10-18
Maybe you should update to 8.04.1 at least instead of being at 8.03 :/

---

### Post by linuxisevolution on 2008-10-18
> **MasterNetra said:**
> Maybe you should update to 8.04.1 at least instead of being at 8.03 :/
that was a typo. I have 8.04.1 :)

---

### Post by gjoellee on 2008-10-18
well there is a lot of issues in Hardy, most of them are fixed in Intrepid thogh

---

### Post by jerome1232 on 2008-10-18
fsck on mounted partition = no no btw. I could've sworn it throws a fat warning at you when you try that.

---

### Post by rustutzman on 2008-10-18
The problem is not your operating system it's your hard drive, Debian works because that partition didn't have a problem. You need to run fsck again unmounted. You probably should save your data reformat that partition and re-install your operating system after fsck is completed. The same would be true with any operating system working on that partition.

Russ

---

### Post by linuxisevolution on 2008-10-18
> **rustutzman said:**
> The problem is not your operating system it's your hard drive, Debian works because that partition didn't have a problem. You need to run fsck again unmounted. You probably should save your data reformat that partition and re-install your operating system after fsck is completed. The same would be true with any operating system working on that partition.

Russ
Thanks for the advice. I see clearly now. I'll boot into debian and run gparted on the other partition. Thanks everyone, an BTW, how do you join too primary partitions?

---

