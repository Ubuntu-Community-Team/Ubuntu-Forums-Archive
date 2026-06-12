---
title: "Ubuntu wont boot after inproper restart in Ubuntu"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by tigshadorakie on 2009-01-26
After I start my PC up and choose to run Ubuntu all it is doing is going right to Grub4Dos and it sits a GRUB > command prompt. I have no idea how to get Ubuntu to load up again. I had restarted Ubuntu without the proper shutdown now it doesn't work? Why does it do this and how do I correct the problem. As of right now I can not use Ubuntu at all. 

I am new to linux so please respond in terms that a noob would understand.

---

### Post by caljohnsmith on 2009-01-26
Sounds like you have a Wubi install, i.e. Ubuntu installed inside of Windows. If that's true, how about opening a terminal in Windows (Start > Run > type "cmd" and enter), and then in the "cmd" window do:
```
chkdsk /r
```
And that should schedule a chkdsk for the next reboot (if I remember correctly), so go ahead and reboot into Windows and hopefully chkdsk will do its thing. If that completes successfully, then try booting Ubuntu again, and let me know how that goes.

---

### Post by tigshadorakie on 2009-01-26
Yes it is a WUBI install. Everything was great until now. Did what you said. It is still doing the same. Is Linux suppose to get all messed up every time you don't restart properly?

---

### Post by caljohnsmith on 2009-01-27
> **tigshadorakie said:**
> Yes it is a WUBI install. Everything was great until now. Did what you said. It is still doing the same. Is Linux suppose to get all messed up every time you don't restart properly?
So you did the chkdsk and still no joy about booting Ubuntu? And by the way, yes, unfortunately Wubi installs are especially sensitive to improper shutdowns, and it's even mentioned somewhere in the Wubi documentation I think. Do you have a Ubuntu Live CD you can boot to use for troubleshooting? It looks like you will need it at this point. You might still have the Ubuntu Live CD ISO file in the following Windows directory:
```
C:\ubuntu\install\
```
Once you get a Live CD, please boot that, choose the "try Ubuntu without making changes" option at the main menu, once you get to the Ubuntu desktop open a terminal (Applications > Accessories > Terminal), and do:
```
sudo fdisk -lu
```
And please post the output. We can work from there if you want.

---

### Post by tigshadorakie on 2009-01-27
I will try this at some point today. Just check up on the thread later. Thanks

---

### Post by tigshadorakie on 2009-01-27
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd7c7d7c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156280319    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc9e94641

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   490231807   245114880    7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2009-01-27
So is your Ubuntu Wubi install on sda1 or sdb1? Whichever it is, how about doing the following (replace sdXY with the partition Ubuntu is on):
```
sudo mount /dev/[COLOR="Blue"]sdXY[/COLOR] /mnt
sudo fsck -yCM /mnt/ubuntu/disks/root.disk
```
And please post the output. If it says "file not found", how about posting:
```
ls -lR /mnt/ubuntu
```
And we can work from there.

---

### Post by tigshadorakie on 2009-01-27
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo fsck -yCM /mnt/ubuntu/disks/root.disk
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: No such file or directory while trying to open /mnt/ubuntu/disks/root.disk

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ ls -lR /mnt/ubuntu
ls: cannot access /mnt/ubuntu: No such file or directory

---

### Post by caljohnsmith on 2009-01-27
OK, looks like I'm going to need more info about your setup in order to help, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what it will take to get your Wubi install booting again.

---

### Post by tigshadorakie on 2009-01-27
Ok I did it but I dont see the pound sign option anywhere.

---

### Post by tigshadorakie on 2009-01-27
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  Windows XP
    Boot files/dirs:   /bootmgr /ntldr /NTDETECT.COM /wubildr.mbr

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /wubildr.mbr /ubuntu/winboot/wubildr.mbr

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd7c7d7c7

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *            63  156,280,319  156,280,257   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc9e94641

Partition  Boot        Start          End         Size  Id System

/dev/sdb1    *         2,048  490,231,807  490,229,760   7 HPFS/NTFS

/dev/sdb1 ends after the last cylinder of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="9638DF6138DF3F45" LABEL="XP" TYPE="ntfs" 
/dev/sdb1: UUID="48A08168A0815D76" LABEL="Ubuntu-Vista" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/Ubuntu-Vista type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

=======Devices which don't seem to have a corresponding hard drive==============

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-27
OK, how about doing:
```
sudo umount /mnt && sudo mount /dev/sdb1 /mnt
ls -lR /mnt/ubuntu
```
And please post the output.

---

### Post by tigshadorakie on 2009-01-27
ubuntu@ubuntu:~$ sudo umount /mnt && sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ ls -lR /mnt/ubuntu
/mnt/ubuntu:
total 145
-rwxrwxrwx 1 root root      0 2008-12-18 22:39 curl_log.txt
drwxrwxrwx 1 root root      0 2008-12-18 22:39 docs
drwxrwxrwx 1 root root      0 2008-12-18 23:07 install
-rwxrwxrwx 2 root root    225 2008-12-18 22:42 metadl_log.txt
-rwxrwxrwx 1 root root  25214 2008-10-27 17:37 Ubuntu.ico
-rwxrwxrwx 2 root root 118608 2008-12-18 22:39 Uninstall-Ubuntu.exe
drwxrwxrwx 1 root root      0 2008-12-18 22:39 winboot

/mnt/ubuntu/docs:
total 0

/mnt/ubuntu/install:
total 0

/mnt/ubuntu/winboot:
total 408
-rwxrwxrwx 1 root root    806 2008-10-27 17:37 menu.lst
-rwxrwxrwx 1 root root 192307 2008-10-27 17:37 wubildr
-rwxrwxrwx 1 root root 209235 2008-10-27 17:37 wubildr.exe
-rwxrwxrwx 1 root root   8192 2008-10-27 17:37 wubildr.mbr
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2009-01-27
Did you all ready try to uninstall Ubuntu? Because you don't seem to have the Ubuntu main partition any where. Usually it is under /ubuntu/disks/root.disk. Do you have any idea of how it might have been deleted or maybe moved? I think now would be a good time to consider doing a standard Ubuntu install to its own partition. You could for example shrink your sdb1 partition and put Ubuntu on the sdb drive, or you could shrink your sda1 partition and put Ubuntu on the sda drive. How does that sound?

---

### Post by tigshadorakie on 2009-01-27
I didn't delete Ubuntu at all yet. It still shows up under my Add/Remove programs in XP. Is there any type of viruses or scripts that can do anything while surfing the net? I thought Linux was very secure and I don't use antivirus or a firewall.

---

### Post by caljohnsmith on 2009-01-27
OK, we could do a search and see if we can find your Ubuntu partition. How about doing:
```
sudo umount /mnt && sudo mkdir /mnt/sda1 /mnt/sdb1
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sdb1 /mnt/sdb1
find /mnt -size +1000M -printf "%s - %p\n" | sort -n
```
It might take a little while for the "find" command to run, but please post the results once it finishes.

---

### Post by tigshadorakie on 2009-01-27
Yeah I am going to put Ubuntu on its own partition, maybe even it's own Hard drive. I have to figure out how I want to work it. I have some important things on both drives and I don't want to accidently format one of them or the wrong one. I will have to mess with this later tonight or tomorrow. Your suggestions and help are still appreciated though, if you think of something. I'll be checking the forum again in a bit.

---

### Post by tigshadorakie on 2009-01-27
ok I will try that, I'll post the results

---

### Post by tigshadorakie on 2009-01-27
ubuntu@ubuntu:~$ sudo umount /mnt && mkdir /mnt/sda1 /mnt/sdb1
umount: /mnt: not mounted
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/sda1
fuse: failed to access mountpoint /mnt/sda1: No such file or directory
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt/sdb1
fuse: failed to access mountpoint /mnt/sdb1: No such file or directory
ubuntu@ubuntu:~$ find /mnt -size +1000M -printf "%s - %p\n" | sort -n
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2009-01-27
My mistake, you just need a "sudo" in front of the "mkdir" command. I corrected my previous post, so please try again.

---

### Post by tigshadorakie on 2009-01-27
still does the same thing.

---

### Post by caljohnsmith on 2009-01-27
How about trying instead:
```
sudo umount /mnt
sudo mkdir /mnt/sda1 /mnt/sdb1
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sdb1 /mnt/sdb1
find /mnt -size +1000M -printf "%s - %p\n" | sort -n
```

---

### Post by tigshadorakie on 2009-01-27
just to let you know the cursor is blinking after the -n. It has been doing this since a little after your last post. Is it doing something?

---

### Post by caljohnsmith on 2009-01-27
> **tigshadorakie said:**
> just to let you know the cursor is blinking after the -n. It has been doing this since a little after your last post. Is it doing something?
Great, that means its working, but it will probably take quite a while; it is searching through your entire sda and sdb drives, so that's about 330 GB total. But at least if your Ubuntu partition is hiding somewhere, that command should find it.

---

### Post by tigshadorakie on 2009-01-27
I don't know if your suppose to do it this way, but for that one I copied what you put down and pasted it in the terminal all at once. I don't know if it needed to posted one line at a time. This is the output as of right now.

ubuntu@ubuntu:~$ sudo umount /mnt
umount: /mnt: not mounted
ubuntu@ubuntu:~$ sudo mkdir /mnt/sda1 /mnt/sdb1
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/sda1
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt/sdb1
ubuntu@ubuntu:~$ find /mnt -size +1000M -printf "%s - %p\n" | sort -n

---

### Post by caljohnsmith on 2009-01-27
That looks just fine; the "find" command should be cranking away right now looking through your HDDs for any large files, and it will output them when done. Unfortunately looking through 330 GB is going to take a while though, you may want to leave it and come back in say an hour or so.

---

### Post by tigshadorakie on 2009-01-28
Just want to let you know I did a fresh install of Ubuntu and things seem to be much better. Grub loads up properly and gives me the option of using Ubuntu or Windows. Thanks for all your help. I just wish I knew why it all of a sudden went bad. Maybe something happened in Windows. I won't use Wubi anymore that is for sure. Thanks!

---

### Post by caljohnsmith on 2009-01-28
I'm glad to hear your new Ubuntu install went OK; I think you will run into alot less problems since you decided to do a standard Ubuntu install to its own partition. Cheers and hope your Ubuntu experience goes smoother now. :)

---

