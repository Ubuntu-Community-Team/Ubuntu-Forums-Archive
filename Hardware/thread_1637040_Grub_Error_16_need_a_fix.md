---
title: "Grub Error 16 need a fix"
date: 2010-12-03
forum: Hardware
---

### Post by bikefreak on 2010-12-03
I'm getting a Grub error 16: inconsistent filesystem structure  at boot up.  It displays a menu of different kernel choices and the first one (and 2nd which is recovery mode) always fails with this error.

Been running it for a quite a while with no problems.  32bit

Ubuntu 10.10, kernel 2.6.35-23-generic is giving me the problems
Ubuntu 10.10, kernel 2.6.35-22-generic works fine but seems slow.

Thought it might be a MBR type of error and ran Rescatux (like super grub disk) basically restored MBR and no change.

Error first appeared when I was having trouble getting a thumb drive to load.  plugged it in and out a number of times and it never mounted.  upon reboot (to see if that would fix the mounting problem) it gave the error.  Also don't recall if I rebooted after doing an upgrade where it requested a reboot.  I'm trying to think of what might have caused it.

I'm single booting off a laptop. so no dual boot reasons like most I found when googling.

Searched here and googled with no luck.

Let me know what else you need to help me.

Thanks!

---

### Post by oldfred on 2010-12-04
Welcome to the forums.

You must be using grub legacy as grub2 does not have error numbers.

[http://members.iinet.net.au/~herman546/p15.html#16]("http://members.iinet.net.au/%7Eherman546/p15.html#16")
Says to use gparted and click on partitions to see if it will clear error.

If you know what partition I would run fsck. If you have just upgraded you should download a liveCD just for repairs. Ubuntu liveCD includes gparted. Or you can download the latest gparted liveCD which is a smaller download as Herman suggests.

From liveCD so everything is unmounted, change sdb1 to your partition(s)
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by bikefreak on 2010-12-04
Tried gparted ---  ran "check" and returned no problems.  Still getting grub error.  I am running 10.10 but have upgraded from 8.04?? or something around then.  never had any problems.

Tried your first e2fsck command.  (I tried a fsck command earlier but forgot to mention it)  It didn't return any errors so I didn't run the second. Here is the output:
```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
                                                                               
  302885 inodes used (12.93%)
   21080 non-contiguous files (7.0%)
     624 non-contiguous directories (0.2%)
         # of inodes with ind/dind/tind blocks: 19681/413/1
 8378616 blocks used (89.55%)
       0 bad blocks
       4 large files

  229522 regular files
   31485 directories
      66 character device files
      26 block device files
       3 fifos
     434 links
   41766 symbolic links (35484 fast symbolic links)
       8 sockets
--------
  303310 files
ubuntu@ubuntu:~$ 
```

Is there anything that would have brought "inconsistency" as a result of putting in and pulling out the usb drive quickly and repeatedly?  partial mount or something?

Can i upgrade to grub2?  (how?)

thanks for the help so far.
-

---

### Post by oldfred on 2010-12-04
To install grub2 you need to chroot into your system, and fully uninstall both grub & grub2, then cleanly reinstall grub2.

chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by bikefreak on 2010-12-04
Installed grub2 per instructions (removed grub, used chroot) that went well.  rebooted and got a mess but basically still not working.  here is the error message (in part)  it hangs after the _.
```
[    0.573014] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
[    0.573053] Pid: 1, comm: swapper Not tainted 2.6.35-23-generic #41-Ubuntu
[     xxx] Call Trace:
[     xxx] [<c05c6db0>] ? printk+0x2d/0x35...
[     xxx] [<c05c6db0>] panic+0x5a/oxd2...
[     xxx] [<c05c6db0>] mount_block_root...
[     xxx] [<c05c6db0>] ? sys_mknod+...
[     xxx] [<c05c6db0>] mount_root+...
[     xxx] [<c05c6db0>] prepare_namespace+...
[     xxx] [<c05c6db0>] ? sys_access+...
[     xxx] [<c05c6db0>] kernel_init+...
[     xxx] [<c05c6db0>] ? kernel_init+...
[     xxx] [<c05c6db0>] kernel_thread_helper+...
_

```

Reboot after this presents the grub2? menu where i can select kernel 22 again and get back to where i was. Grub had at the top gnu grub version 1.98+20100804-5ubuntu3

Pressing escape got me to a grub> prompt.

next?  :popcorn:

thx.

---

### Post by bikefreak on 2010-12-04
did more searching with the new error message and thought it might be a problem in the grub.cfg...  doesn't look like it, here is a snip of the contents:
```
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set 075756c2-66cf-42ab-bd7a-e80eedbd5c35
        linux   /boot/vmlinuz-2.6.35-23-generic root=UUID=075756c2-66cf-42ab-bd7a-e80eedbd5c35 ro   quiet splash
        initrd  /boot/initrd.img-2.6.35-23-generic
}
***snip***
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set 075756c2-66cf-42ab-bd7a-e80eedbd5c35
        linux   /boot/vmlinuz-2.6.35-22-generic root=UUID=075756c2-66cf-42ab-bd7a-e80eedbd5c35 ro   quiet splash
        initrd  /boot/initrd.img-2.6.35-22-generic
}

```

-22 works -23 does not.  time to learn about corrupt kernels and how to fix/rebuild/reinstall them?  thoughts?  I'll keep looking for ideas.

---

### Post by bikefreak on 2010-12-04
Sorry for all the posts.  here is where i'm finding some info...  would this make sense in my case?
pulled from this post [http://ubuntuforums.org/showthread.php?t=1635133](http://ubuntuforums.org/showthread.php?t=1635133) but edited for my issue.

Remove 2.6.35-23 with this:
```

sudo apt-get purge linux-headers-2.6.35-23 linux-headers-2.6.35-23-generic linux-image-2.6.35-23-generic

```
Re-install it with this:
```

sudo apt-get install linux-headers-2.6.35-23 linux-headers-2.6.35-23-generic linux-image-2.6.35-23-generic

```

I have not run it yet... looking for a green light on trying it.  All new stuff for me at this point.

thx.

---

### Post by oldfred on 2010-12-04
As long as you have -22 working there should be no harm in uninstalling -23 and reinstalling it. I have never tried it to know for sure.

Does this come back to the original grub error of inconsistent file structure.

Have you run a refresh?
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get clean
sudo apt-get update && sudo apt-get upgrade  #this updates everything
sudo apt-get dist-upgrade     #would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a

---

### Post by bikefreak on 2010-12-04
the original grub error (#16) is gone and the kernel panic error and it hanging has replaced it.  (reboot gives menu then)

I did the clean and no luck.  I started the kernel purge but didn't know if I should continue, see below...

```

user@mylinux:~$ sudo apt-get purge linux-headers-2.6.35-23 linux-headers-2.6.35-23-generic linux-image-2.6.35-23-generic[sudo] password for bikefreak: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  hplip-cups
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-generic* linux-headers-2.6.35-23* linux-headers-2.6.35-23-generic* linux-headers-generic*
  linux-image-2.6.35-23-generic* linux-image-generic*
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
After this operation, 198MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

Will removing linux-generic* and linux-headers-generic* cause any problems for the 2.6.35-22 that is working?   Just concerned it might hork the whole thing...

Thanks oldfred!

---

### Post by oldfred on 2010-12-04
Not sure, but I am always adventuresome as I assume (maybe not correctly) that I can get back into system some way as long as it is not totally corrupted. Then I reinstall.

If you run the  sudo apt-get dist-upgrade next it should make sure you have the newest kernal and what ever it requires.

---

### Post by bikefreak on 2010-12-04
Well I did it with my fingers crossed and everything.  running the commands above appeared to work.  No more errors on bootup.  It does seem slower and not as I remember it but could be because of the change from grub to grub-pc?  not sure.  It never installed a newer kernel even after running the dist-upgrade.  ran synaptic as well... no upgrades.  checked my kernel version. 35-22...  so for now it is solved.  the outcome of my script is below that gives some indications around the error that might have been the root cause.  

```

user@mylinux:~$ sudo apt-get purge linux-headers-2.6.35-23 linux-headers-2.6.35-23-generic linux-image-2.6.35-23-generic[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  hplip-cups
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-generic* linux-headers-2.6.35-23* linux-headers-2.6.35-23-generic* linux-headers-generic*
  linux-image-2.6.35-23-generic* linux-image-generic*
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
After this operation, 198MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 224516 files and directories currently installed.)
Removing linux-generic ...
Removing linux-headers-generic ...
Removing linux-headers-2.6.35-23-generic ...
Removing linux-headers-2.6.35-23 ...
Removing linux-image-generic ...
Removing linux-image-2.6.35-23-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found memtest86+ image: /boot/memtest86+.bin
done
The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-2.6.35-23-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
user@mylinux:~$ 

```
The link /vmlinuz is a damaged link
This might have been the problem??  

I redid the grub-pc thing based on the re-run recommendation from this.  (no change that I noticed)

ran uname -r got this back:
2.6.35-22-generic

thanks for the help and encouragement.  back to my htpc x64 network issue.

---

### Post by oldfred on 2010-12-04
You have old kernels that it looks like you can remove as they are from the old system and may not even be compatible now.

Confirm version you are using so you do not delete it.
 uname -r
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

Some of us use the links as short cuts in custom grub menus to the most current kernel when not wanting to have to upgrade grub menu on every change. I do not think the links are normally used as all the entries refer to the specific kernel.


Your 2.6.28, 2.6.31 & 2.6.32 are all older versions that can be deleted since you now are 2.6.35

---

