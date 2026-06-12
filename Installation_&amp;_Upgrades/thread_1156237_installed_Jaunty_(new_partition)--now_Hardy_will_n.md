---
title: "installed Jaunty (new partition)--now Hardy will not boot"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2009-05-11
I wanted to keep my Hardy installation and install Jaunty on a separate partition. I did this, and Jaunty boots up, but Hardy will no longer boot up.

I looked in /boot/grub/menu.lst and I noticed that the Jaunty install changed _all_ the menu entries from "Ubuntu 8.04.2" to "Ubuntu 9.04".

The new entries look like this:
```

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        snip-uuid-27_27
kernel        /vmlinuz-2.6.28-11-generic root=/dev/mapper/vg2-lvJauntyRoot_crypt ro quiet splash 
initrd        /initrd.img-2.6.28-11-generic
quiet
```Obviously, that's OK for Jaunty, but not for Hardy. So I carefully changed the entries for the older kernels back to the way they were before:

```
title        Ubuntu 8.04.2, kernel 2.6.24-24-generic
uuid        snip-uuid-27_27
kernel        /vmlinuz-2.6.24-24-generic /dev/mapper/vg1-lvHardyRoot ro quiet splash 
initrd        /initrd.img-2.6.24-24-generic
quiet
```But I still cannot get Hardy to boot. What else do I need to do?

I'm attaching a boot_info_script obtained while booted into Jaunty.

FYI, here is an explanation of my partitions:
```
/dev/sda1                  63    61,448,624    61,448,562  8e Linux LVM
/dev/sda2    *     61,448,625    61,834,184       385,560  83 Linux
/dev/sda3          61,834,185   120,423,239    58,589,055  83 Linux
/dev/sda4         120,423,240   293,041,664   172,618,425  83 Linux
```sda1 is Jaunty. It works.
sda2 is /boot (unencrypted, of course)
sda3 is Hardy (encrypted) - worked before installing Jaunty, boots from sda2
sda4 is just some data (mounted in Hardy) (encrypted)

P.S. Jaunty is partitioned with LVM first and then crypto inside LVM.
Hardy was partitioned with crypto first and LVM inside that.

P.P.S. Here was my original thread on this subject.
[http://ubuntuforums.org/showthread.php?t=1108613](http://ubuntuforums.org/showthread.php?t=1108613)
It took me a long time to solve the installation problem, but I solved that here:
[http://ubuntuforums.org/showthread.php?t=1144086](http://ubuntuforums.org/showthread.php?t=1144086)

---

### Post by lvleph on 2009-05-11
It looks like you are trying ot use the wrong partition for the kernel you are trying to use.

EDIT: Use blkid to find the proper uuid for the hardy partition, and then fix that. But maybe I am wrong since I have never used a separate boot partition.

---

### Post by MountainX on 2009-05-11
> **lvleph said:**
> It looks like you are trying ot use the wrong partition for the kernel you are trying to use.

EDIT: Use blkid to find the proper uuid for the hardy partition, and then fix that. But maybe I am wrong since I have never used a separate boot partition.

The UUID is for the boot partition, and I think it is correct (see below for why).
The entries for the menu.lst for Hardy, before installing Jaunty, look exactly like this:

```
title        Ubuntu 8.04.2, kernel 2.6.24-23-generic
root        (hd0,1)
kernel        /vmlinuz-2.6.24-23-generic root=/dev/mapper/vg1-lvHardyRoot ro quiet splash
initrd        /initrd.img-2.6.24-23-generic
quiet
```The only difference between before and now is that before menu list used this:
```
root        (hd0,1)
```Now it uses this:
```
uuid        snip-uuid-27_27
```But blkid shows that those match:
```
/dev/sda2: LABEL="BootPart" UUID="snip-uuid-27_27" TYPE="ext3"
```I only have 1 HDD, so I presume there are no problems with sda not matching hd0.

---

### Post by MountainX on 2009-05-11
I just tried it again. When it stops booting up, I switched to the Alt-F1 terminal. Here's the error message:
```
Starting up...
Loading, please wait...
Setting up cryptographic volume sda3_crypt (based on /dev/disk/by-uuid/snip-uuid-3e36c)
cryptsetup: failed to setup lvm device
[snip - typing by hand because not sure how to copy/paste]
Found volume group "vg1-lvHardyRoot" using metadata type lvm2
Found volume group "vg2-lvJauntyRoot_crypt" using metadata type lvm2
ALERT! does not exist. Dropping to a shell!

```

The UUID mentioned in the error message is the one listed in /etc/crypttab on the Hardy installation. The info is correct in terms of what Hardy expects. But maybe the Jaunty install changed something on /boot that affects this?

---

### Post by MountainX on 2009-05-11
need some help...
been working on this all day and I can't get Hardy to boot

---

### Post by MountainX on 2009-05-11
still looking for help...

---

### Post by MountainX on 2009-05-12
I know this can be fixed, but so far I have not been able to fix it.

However, I can mount both partitions used by Hardy (sda3 and sda4). The data is all there, so it seems the problem has to be limited to the boot partition. I have that backed up, so one would think I could restore parts of /boot and get Hardy to boot up again (without destroying my Jaunty install either).

Any suggestions?

---

### Post by MountainX on 2009-05-16
bump

---

### Post by MountainX on 2009-05-18
any ideas? suggestions?

---

### Post by MountainX on 2009-05-26
I'm just updating this to make it clear that I am still looking for a solution...

---

### Post by MountainX on 2009-08-13
bumping
need help

---

### Post by mikechant on 2009-08-18
Maybe it doesn't help much now, but I think your problems must relate to using the same /boot for both releases - from what happened to your menu.lst it looks like the jaunty install screwed up when recognizing hardy. Although it means a bit of manual work when updating kernels, I like to have a completely seperate set of partitions for a new release - in your case a new /boot for jaunty. Then you can switch grub in the MBR to boot from either the old or new grub setups, and put a non-automatic entry in each to boot the other release. More work but less likely to go wrong I think.

---

### Post by MountainX on 2009-08-18
> **mikechant said:**
> Maybe it doesn't help much now, but I think your problems must relate to using the same /boot for both releases - from what happened to your menu.lst it looks like the jaunty install screwed up when recognizing hardy. Although it means a bit of manual work when updating kernels, I like to have a completely seperate set of partitions for a new release - in your case a new /boot for jaunty. Then you can switch grub in the MBR to boot from either the old or new grub setups, and put a non-automatic entry in each to boot the other release. More work but less likely to go wrong I think.

I have heard conflicting opinions on that -- I asked about it before doing the install, and unfortunately I followed the advice to use the same /boot partition. Now that the mistake has been made, I'm looking for a solution. My reading indicates it can work this way, and that a solution should be possible, but I haven't found one yet.

---

### Post by MountainX on 2009-11-15
I still want to solve this! As long as this thread is not marked solved, I continue to look for a solution. 

At this point in time, the main reason I want a solution is for the learning experience that will come from solving this. I have learned a lot more about grub recently and I would like to apply some of that info to solving this problem. I have attempted a couple times in recent weeks, but I realized that I still need help. I do not yet know enough to fix this on my own. However, I remain convinced it can be fixed.

Anyone want to help me solve this challenge for the purpose of learning more about how grub works?

---

