---
title: "Kernel panic - not syncing"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by dereferenced on 2009-03-28
Now, I did search about this problem in web before posting this thread.. so please do not get angry. The error I got is "Kernel panic - not syncing: VFS: Unable to mount root FS... etc." 

I tried to **upgrade Ubuntu** and that is when this problem raised. some forums said this might be due to bad memory, so I did memory test and it passed.

so next I thought its due to mount point issues, so with live cd I tried to mount root i.e. /dev/sda6 in my case.. as some forum suggested I changed my fstab to look like:
> 
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda7 swap swap defaults 0 0
/dev/sda6 /media/sda6 ntfs defaults 0 0

**[SIZE="3"]fdisk:[/SIZE]**

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00028611

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2490    20000893+   b  W95 FAT32
/dev/sda2            2491       19457   136287427+   5  Extended
/dev/sda5            2491       16843   115290441    b  W95 FAT32
/dev/sda6           16844       19333    20000893+  83  Linux
/dev/sda7           19334       19457      995998+  82  Linux swap / Solaris


so when I say 'mount -a' it gives following error:

> NTFS signature is missing.
Failed to mount '/dev/sda6': Invalid argument
The device '/dev/sda6' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

what am I doing wrong. Many thanks in advance.

---

### Post by dereferenced on 2009-03-28
also, grub stage1 is on (hd0,5) and I set it up again. but I wanted to check menu.lst file but I do not see /boot/grub folder at all (through live cd).. how is that? (and while booting without live cd grub is launched).

---

### Post by tommcd on 2009-03-28
> **dereferenced said:**
> 
... so next I thought its due to mount point issues, so with live cd I tried to mount root i.e. /dev/sda6 in my case.. as some forum suggested I changed my fstab to look like:
Quote:
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda7 swap swap defaults 0 0
**/dev/sda6 /media/sda6 ntfs defaults 0 0 **

**[SIZE="3"]fdisk:[/SIZE]**
Device Boot Start End Blocks Id System
/dev/sda1 * 1 2490 20000893+ b W95 FAT32
/dev/sda2 2491 19457 136287427+ 5 Extended
/dev/sda5 2491 16843 115290441 b W95 FAT32
**/dev/sda6 16844 19333 20000893+ 83 Linux**
/dev/sda7 19334 19457 995998+ 82 Linux swap / Solaris 


If /dev/sda6 is your root partition (as it looks like from the output of fdisk) then your fstab for /dev/sda6 should be something like:
```
#/dev/sda6   
UUID     /        ext3       relatime,errors=remount-ro        0  1

```
Replace UUID with the UUID of your root partition. To find the UUID run **blkid** in terminal. It will output the UUID for each partition. You could just go with **defaults** in the options column of fsab. The relatime,errors=remount-ro is the standard options that Ubuntu sets for the root partition.

I don't know why there is no grub directory when booting from the live CD. Did you mount the root partition from the live CD before checking? 

Also, what version of Ubuntu did you upgrade from? And what version did you upgrade to?

---

### Post by dereferenced on 2009-03-29
Hi, thank you for the reply.

I upgraded from hardy to intrepid. kernel got upgraded from 2.16.24 to 2.16.27. And its my mistake, yes I was stupidly looking into ubuntu root file system and not /media/sda6 root to check for menu.lst. I checked fstab was set already with the appropriate UUID for /dev/sda6. But no use.

All this while I installed 8.04 again(since I had only that CD) and upgraded to 8.10 (only after updating the system in 8.04 of course. I also read its not a good idea to upgrade but to install afresh). Kernel 2.16.27 is still giving kernel panic error while Kernel 2.16.24 is booting but keyboard not working (in login page itself). I checked in xorg config file in which keyboard is mentioned in input devices.

Somebody had the same problem but their native SATA is disabled so they had to change it to hda3 instead of sda3, link is as below for more info:
[http://www.linuxquestions.org/questions/linux-kernel-70/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block20-688150/](http://www.linuxquestions.org/questions/linux-kernel-70/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block20-688150/)

I had once disabled SATA when I was installing windows (windows installation was giving error when it was enabled, so disabled it), so I tried enabling it and booting Kernel 2.16.27. but for no use.

I still want help resolving it (I could go for installing 8.10 afresh but I want to know what the issue is with this, and that if I can work around, also as I do not have 8.10 CD). Many thanks in advance.

---

### Post by tommcd on 2009-03-29
> **dereferenced said:**
> 
I upgraded from hardy to intrepid. kernel got upgraded from 2.16.24 to 2.16.27. 
The current kernel for Intrepid is 2.6.27-11-generic. Is 2.16.27 a typo? Ubuntu 8.10 from a fresh install would give you 2.6.27-xx. Did you get all the updates for Intrepid? Run:
```
aptitude search linux-image
```
to see what kernels are available. A **p** before the package name means it is purged (i.e., not installed). A **i** before the package means it is installed. It should show 2.6.27-xx kernels available for installation. 

> **dereferenced said:**
>  I also read its not a good idea to upgrade but to install afresh).
You will get different opinions on this. Personally, I always do a clean install. It takes less than 20 minutes for me to do a clean install, then perhaps another 60 minutes (at the most) to reinstall the programs I use and set things up the way I want them. I don't consider this to be a problem. It is the best way to avoid problems imo because you start with a fresh system.

> **dereferenced said:**
> 
Somebody had the same problem but their native SATA is disabled so they had to change it to hda3 instead of sda3, link is as below for more info:
[http://www.linuxquestions.org/questions/linux-kernel-70/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block20-688150/](http://www.linuxquestions.org/questions/linux-kernel-70/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block20-688150/)
Make sure grub's menu.lst is pointing to the correct to the correct kernel and root partition (which is noted on the kernel line in menu.lst as root=UUID# instead of root=/dev/sdaX).

If that fails then try updating the initrd for the problematic kernel. See this:
[https://help.ubuntu.com/community/Update%20the%20Ramdisk](https://help.ubuntu.com/community/Update%20the%20Ramdisk)
Replace "uname -r" with the name of the kernel you want to update the initrd for. Using uname -r will update the initrd for the running kernel.

---

### Post by dereferenced on 2009-03-30
tommcd, thank you for replying again.

While upgrading it got all the updates needed for 8.10 and removed some files. But I got all the updates for hardy before attempting to upgrade.

I have searched for linux images, the result did not have 2.6.27 image. Please find below the output:

> p   linux-image                                                            - Generic Linux kernel image.                                                     
v   linux-image-2.6                                                        -                                                                                 
p   linux-image-2.6.24-16-386                                              - Linux kernel image for version 2.6.24 on i386                                   
p   linux-image-2.6.24-16-generic                                          - Linux kernel image for version 2.6.24 on x86/x86_64                             
p   linux-image-2.6.24-16-server                                           - Linux kernel image for version 2.6.24 on x86/x86_64                             
p   linux-image-2.6.24-16-virtual                                          - Linux kernel image for version 2.6.24 on x86                                    
p   linux-image-2.6.24-18-386                                              - Linux kernel image for version 2.6.24 on i386                                   
p   linux-image-2.6.24-18-generic                                          - Linux kernel image for version 2.6.24 on x86/x86_64                             
p   linux-image-2.6.24-18-server                                           - Linux kernel image for version 2.6.24 on x86/x86_64                             
p   linux-image-2.6.24-18-virtual                                          - Linux kernel image for version 2.6.24 on x86                                    
p   linux-image-2.6.24-19-386                                              - Linux kernel image for version 2.6.24 on i386                                   
i   linux-image-2.6.24-19-generic                                          - Linux kernel image for version 2.6.24 on x86/x86_64                             
p   linux-image-2.6.24-19-server                                           - Linux kernel image for version 2.6.24 on x86/x86_64                             
p   linux-image-2.6.24-19-virtual                                          - Linux kernel image for version 2.6.24 on x86                                    
p   linux-image-386                                                        - Linux kernel image on 386.                                                      
p   linux-image-686                                                        - Upgrade dummy package. Can be removed                                           
p   linux-image-debug-2.6.24-16-386                                        - Linux kernel debug image for version 2.6.24 on i386                             
p   linux-image-debug-2.6.24-16-generic                                    - Linux kernel debug image for version 2.6.24 on x86/x86_64                       
p   linux-image-debug-2.6.24-16-server                                     - Linux kernel debug image for version 2.6.24 on x86/x86_64                       
p   linux-image-debug-2.6.24-16-virtual                                    - Linux kernel debug image for version 2.6.24 on x86                              
p   linux-image-debug-2.6.24-18-386                                        - Linux kernel debug image for version 2.6.24 on i386                             
p   linux-image-debug-2.6.24-18-generic                                    - Linux kernel debug image for version 2.6.24 on x86/x86_64                       
p   linux-image-debug-2.6.24-18-server                                     - Linux kernel debug image for version 2.6.24 on x86/x86_64                       
p   linux-image-debug-2.6.24-18-virtual                                    - Linux kernel debug image for version 2.6.24 on x86                              
p   linux-image-debug-2.6.24-19-386                                        - Linux kernel debug image for version 2.6.24 on i386                             
p   linux-image-debug-2.6.24-19-generic                                    - Linux kernel debug image for version 2.6.24 on x86/x86_64                       
p   linux-image-debug-2.6.24-19-server                                     - Linux kernel debug image for version 2.6.24 on x86/x86_64                       
p   linux-image-debug-2.6.24-19-virtual                                    - Linux kernel debug image for version 2.6.24 on x86                              
p   linux-image-debug-386                                                  - Linux kernel debug image for 386 kernel image                                   
p   linux-image-debug-generic                                              - Linux kernel debug image for generic kernel image                               
p   linux-image-debug-server                                               - Linux kernel debug image for server kernel image                                
i   linux-image-generic                                                    - Generic Linux kernel image                                                      
p   linux-image-k7                                                         - Upgrade dummy package. Can be removed                                           
p   linux-image-server                                                     - Linux kernel image on Server Equipment.                                         
p   linux-image-virtual                                                    - Description: Linux kernel image geared towards virtualised hardware             


Also, menu.lst has UUID mentioned properly against all the images.
And I tried updating ramdisk for 2.6.27-11-generic kernel but as I am running on live cd it said update-initramfs is disabled.

---

### Post by superigue on 2009-03-30
i cannot understanding your posts. could you please explain it in layman's terms if you can. thank you.. i am currently experiencing the same problem and i also would like to ask how can i reinstall ubuntu? even if i restart my computer, the CD won't install ubuntu... thanks

---

### Post by tommcd on 2009-03-30
> **superigue said:**
> ... i also would like to ask how can i reinstall ubuntu? even if i restart my computer, the CD won't install ubuntu..

How are you installing Ubuntu? Are you trying to install in Windows using Wubi? Or are you trying to install the real way, to a dedicated partition?
If you want to install to a dedicated partition, then make sure your computer is set to boot from the CDROM drive as the first boot device in the BIOS.

Here is a good set of guides for setting up a dual boot Windows + Ubuntu system. It uses Ubuntu 8.04 as an example, but installing 8.10, or 9.04, would be essentially the same.
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
Here is another good site for getting started with Ubuntu:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by tommcd on 2009-03-30
> **dereferenced said:**
> 
And I tried updating ramdisk for 2.6.27-11-generic kernel but as I am running on live cd it said update-initramfs is disabled.

It looks like your kernel did not get updated when you upgraded from Hardy to Intrepid. You only have 2.6.24 kernels available. The 2.6.24 kernel was the one from Hardy IIRC.

You wont be able to update the initrd for 2.6.27 if you do not have it on your system. If you are booting from the live CD, then you could try mounting and chroot-ing into your Ubuntu install. Something like:
```

sudo mount /dev/sda6 /mnt
sudo chroot /mnt
sudo update-initramfs -u -v -k 2.6.XX

```
Replace 2.6.XX with whatever kernel is giving you problems. I don't know if this will help, but at this point it can't hurt, so it's worth a try.

Late EDIT: Are you running 32 bit or 64 bit Ubuntu?

---

### Post by dereferenced on 2009-03-31
Greetings tommcd, this is amazing. I just booted into 2.6.24 (as I said earlier, I was able to boot through 2.6.24 but keyboard is not working to login), I launched tty1 and tried to install something, it gave me error that package manager was interrupted so I had to run dpkg --configure -a. Then it was done and I was automatically pushed to Xserver mode, keyboard was not active yet. Just whimsically I rebooted through 2.6.27 and hurray!! I was able to boot through 2.6.27. 

You are right, the whole problem might be because of things not getting installed properly. Thanks for guiding me through (and for not getting yourself panic attacks when I upgraded my kernel to "2.16.27". That did made me laugh hysterically when I realised).

Also, just to add, I did enable SATA before I ran dpkg --configure -a (which created initrd image again, complaining things are not in sync) (if that helps somebody, not sure if it helped in my case). Phew, my system is up and running in 8.10. 

**I am running on 32 bit Ubuntu.**

---

