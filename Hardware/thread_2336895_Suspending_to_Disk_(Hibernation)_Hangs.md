---
title: "Suspending to Disk (Hibernation) Hangs"
date: 2016-09-12
forum: Hardware
---

### Post by os2 on 2016-09-12
I am having an issue suspending ram to disk (aka. Hibernating).

I am simply issuing this command to the kernel (4.4, 4.7) as root user:

```

echo disk > /sys/power/state

```

On a freshly booted system this works well for the first time. But if the memory consumption goes up to 30+% say then the system just hangs thereby resulting in having to cold boot.

I have seen this occurring before on previous kernels and other hardware. My Swap partition in all cases is encrypted which is part of a LVM. I wonder if this has any bearing on the issue?

I'm not using any PM-utils type programme nor any other power management utilities for that matter. The swap partition is 2.5x the amount of total ram. Also there isn't any logging information generated in syslog or kern.log.

Any thoughts?

---

### Post by DuckHook on 2016-09-12
You cannot hibernate to an encrypted swap without significant, critical and very convoluted preparation beforehand. What you are doing just won't work. Moreover, the two directories that you must not put on a LVM are /boot and swap. With respect to swap, instructions are as follows:

[https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap](https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap)

---

### Post by os2 on 2016-09-13
Sorry but the process isn't critical, convoluted or significant. The swap partition can be anywhere and in any form really, even part of a LVM. /boot is an unencrypted primary volume.

---

### Post by DuckHook on 2016-09-13
> **os2 said:**
> Sorry but the process isn't critical, convoluted or significant. The swap partition can be anywhere and in any form really, even part of a LVM. /boot is an unencrypted primary volume.We may be posting at cross purposes. A regular swap is indeed easy. OP was, I believe, interested in an encrypted swap, which were the instructions I linked to. For most new users, these are not easy steps and they should be aware of that before starting. Otherwise, better to stick to a simple unencrypted swap. I may be mistaken about swap and LVM but was told in past that encrypted swap needs primary partition. In any case, no need to inject my own opinion. OP can decide for self if process is easy or difficult.

---

### Post by os2 on 2016-09-13
The partition layout is correct and hibernation works in principle but only to an extent. This is the heart of the issue.

I changed the LVM arrangements around and also tried a fully encrypted setup but the issue stands. Namely: when memory consumption is around 30-35%+ the system just hangs when issued with the echo disk > /sys/power/state command. Either the screen freezes along with the input devices or the screen goes blank and stays that way indefinitely.

---

### Post by os2 on 2016-09-13
If we look at a similar issue experienced by this user:

[https://www.reddit.com/r/archlinux/comments/4up2ht/arch_linux_resume_from_hibernation_fails_if_the/](https://www.reddit.com/r/archlinux/comments/4up2ht/arch_linux_resume_from_hibernation_fails_if_the/)

The issue described herein appears to be the antipode of what he's describing. He says under Linux 4.7 this has solved his problem. I am not convinced. I am running Kernel 4.7 as well.

---

### Post by #&amp;thj^% on 2016-09-13
Hmmm? I use Hibernation on Arch and have no problems...but I use zram for swap
```
cat /proc/swaps
Filename                Type        Size    Used    Priority
/dev/sda2                               partition    3145724    0    -1
/dev/zram0                              partition    2097148    0    100

```
If interested in Zram... info here: [http://www.techrapid.co.uk/linux/arch-linux/create-zram-memory-compression-on-arch-linux/](http://www.techrapid.co.uk/linux/arch-linux/create-zram-memory-compression-on-arch-linux/)
And if not kindly disregard.
And I too am using Kernel: x86_64 Linux 4.7.2-1-ARCH.

---

### Post by os2 on 2016-09-15
The machine is one of the new DELLs built around the Skylake platform. I have set Ubuntu up with UEFI. Using Secure Boot or not it's still the same issue. This is what the partition layout looks like:

```

NAME                  MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
nvme0n1               259:0    0 238.5G  0 disk  
&#9500;&#9472;nvme0n1p1           259:1    0   102M  0 part  
&#9500;&#9472;nvme0n1p2           259:2    0  13.8G  0 part  
&#9500;&#9472;nvme0n1p3           259:3    0   244M  0 part  /boot/efi
&#9500;&#9472;nvme0n1p4           259:4    0     1K  0 part  
&#9500;&#9472;nvme0n1p5           259:5    0   243M  0 part  /boot
&#9492;&#9472;nvme0n1p6           259:6    0 224.2G  0 part  
  &#9492;&#9472;nvme0n1p6_crypt   252:0    0 224.2G  0 crypt 
    &#9500;&#9472;debian--vg-swap 252:1    0  22.4G  0 lvm   [SWAP]
    &#9492;&#9472;debian--vg-root 252:2    0 201.8G  0 lvm   /

```

Also:

```

# swapon --summary

Filename                                Type            Size    Used    Priority
/dev/dm-1                               partition       23437308        20      -1

```

---

### Post by os2 on 2016-09-17
I would appreciate any further ideas..

---

### Post by os2 on 2016-09-23
I've been able to narrow this issue down. I reinstalled the entire system without encryption. After running the same test the problem doesn't arise. So this means it has to do with the swap partition which happens to be part of the encrypted container.

---

### Post by os2 on 2016-09-26
I managed to carry out further diagnostics by issuing the following in a standard vanilla kernel:

```

echo platform > /sys/power/pm_test

```

The error reported was "Write error to swap device."

---

### Post by os2 on 2016-09-26
I have now managed to isolate the problem.

I have /tmp set as a tmpfs. The test I was running was to load /tmp withh data such that it populated RAM in excess of 35%. Seems that this was the culprit. In fact you can not use any tmpfs whatsoever with encrypted swap. I think this has been a relatively recent change in the Linux kernel because I don't recall having this issue in many previous iterations of the kernel.

This user asks an interesting question:

[https://bbs.archlinux.org/viewtopic.php?id=191960](https://bbs.archlinux.org/viewtopic.php?id=191960)

Further dialogue on this topic would be appreciated.

---

### Post by os2 on 2016-10-01
In continuing to look at this problem I seem to have managed to suspend to disk even with a tmpfs on the system. My previous conclusion was that this was impossible. There were still issues with that conclusion given an encrypted LUKS swap.

I have now set up a tmpfs. I noticed that /sys/power/image_size which is set by the kernel was set to around 6.6GB. This may well be merited but I have had to set it to 0. In particular I have also use the sync command prior to issuing the hibernate command to make hibernation work.

```

# echo 0 > /sys/power/image_size
# sync
# echo disk > /sys/power/state

```

The issue may or may not be new. Here's one example of the background to the problem:

[https://bugzilla.kernel.org/show_bug.cgi?id=47931](https://bugzilla.kernel.org/show_bug.cgi?id=47931)

---

### Post by os2 on 2016-10-06
I have now realised that there are two flaws in the kernel. One of the major flaws is the way in which the kernel creates a hibernation image. It does this in RAM before scratching the image to disk. At this rate one can potentially only hibernate half the amount of total RAM to disk. This is where the issue lies. As in my case my system tanks out at around 35% of RAM because the system needs the same amount of free RAM to construct the hibernation image. So if you are in principle using anything more than 50% of RAM (35% in my case) then hibernation fails as there is no amount of free RAM available in the system to create a hibernation image.

It's a rather silly bug because the kernel ought to be writing the image to swap as the image is being generated in the free RAM available.

[https://bugzilla.kernel.org/show_bug.cgi?id=176461](https://bugzilla.kernel.org/show_bug.cgi?id=176461)

---

