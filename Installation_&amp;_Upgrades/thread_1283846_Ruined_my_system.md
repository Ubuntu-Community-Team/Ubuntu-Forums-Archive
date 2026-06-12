---
title: "Ruined my system"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by G2k on 2009-10-06
Hey guys. Not long ago I apt-get upgraded my system to the latest Karmic release and it ruined my Ubuntu install. In the hopes of fixing it, I waited a few weeks so that maybe the bug would be fixed. I used an Ubuntu livecd and did as follows```
#mkdir /mnt/ubuntu && mount -t ext3 /dev/sda4 /mnt/ubuntu && mount -t ext2 /dev/sda3 /mnt/ubuntu/boot && mount -o bind /dev/pts /mnt/ubuntu/dev/pts/ && mount -o bind /sys /mnt/ubuntu/sys && mount -o bind /proc /mnt/ubuntu/proc && chroot /mnt/ubuntu /bin/bash
```
then I did a```
apt-get update && apt-get upgrade
```but I think I did something wrong because when I rebooted, I just got a black screen with a bunch of text flashing by over and over. So I rebooted into the livecd again, did the same steps as written above, only this time I ran```
apt-get autoremove && apt-get dist-upgrade
```This time, something went wrong with the kernel installation I guess because now when I reach the GRUB screen, it tells me it cannot find any of the kernels I try to boot into. Do you guys know what I can do to fix this problem :confused: ??

Thanks in advance...I don't really feel like doing a fresh Ubuntu install

---

### Post by slakkie on 2009-10-06
I noticed some problems too with the upgrade of last night. I had to restore an old backup because I needed some work done. 

Don't take this the wrong way: MAKE BACKUPS SO YOU CAN RESTORE.
Really, running a development release is likely to cause problems. If you can restore to a known state you can experiment with the upgrades you allow and which you don't allow. Then you don't have problems that you don't have access to your PC because a particular upgrade broke your system.

Regarding the issue, since you have a liveCD, boot from the liveCD. Mount your root file system (I take it /var/log is not on a seperate slice) and have a look in 

* /var/log/messages
* /var/log/daemon
* /var/log/kern.log
* /var/log/debug
* /var/log/syslog
* /var/log/dmesg 

See if you can find something relevant.

---

### Post by G2k on 2009-10-06
hmm ok I'll give that a spin but I think i messed something up with where my kernels are pointing to or where GRUB is looking for them. How can I re-install the latest stable kernel?

---

### Post by slakkie on 2009-10-06
> **G2k said:**
> hmm ok I'll give that a spin but I think i messed something up with where my kernels are pointing to or where GRUB is looking for them. How can I install the latest stable kernel?

Install one of these packages:

```

p   linux-image-ec2                                            - Linux kernel image for ec2 machines
i   linux-image-generic                                        - Generic Linux kernel image
p   linux-image-generic-pae                                    - Generic Linux kernel image
p   linux-image-rt                                             - Rt Linux kernel image
p   linux-image-virtual                                        - Linux kernel image for virtual machines

```

---

### Post by G2k on 2009-10-06
Ok I've finally booted back into my system...phew.
I removed grub and my kernels and then ran apt-get autoremove. Then I re-installed grub and the latest kernel, ran grub manually and rebooted. Things seem fine now.
Thanks ;-)

---

### Post by slakkie on 2009-10-06
Good to hear! Best of luck during the rest of the beta :)

---

### Post by ottosykora on 2009-10-06
> **G2k said:**
> Ok I've finally booted back into my system...phew.
I removed grub and my kernels and then ran apt-get autoremove. Then I re-installed grub and the latest kernel, ran grub manually and rebooted. Things seem fine now.
Thanks ;-)

on one system where I have separate boot partition and ubuntu root on other drive, after cloning the drive to new disk, grub refused to find what it was told to find. To me it looks as grub needs very little to break?
I also had to use the grub supperdisk and replace the grub, from then on it did find the kernel and the rest again.

---

