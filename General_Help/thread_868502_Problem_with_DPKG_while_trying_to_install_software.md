---
title: "Problem with DPKG while trying to install software."
date: 2008-07-23
forum: General Help
---

### Post by salparadise17 on 2008-07-23
Let me say I LOVE UBUNTU and I hoped I would never actually have to join the forum to solve a problem:(. None the less, here it is:
     A few weeks ago when I went to update software I got a message saying that "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E:_cache->open() failed, please report." For a while I did nothing, then I realized that I get that error whenever I try to install any software. If I try to open Synaptic Package Manager, I get the error before the program even fully opens. I get it whenever I try to install from "add/remove programs". It's everywhere. 
     I am not entirely helpless, I have run the suggested command (and several others all resulting in the same messages) which returned:
```
Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.24-18-generic (2.6.24-18.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-18-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-18-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-18-generic:
 linux-restricted-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-18-generic:
 linux-ubuntu-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-18-generic; however:
  Package linux-ubuntu-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-18-generic; however:
  Package linux-restricted-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.18.20); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.18.20); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
dpkg: subprocess post-installation script returned error exit status 1

```

     I know a bit but this output is over my head, please help!
Thanks,
Sal.

---

### Post by cdtech on 2008-07-23
I would start off with a "sudo apt-get autoclean && sudo apt-get autoremove" to clean out the repository then try the apt-get update again and see what you get.

Hope this helps...

**P.S.**
Added the autoclean to the command.

---

### Post by salparadise17 on 2008-07-23
Nope, I get the same "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E:_cache->open() failed, please report." message again before it does anything else.

---

### Post by cdtech on 2008-07-23
Let's try this then:
"sudo dpkg --configure -a && sudo apt-get -f install"

---

### Post by salparadise17 on 2008-07-23
Yeah, I've already done that. Returned same thing basically as the first post:
```

Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.24-18-generic (2.6.24-18.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-18-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-18-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-18-generic:
 linux-restricted-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-18-generic:
 linux-ubuntu-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-18-generic; however:
  Package linux-ubuntu-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-18-generic; however:
  Package linux-restricted-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.18.20); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.18.20); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
dpkg: subprocess post-installation script returned error exit status 1
```

---

### Post by cdtech on 2008-07-23
gzip: stdout: No space left on device

say's you have no space left. What do you get with "df -H"?

---

### Post by bodhi.zazen on 2008-07-24
Your root partition is full, lol

Delete / remove unnecessary files, empty the trash, then

```
sudo dpkg --configure -a && sudo apt-get -f install
```

---

### Post by salparadise17 on 2008-07-24
Looks to me like root is only 74 percent full, what gives? Is it the boot partition that needs space? I would assume not?

```
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda6              6.0G   4.2G   1.6G  74% /
varrun                 1.1G   107k   1.1G   1% /var/run
varlock                1.1G      0   1.1G   0% /var/lock
udev                   1.1G    74k   1.1G   1% /dev
devshm                 1.1G    13k   1.1G   1% /dev/shm
lrm                    1.1G    40M   1.1G   4% /lib/modules/2.6.24-17-generic/volatile
/dev/sda1               48M    46M      0 100% /boot
/dev/sda7              125G    37G    82G  31% /home
gvfs-fuse-daemon       6.0G   4.2G   1.6G  74% /home/joshua/.gvfs
/dev/mmcblk0p1         2.1G   2.0G   118M  95% /media/disk
/dev/scd0              621M   621M      0 100% /media/cdrom0

```

---

### Post by cdtech on 2008-07-24
Yes, that's correct. The /boot holds the kernel image files.

You could remove the kernel images that you are not using (through synaptic). Leaving the one that you know works correctly.

**P.S.**
I just noticed that you only have 48mb within the /boot partition. If you plan to play around with more than one kernel you will need more than that my friend.

---

### Post by salparadise17 on 2008-07-24
Well I feel stupid and angry. That did not fix the problem, now I have a new one, a big one. I deleted the 2.6.24-16 and 17 stuff, because I had an 18 entry in there and I figured that was what I was using. Unfortunately, it turns out I was using 17, and the 18 kernel isn't even an option on the GRUB boot list. Now I am on the live cd, because my computer does not start. I replaced the 2.6.24-16 kernel files from the boot cd back onto my boot partition, and tried to reboot, but it still says file not found... WHAT DO I DO?

---

### Post by cdtech on 2008-07-24
When you get to the grub boot list select the kernel line before it boots and press the "e" key. Edit the kernel line to reflect the Kernel image you have to boot with.

Once you boot into the Ubuntu drive you'll have to do a "update-grub".

**P.S.**
Don't feel stupid or angry, we've all been there.

---

### Post by salparadise17 on 2008-07-24
Yay, it worked. Okay I had some extraneous issues with my kernels and their names. For people who might have this same problem I would like to point out that the advice:
> 
You could remove the kernel images that you are not using (through synaptic). Leaving the one that you know works correctly.

Was absolutely correct. Only 2 things: Make sure sure you are deleting the correct files, and **after you delete them you must run "sudo dpkg --configure -a" again in order to be able to update!**

Thanks much man, I owe you!

---

### Post by bodhi.zazen on 2008-07-24
If you are on the live CD you can install a kernel / reconfigure using chroot.

First, as suggested, you might want to make /boot larger (with gparted)

```
sudo -i #Might as well become root

mount /dev/sda6 /mnt
mkdir /mnt/boot #may not need to do this step
mount /dev/sda1 /mnt/boot

sudo chroot /mnt /bin/bash
```with the chroot / is now your HD install, proceed

```
dpkg --configure -a && sudo apt-get -f install
```Now that may solve your problem and install a kernel. If not use apt-get to install a kernel.

exit and reboot

---

### Post by cdtech on 2008-07-24
Awesome, great job. You don't owe anybody just enjoy.......

---

