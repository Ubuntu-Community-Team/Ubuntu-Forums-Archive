---
title: "Unbootable Laptop after Grub- Removal"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by Abhischek Thottakara on 2009-01-04
I have installed Ubuntu 64-Bit on my Laptop to DUAL-BOOT Vista/Ubuntu.Because I have a Nvidia 9600GT Graphic Card, which has some performance issues I decided to wait and formated my Linux partition. I know that you have to restore Vista MBR to get a bootable machine again but I did not have a recovery cd to use the recover console and I did not know at that time that you can download one free. So I used Ubuntu Live CD 8.10 Intrepid Ibex and followed the instructions of this webpage: "http://ubuntuforums.org/showthread.php?t=622828".

The exact commands I used were: 
"sudo apt-get install syslinux
 sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda"

But because it didn't work out: 
"sudo apt-get install mbr
 sudo install-mbr -i n -p D -t 0 /dev/sda"

Both commands were of no use and Grub was still making the error. I forgot the exact error number, but I'm sure you'll know this error when you format the ubuntu partion. I got very desperate and installed ubuntu again with the hope that I can at least dual boot the laptop again. But after installation when I rebooted I noticed that there wasn't an entry for Vista as earlier. I could only choose between Ubuntu 8.10, Ubuntu 8.10 recovery mode, and Memtest. So I got even more desperate because I feared that Ubuntu formated my Vista Partition accidentaly. I researched on the Internet and found an answer. SuperGrubDisk: "http://supergrubdisk.org/". I downloaded the Iso and booted the cd then I went to the Windows Section and selected restore mbr then that programm prompted me to select the OS that was installed bevor Ubuntu, well actually select the Bootloader before Grub. 
And here is my actual problem: There is no entry for Windows, the only thing I can select is "Syslinux". I have no idea what that is and how it came to my Vista partition. But in my despair I selected "Syslinux" hoping that I can boot Vista again, but now my laptop is totally unbootable is says: "BOOTMGR is missing, Press Ctrl+Alt+Del to restart". 

I called my friend who has a recovery cd for his laptop, but which is 32-bit. I started the Vista setup and went to "Repair Computer" what first scared me to death was that there was no entry for "previous Vista installations", still I pressed next and selected "Fix Starting Problems" which ended with the message that all problems were solved and it wrote a new MBR. But it still didn't work out. Again same problem "BOOTMGR.." then I researched on the internet and went to Command & Prompt in the Repair menu. 
And used this commands:
"bootrec /fixmbr"
"bootrec /fixboot"
"bootrec /rebuildbc"
The first to commands completed succesfully but the last one showed me the Error Message that there were no Windows Versions.
I am still stuck with the "BOOTMGR" Problem, and I want to boot Vista again.
So please help me I am very desperate and I do not want to format my Vista partition and reinstall Vista.
I appreciate all the help I can get, but please notice that I am not a linux Pro, I've began to use Ubuntu on my old laptop about a year ago "Dapper Drake" but still I am new to that OS.

Please help me fast, because my old laptop from which I am writing right now belongs to my friend now.

Abhischek**[B][B]**[/B][/B]

---

### Post by caljohnsmith on 2009-01-04
In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by Abhischek Thottakara on 2009-01-05
I did that command and these are the results, but please note that you will find an Windows Vista entry in Grub-menu.lst. I added that entry by myself because ubuntu did not automatically. But when I boot this entry the error "BOOTMGR..." occurs again.

Results
```
 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x31604f27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   292095991   146046972    7  HPFS/NTFS
/dev/sda2       292109895   312576704    10233405   83  Linux

sfdisk -V /dev/sda:

Warning: partition 1 does not end at a cylinder boundary

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="D6FC1A87FC1A6253" TYPE="ntfs" 
/dev/sda2: UUID="117463c2-3ee9-40f6-82cb-7e7696054ed6" SEC_TYPE="ext2" TYPE="ext3" 
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

=========================== sda2/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=117463c2-3ee9-40f6-82cb-7e7696054ed6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=117463c2-3ee9-40f6-82cb-7e7696054ed6

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title         Windows Vista
root          (hd0,0)
savedefault
makeactive
chainloader   +1

#This is a divider, added to separate the menu items below from the Windows
# ones.
title		Other operating systems:
root

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		117463c2-3ee9-40f6-82cb-7e7696054ed6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=117463c2-3ee9-40f6-82cb-7e7696054ed6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		117463c2-3ee9-40f6-82cb-7e7696054ed6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=117463c2-3ee9-40f6-82cb-7e7696054ed6 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		117463c2-3ee9-40f6-82cb-7e7696054ed6
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=117463c2-3ee9-40f6-82cb-7e7696054ed6 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda2/boot: ==================================

total 12820
drwxr-xr-x  3 root root    4096 2009-01-04 15:59 .
drwxr-xr-x 20 root root    4096 2009-01-04 15:59 ..
-rw-r--r--  1 root root  503560 2008-10-24 07:55 abi-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-10-24 07:55 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-04 15:59 grub
-rw-r--r--  1 root root 8656628 2009-01-04 15:59 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-10-24 07:55 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-10-24 07:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-10-24 07:55 vmlinuz-2.6.27-7-generic

=============================== sda2/boot/grub: ===============================

total 216
drwxr-xr-x 2 root root   4096 2009-01-04 15:59 .
drwxr-xr-x 3 root root   4096 2009-01-04 15:59 ..
-rw-r--r-- 1 root root    197 2009-01-04 15:59 default
-rw-r--r-- 1 root root     15 2009-01-04 15:59 device.map
-rw-r--r-- 1 root root   8108 2009-01-04 15:59 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-04 15:59 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-04 15:59 installed-version
-rw-r--r-- 1 root root   8712 2009-01-04 15:59 jfs_stage1_5
-rw-r--r-- 1 root root   4524 2009-01-04 16:27 menu.lst
-rw-r--r-- 1 root root   7352 2009-01-04 15:59 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-04 15:59 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-04 15:59 stage1
-rw-r--r-- 1 root root 121460 2009-01-04 15:59 stage2
-rw-r--r-- 1 root root   9556 2009-01-04 15:59 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

Thanks for your help, please help me @ all!
Abhischek

---

### Post by caljohnsmith on 2009-01-05
According to the results, your only NTFS partition (sda1) that could hold Vista does not have Vista's boot files, so that's why you would get the "BOOTMGR missing" error; but of more concern is the script could not identify sda1 as a valid Vista installation. How about posting the output of:
```
sudo mount /dev/sda1 /mnt && ls -l /mnt
```
And we can work from there.

---

### Post by Abhischek Thottakara on 2009-01-05
Hi here are the results!

```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt && ls -l /mnt
total 44
drwxrwxrwx 1 root root     0 2006-11-02 15:42 Documents and Settings
drwxrwxrwx 1 root root  8192 2009-01-04 14:03 ProgramData
drwxrwxrwx 1 root root     0 2009-01-05 01:45 System Volume Information
drwxrwxrwx 1 root root     0 2009-01-05 01:45 Temp
drwxrwxrwx 1 root root  4096 2009-01-04 14:03 Users
drwxrwxrwx 1 root root 32768 2009-01-04 14:10 Windows
ubuntu@ubuntu:~$ 
```

And I am not sure if it helps you but my friend told me that he saw something like this as I booted right after I used those MBR restore commands in Live- CD session. A black screen saying "MBR 123FA" and he said that he could only press the Power- Off button and then I used "SuperGRUBDISK".

Again thanks

Abhischek

---

### Post by caljohnsmith on 2009-01-05
OK, it looks like you might be missing some more of your Vista system files/directories other than just your Vista boot files, but we can try replacing the boot files and see if that works. So first, how about downloading the [vista_boot_files.tar.gz]("http://www.keepandshare.com/doc/view.php?id=785254&da=y") file to your Ubuntu desktop, and then do:
```
sudo mount /dev/sda1 /mnt
cd ~/Desktop
sudo tar xvf vista_boot_files.tar.gz
sudo mv bootmgr Boot /mnt
ls -l /mnt
```
Please post the output of that last "ls" command above so I can check that it went OK. Then boot your Vista CD, go to the command line, and do like you did previously:
```
bootrec /rebuildbcd
```
Also, I would recommend running:
```
chkdsk /r
```
And run that as many times as it takes until it reports no errors. Then reboot, and let me know exactly what happens; we can work from there. :)

CREDITS: Many thanks to forum member meierfra for providing the Vista boot files.

---

### Post by Abhischek Thottakara on 2009-01-05
Hi sorry I am stuck with the first command!

```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
fuse: mount failed: Device or resource busy
```

What should I do know?

Abhischek

---

### Post by caljohnsmith on 2009-01-05
That should be OK, because you probably still have sda1 mounted on /mnt where it needs to be for the rest of the commands. Just continue with the rest of the commands and post the output of last "ls" command, and you should be fine.

---

### Post by Abhischek Thottakara on 2009-01-05
As you requested the output, I will try it out know so I will be offline for some minutes. I`ll post the results. 

```
ubuntu@ubuntu:~/Desktop$ ls -l /mnt
total 484
drwxrwxrwx 1 root root   4096 2008-01-09 21:32 Boot
-rwxrwxrwx 1 root root 443912 2008-01-09 15:22 bootmgr
drwxrwxrwx 1 root root      0 2006-11-02 15:42 Documents and Settings
drwxrwxrwx 1 root root   8192 2009-01-04 14:03 ProgramData
drwxrwxrwx 1 root root      0 2009-01-05 01:45 System Volume Information
drwxrwxrwx 1 root root      0 2009-01-05 01:45 Temp
drwxrwxrwx 1 root root   4096 2009-01-04 14:03 Users
drwxrwxrwx 1 root root  32768 2009-01-04 14:10 Windows
```

Thanks in advance!
Abhischek

---

### Post by Abhischek Thottakara on 2009-01-05
Hi sry for late reply, but Startup Repair took ages.

So after I copied those files I rebooted my Laptop with the Vista CD inserted, the first thing I noticed was that it recognized my install as a Vista install which it did not before. So I selected the Windows Vista C: entry and went to Command & Prompt. Then I used the "bootrec /rebuildbcd" command which failed with the errormessage "Total identified Windows installations: 0" which was the same error i got before. But hoping it would work I rebooted and now the error message "BOOTMGR.." was gone instead the screen was black and automatically rebooted and I saw the Bios Startup Screen- then a Black Screen- Bios Startup Screen- ... Like a loop it went on "forever" restarting my laptop. Then I started the Vista Recovery CD againg doing all other two commands "bootrec /fixmbr, bootrec /fixboot" and finally because it did not work "Windows Startup Repair" which also did not work. This is the current situation now!

Thank you in advance
Abhischek

---

### Post by caljohnsmith on 2009-01-05
It's unfortunate that replacing Vista's boot files did not work, but it is not too surprising since it appears you could be missing more than just the boot files. I noticed in your first post that you borrowed a 32-bit Vista Recovery CD from a friend, but is your Vista install 32-bit or 64-bit? If you have a 64-bit install, you could instead download a 64-bit Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/") and try using that. But if your Vista is 32-bit, I think about your only remaining option is to save your files from the Vista partition and reinstall Vista. Good luck and let me know how it goes.

---

### Post by Abhischek Thottakara on 2009-01-05
Hmm.. yes my Vista is a 64-Bit installation. I am downloading right now, but it seems kinda weird to me that the 32- Bit Recovery CD recognizes the Vista Install but can't repair it. But still it is somekind of progress that it at least recognizes it. Thank you very much for your help, I will post again when download is finished. But how could the files be deleted, I never executed a command that would do so..?

I am grateful for every idea.
Thanks in advance
Abhischek

---

### Post by Abhischek Thottakara on 2009-01-05
The download is finished and I went to repair options again, this time "Startup- Repair" completed very fast but again with the error message "Identified Os:0", this really is annoying me because it recognizes my Vista install on C:. Then I tried "bootrec /rebuildbcd" which also ended with the output "Total identified Windows installations:0" but then I rememberd that I did not do chkdsk /r as you said. So now it is kinda stuck doing this: "Deleting an index entry from index $0 of file 25." I have no idea what that is, but as you said I'll try running chkdsk until it gives me no errors. 
[UPDATE] Ok that index deleting has finished now although it took very long now it is doing: " CHKDSK is verifying free space [stage 5 of 5] 45%. So I will start chkdsk after it finished again to see if it has removed all bad files, then I'll try the bootrec commands. I'm going to post then how it went.

Thanks
Abhischek

---

### Post by Abhischek Thottakara on 2009-01-05
Hi this is the last update for my case. Chkdsk also didn't work, because as I noticed right now my whole Vista Installation was wiped out. I do not know how or when, but it must have happened when I formatted my Ubuntu partition, somehow I must have checked Vista too. But all my Documents, Music, Software is gone. Only the Folders are left over somehow, that's why I thought Vista was still there. I do not know how that was possible but now I have to install Vista again. 
Still thank you very much for all your help and trying, I really really appreciate it.
Also thanks to forum user "meierfa".

For anyone who has the same problem like me but with a healthy Vista System, just follow "caljohnsmith's" instructions then restore Windows Vista bootloader.

Thanks for helping 
Abhischek

---

### Post by caljohnsmith on 2009-01-05
I'm really sorry to hear all your personal documents were wiped out with Vista, but have you by chance looked under the "Users" directory in the sda1 partition to see if there is anything there? You could check with:
```
sudo mkdir /media/sda1 && sudo mount /dev/sda1 /media/sda1
nautilus /media/sda1/Users &
```
Maybe that will have some of your documents, but it might be a long shot. Best of luck with the reinstall, and sorry there wasn't much we could do it looks like.

---

