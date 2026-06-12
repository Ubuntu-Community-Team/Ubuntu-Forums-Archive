---
title: "Installing Grub on RAID 0: Error 15 File not found"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by Jazsun on 2009-07-16
[B]UPDATED OUTPUT/INFO IN POST DOWN BELOW
[/B]
Hello folks,

Booted from Ubuntu 9 x64 live CD. I'm trying to dual boot Win 7 x64 and Ubuntu 9.* x64. Win 7 has already been installed on my two 160GB drives in nvidia RAID 0. I installed dmraid following the instructions here: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto). 

I do the following: 
ubuntu@ubuntu:~$ sudo apt-get install -y dmraid 
ubuntu@ubuntu:~$ sudo modprobe dm-raid4-5 
ubuntu@ubuntu:~$ sudo dmraid -ay 
ubuntu@ubuntu:~$ cd /dev/mapper/ 
ubuntu@ubuntu:/dev/mapper$ ls 
Output: shows my nvidia RAID 0 as nvidia_cbcaeffb, and existing Vista partitions alredy on it (nvidia_cbcaeffb1,nvidia_cbcaeffb2 etc..)

I continue to go through the installation process are create 3 more partitions on the raid 0 drive (nvidia_cbcaeffb), one for /boot, /, and swap. I uncheck "Install bootloader" during the GUI install and then continue to follow the directions on the link above.

ubuntu@ubuntu:/dev/mapper$ sudo mount nvidia_cbcaeffb3 (my root install) /target/ 
ubuntu@ubuntu:/dev/mapper$ sudo mount --bind /dev /target/dev/ 
ubuntu@ubuntu:/dev/mapper$ sudo mount -t proc proc /target/proc/ 
ubuntu@ubuntu:/dev/mapper$ sudo mount -t sysfs sys /target/sys/ 
ubuntu@ubuntu:/dev/mapper$ sudo cp /etc/resolv.conf /target/etc/resolv.conf 
ubuntu@ubuntu:/dev/mapper$ sudo chroot /target/ 
root@ubuntu:/# apt-get update 
root@ubuntu:/# apt-get install -y dmraid 
root@ubuntu:/# apt-get install -y grub 
root@ubuntu:/# mkdir /boot/grub 
root@ubuntu:/# cp /usr/lib/grub/x86_64-pc/* /boot/grub/ 
root@ubuntu:/# grub --no-curses 

grub> device (hd0) /dev/mapper/nvidia_cbcaeffb
grub> find /boot/grub/stage1 

^ and this is where the problem starts... I get ERROR 15: file not found. I tried  device (hd1) (since I have 3 hard drives, 2 in raid 0 and one by itself), but I still get the same issue. If I: ls /target/boot/grub, it shows stage1 as being in there.

I cant get you exact printouts of fdisk nvidia_cbcaeffb3 because I'm not on my machine right now but I will tonight. 

Any ideas? Is grub able to be places on a RAID 0? Is the problem because my linux root partition is not the first partition on the drive?

Thanks a lot!

---

### Post by dstew on 2009-07-16
> ls /target/boot/grub, it shows stage1 as being in there.Then wouldn't the grub command be```
find /target/boot/grub/stage1
```?
I guess it depends on what your root file system is when you run the grub shell program.

---

### Post by Jazsun on 2009-07-17
> **dstew said:**
> Then wouldn't the grub command be```
find /target/boot/grub/stage1
```?
I guess it depends on what your root file system is when you run the grub shell program.


Well, the way I understand find to work is that it will find the /boot/grub/stage1 on any partition on the drive specified (i.e. (hd0)) So this would lead me to belive I shouldnt have to direct it to the mount of the raid 0 root file system partition (/target/boot/grub/stage1)...Anyone?

---

### Post by Jazsun on 2009-07-17
Allright guys this is getting really frustrating..I've deleted my ubuntu partitions numerous times and re-installed..still to no avail. Grub find does not locate anything and gives error 15, and if I skip find and do setup (hd0) I get.


Here is my new HD/partition setup:

My root is: nvidia_cbcaefbb5, im not sure what nvidia_cbcaefbb3 is, but it also creates it when I create a root/swap/boot partition.
```
ubuntu@ubuntu:~$ cd /dev/mapper
ubuntu@ubuntu:/dev/mapper$ sudo fdisk nvidia_cbcaefbb

The number of cylinders for this disk is set to 38914.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk nvidia_cbcaefbb: 320.0 GB, 320083722240 bytes
255 heads, 63 sectors/track, 38914 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c69a450

          Device Boot      Start         End      Blocks   Id  System
nvidia_cbcaefbb1               1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
nvidia_cbcaefbb2              13        3825    30616576    7  HPFS/NTFS
nvidia_cbcaefbb3            3826        7235    27390825    5  Extended
nvidia_cbcaefbb5            3831        6262    19535008+  83  Linux
nvidia_cbcaefbb6            6263        7235     7815591   82  Linux swap / Solaris
nvidia_cbcaefbb7   *        3826        3830       40099+  83  Linux

Partition table entries are not in disk order

Command (m for help): ^C
ubuntu@ubuntu:/dev/mapper$ 

```

And finally here's me failing at GRUB. I belive root should be (hd0,3) because root is the 4th partition according to fdisk above.
```
root@ubuntu:/# sudo grub
sudo: unable to resolve host ubuntu
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> device (hd0) /dev/mapper/nvidia_cbcaefbb
device (hd0) /dev/mapper/nvidia_cbcaefbb
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
grub> root (hd0,3)
root (hd0,3)

Error 18: Selected cylinder exceeds maximum supported by BIOS
grub> setup (hd0)
setup (hd0)

Error 12: Invalid device requested
grub> root (hd0,2)
root (hd0,2)

Error 18: Selected cylinder exceeds maximum supported by BIOS
grub> root (hd0,1)
root (hd0,1)
grub> setup (hd0)
setup (hd0)

Error 17: Cannot mount selected partition
grub> 
```

I followed the steps on the fakeRaidHowTo site to mount the root partition to /target/ and perform various tasks on it before going into grub:

```

$ sudo mount /dev/mapper/nvidia_cbcaefbb5 /target/
$ sudo mount --bind /dev /target/dev/
$ sudo mount -t proc proc /target/proc/
$ sudo mount -t sysfs sys /target/sys/
$ sudo cp /etc/resolv.conf /target/etc/resolv.conf 
$ sudo chroot /target/
# apt-get update 
# apt-get install -y dmraid
# apt-get install -y grub
# mkdir /boot/grub
# cp /usr/lib/grub/x86_64-pc/* /boot/grub/
```

To verify that indeed /boot/grub does exist
```
ubuntu@ubuntu:/dev/mapper$ ls /target/boot/grub/
e2fs_stage1_5  jfs_stage1_5    reiserfs_stage1_5  stage2           xfs_stage1_5
fat_stage1_5   minix_stage1_5  stage1             stage2_eltorito
ubuntu@ubuntu:/dev/mapper$ 

```

---

### Post by vertago1 on 2009-07-18
Try installing using the alternative-cd since it is supposed to work without doing all the tweaks, but if it is like my case you will get stuck at the error 15 again.

I am having a similar issue, I wanted to switch my boot drive to ext4 and make a clean install since I had done about 3 or 4 dist upgrades. I tried installing using both the liveCD and the alternative install CD. Once I get everything setup I get stuck at the error 15. Not sure why it is giving the error because the data is there and the uuid is correct in menu.lst

note, I am using dmraid with an nvidia chipset. The boot drive isn't on the RAID array but my /home directory is.

Double checked the uuid in the fstab file with the grub menu.lst and everything checks out. not sure why it can't see the kernel.

---

### Post by vertago1 on 2009-07-18
I followed the instructions to setup grub here:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

it successfully found grub and installed it but when I rebooted I still got the error 15 message.

---

### Post by vertago1 on 2009-07-18
I found a solution:

Install using the 8.10 alternative install CD then do a distro upgrade to 9.04.

Apparently there is a bug in the installer, not sure how to report it but all I know is I did several install methods with both ext3 and ext4 and kubuntu 9.04 both the normal and the alternate installs and still got the grub error.

---

### Post by Jazsun on 2009-07-21
> **vertago1 said:**
> I found a solution:

Install using the 8.10 alternative install CD then do a distro upgrade to 9.04.

Apparently there is a bug in the installer, not sure how to report it but all I know is I did several install methods with both ext3 and ext4 and kubuntu 9.04 both the normal and the alternate installs and still got the grub error.

Hmm...I ended up giving up and just installed without RAID 0. I was using the alternate cd during all my installs. I was thinking about installing grub to a non RAID hd and having it point to the RAID 0 to launch.

---

