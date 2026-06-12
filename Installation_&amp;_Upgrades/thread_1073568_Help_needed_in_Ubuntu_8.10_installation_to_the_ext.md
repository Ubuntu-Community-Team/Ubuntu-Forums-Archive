---
title: "Help needed in Ubuntu 8.10 installation to the external hard drive"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by rajshekhar on 2009-02-18
Hi friends,
I am a new member in this forum.
I have a Dell XPS m1530 system with Microsoft Vista Ultimate.
But, I want to try Ubuntu in my laptop using an external drive. 
So, I have created three partitions for Ubuntu purposes. 
1. for booting purposes with 120mb /dev/hdb2
2. for swap with 3gb /dev/hdb4
3. for the root partition with 6gb /dev/hdb6
I had installed the bootloader to the /dev/hdb2.
After installation, when the reboot is done, I tried to boot the system from external HDD, but it dint detect any OS there, rather started booting the Vista.
I had done some googling, then executed, the below mentioned scripts for both the ext3 partitions - 
tune2fs -c 0 -i 0 -m 1 /dev/hdbx
But still no result. Please help me to load Ubuntu.

---

### Post by birddog165 on 2009-02-18
Do you even get the grub boot loader? I believe that you need to edit the location where it's searching for the OS.

If you can't even see the grub loader, then you need to change your boot order in your bios to load the USB before the internal hdd.

I'm curious though, so did you create the partitions then install, or did you let Ubuntu create them for you?

---

### Post by rajshekhar on 2009-02-18
I am not able to see the boot loader. I made changes in the BIOS to boot from USB hard drive, but to no use.
I have created the partitions **manually** while installing Ubuntu.

---

### Post by caljohnsmith on 2009-02-18
> **rajshekhar said:**
> 
I had installed the bootloader to the /dev/hdb2.

If you installed Grub to /dev/hdb2 under the "Advanced" settings button in the installer, that won't allow you to boot the drive. You need to install Grub to the MBR (Master Boot Record) in order to boot the drive. Since you all ready have Ubuntu installed, you should be able to do that with:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands before typing "quit." Then reboot and see if you can boot your Ubuntu drive.

---

### Post by rajshekhar on 2009-02-18
@caljohnsmith
But I am having another partition in the external hard drive in ntfs format. 
If I install bootloader in the MBR of that drive, will it effect the other(NTFS) partition?

> Since you all ready have Ubuntu installed, you should be able to do that with:
How am I supposed to go to the terminal for executing the commands?
Is it by booting through the Ubuntu Live CD?

---

### Post by caljohnsmith on 2009-02-18
> **rajshekhar said:**
> @caljohnsmith
But I am having another partition in the external hard drive in ntfs format. 
If I install bootloader in the MBR of that drive, will it effect the other(NTFS) partition?

No, fortunately it will not affect the NTFS partition to install Grub to the MBR.
> **rajshekhar said:**
> 
How am I supposed to go to the terminal for executing the commands?
Is it by booting through the Ubuntu Live CD?
Yes, you can do the commands from the Live CD.

---

### Post by rajshekhar on 2009-02-19
> **caljohnsmith said:**
> Please post the output of all the above commands before typing "quit." Then reboot and see if you can boot your Ubuntu drive.

Here are the output from the command executions.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
grub> find /grub/stage1
find /grub/stage1
 (hd1,1)
grub> root (hd1,1)  
root (hd1,1)
grub> setup (hd1)
setup (hd1)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd1) (hd1)1+16 p (hd1,1)/grub/stage2 /grub/menu.lst"... succeeded
Done.
grub> 

By the way, I am able to boot Ubuntu finally. Thanks for the help.

---

### Post by caljohnsmith on 2009-02-19
Glad to hear that worked OK; cheers and enjoy your Ubuntu install. :)

---

