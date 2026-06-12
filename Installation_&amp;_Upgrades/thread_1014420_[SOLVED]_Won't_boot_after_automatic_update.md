---
title: "[SOLVED] Won't boot after automatic update"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by arizonalarry2 on 2008-12-17
Hi everyone !

I bought a computer that came preloaded with 8.04 and used it for a few days when I noticed automatic updates weren't turned on so I activated the security and system updates . Booting up today I saw I had 129 packages to upgrade so I went ahead and they all downloaded and started installing .

During the installation process I was given a dialog screen that said something about keeping a current package or updating to the package maintainer's version and I chose update , the installations completed and now the computer won't boot . The package name was menu.lst .

While rebooting I can go into the grub menu and boot a recovery kernel and the text scrolls by until I get the ' SATA link down ' errors . Digging around I found a live 7.10 disc so I booted from that and I can see the hard drive just fine . Doing a sudo fdisk -l command also shows the drive .

I've only had the computer for a few days and I don't really have anything on it I want to save , would I be better off getting an 8.10 disc and doing a fresh install or can I do a quick fix on this ? Any help appreciated , thanks .

---

### Post by arizonalarry2 on 2008-12-18
No ideas?

Oh well, thanks anyway. I guess I'll just wipe the drive and install Feisty Fawn, I always had good luck with that one. 

Pretty bad when automatic updates kill the computer... just sayin'.

---

### Post by iponeverything on 2008-12-18
> **arizonalarry2 said:**
> No ideas?

Oh well, thanks anyway. I guess I'll just wipe the drive and install Feisty Fawn, I always had good luck with that one. 

Pretty bad when automatic updates kill the computer... just sayin'.

If your doing a clean install anyway, why not try 8.10?

---

### Post by caljohnsmith on 2008-12-18
Wait, you shouldn't need to reinstall for just a Grub menu.lst problem. In order to get a clearer picture of your setup, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```

cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info.txt' && sudo sh ./boot_info.txt
```
That will create a "BootInfo.txt" file on your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

---

### Post by arizonalarry2 on 2008-12-18
> **caljohnsmith said:**
> Wait, you shouldn't need to reinstall for just a Grub menu.lst problem. In order to get a clearer picture of your setup, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```

cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info.txt' && sudo sh ./boot_info.txt
```
That will create a "BootInfo.txt" file on your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.


Okay , will give that a try when I get home from work . Thanks !

---

### Post by arizonalarry2 on 2008-12-18
> **caljohnsmith said:**
> Wait, you shouldn't need to reinstall for just a Grub menu.lst problem. In order to get a clearer picture of your setup, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```

cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info.txt' && sudo sh ./boot_info.txt
```
That will create a "BootInfo.txt" file on your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.


Ran the command and ended up with an empty text file .


Here's the output from the command after I ran it a second time to try it again - 

ubuntu@ubuntu:~$ cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info.txt' && sudo sh ./boot_info.txt
--21:49:46--  [http://home.comcast.net/~ubuntu_grub/boot_info.txt](http://home.comcast.net/~ubuntu_grub/boot_info.txt)
           => `boot_info.txt.1'
Resolving home.comcast.net... 216.87.188.9
Connecting to home.comcast.net|216.87.188.9|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8,323 (8.1K) [text/plain]

100%[====================================>] 8,323         36.78K/s             

21:49:46 (36.75 KB/s) - `boot_info.txt.1' saved [8323/8323]

./boot_info.txt: 88: arith: syntax error: "i+1"
ubuntu@ubuntu:~/Desktop$ 



Here's the piece of code with the part that gives the arithmetic error -

Folder=/tmp/BootInfo
i=0
while (! sudo mkdir $Folder$i 2>/dev/null)
    do  
      i=$((i+1));
      wait;
    done
Folder=$Folder$i





Also here's the output from sudo fdisk -l if that's any help -

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1246    10008463+  83  Linux
/dev/hda2            1247        1371     1004062+  82  Linux swap / Solaris
/dev/hda3            1372        9729    67135635   83  Linux

---

### Post by caljohnsmith on 2008-12-18
Although it probably won't make any difference, how about trying with the script that was just updated today:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo sh ./boot_info_script.txt
```
If that doesn't work, then please post:
```
sudo mkdir /mnt/hda1 /mnt/hda3
sudo mount /dev/hda1 /mnt/hda1
sudo mount /dev/hda3 /mnt/hda3
ls -l /mnt/hda1 /mnt/hda3
ls -lR /mnt/hda1/boot /mnt/hda3/boot
cat /mnt/hda1/boot/grub/menu.lst
cat /mnt/hda3/boot/grub/menu.lst
```
And we can go from there.

---

### Post by arizonalarry2 on 2008-12-18
Yes , the first one yielded the same result with the arithmetic error .

Here's the output from the second one -

/mnt/hda1:
total 1228
drwxr-xr-x   2 root root    4096 2008-12-17 22:36 bin
drwxr-xr-x   3 root root    4096 2008-12-17 22:44 boot
lrwxrwxrwx   1 root root      11 2008-10-15 05:36 cdrom -> media/cdrom
drwxr-xr-x   4 root root    4096 2008-10-15 05:41 dev
drwxr-xr-x 125 root root   12288 2008-12-17 22:45 etc
-rw-rw-rw-   1 root root 1145192 2008-10-10 05:31 everex_gpc3_user_manual.pdf
drwxr-xr-x   2 root root    4096 2008-09-26 00:38 home
drwxr-xr-x   2 root root    4096 2008-04-22 21:50 initrd
lrwxrwxrwx   1 root root      33 2008-12-17 22:41 initrd.img -> boot/initrd.img-2.6.24-22-generic
lrwxrwxrwx   1 root root      33 2008-10-15 05:36 initrd.img.old -> boot/initrd.img-2.6.24-19-generic
drwxr-xr-x  16 root root   12288 2008-12-17 22:34 lib
drwx------   2 root root   16384 2008-09-26 00:38 lost+found
drwxr-xr-x   3 root root    4096 2008-12-17 22:04 media
drwxr-xr-x   2 root root    4096 2008-04-15 05:53 mnt
drwxr-xr-x   2 root root    4096 2008-04-22 21:50 opt
drwxr-xr-x   2 root root    4096 2008-04-15 05:53 proc
drwxr-xr-x  12 root root    4096 2008-10-15 05:43 root
drwxr-xr-x   2 root root    4096 2008-12-17 22:37 sbin
drwxr-xr-x   2 root root    4096 2008-04-22 21:50 srv
drwxr-xr-x   2 root root    4096 2008-04-19 05:05 sys
drwxrwxrwt  12 root root    4096 2008-12-17 22:44 tmp
drwxr-xr-x  12 root root    4096 2008-10-15 05:40 usr
drwxr-xr-x  15 root root    4096 2008-10-15 05:38 var
lrwxrwxrwx   1 root root      30 2008-12-17 22:41 vmlinuz -> boot/vmlinuz-2.6.24-22-generic
lrwxrwxrwx   1 root root      30 2008-10-15 05:36 vmlinuz.old -> boot/vmlinuz-2.6.24-19-generic

/mnt/hda3:
total 20
drwxr-xr-x 40 1000 1000  4096 2008-12-17 22:44 ensor
drwx------  2 root root 16384 2008-10-15 05:41 lost+found
ubuntu@ubuntu:~/Desktop$ ls -lR /mnt/hda1/boot /mnt/hda3/boot
ls: /mnt/hda3/boot: No such file or directory
/mnt/hda1/boot:
total 54172
-rw-r--r-- 1 root root  422607 2008-04-10 16:51 abi-2.6.24-16-generic
-rw-r--r-- 1 root root  422667 2008-08-21 04:46 abi-2.6.24-19-generic
-rw-r--r-- 1 root root  422838 2008-11-24 22:47 abi-2.6.24-22-generic
-rw-r--r-- 1 root root   79964 2008-04-10 16:51 config-2.6.24-16-generic
-rw-r--r-- 1 root root   80049 2008-08-21 04:46 config-2.6.24-19-generic
-rw-r--r-- 1 root root   80062 2008-11-24 22:47 config-2.6.24-22-generic
drwxr-xr-x 2 root root    4096 2008-12-17 22:42 grub
-rw-r--r-- 1 root root 7886210 2008-09-26 01:05 initrd.img-2.6.24-16-generic
-rw-r--r-- 1 root root 7350068 2008-04-22 22:01 initrd.img-2.6.24-16-generic.bak
-rw-r--r-- 1 root root 7496680 2008-12-14 10:32 initrd.img-2.6.24-19-generic
-rw-r--r-- 1 root root 7495717 2008-09-26 15:30 initrd.img-2.6.24-19-generic.bak
-rw-r--r-- 1 root root 7495842 2008-12-17 22:44 initrd.img-2.6.24-22-generic
-rw-r--r-- 1 root root 7495875 2008-12-17 22:41 initrd.img-2.6.24-22-generic.bak
-rw-r--r-- 1 root root  103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r-- 1 root root  899892 2008-04-10 16:51 System.map-2.6.24-16-generic
-rw-r--r-- 1 root root  905170 2008-08-21 04:46 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root  905617 2008-11-24 22:47 System.map-2.6.24-22-generic
-rw-r--r-- 1 root root 1904248 2008-04-10 16:51 vmlinuz-2.6.24-16-generic
-rw-r--r-- 1 root root 1921464 2008-08-21 04:46 vmlinuz-2.6.24-19-generic
-rw-r--r-- 1 root root 1921176 2008-11-24 22:47 vmlinuz-2.6.24-22-generic

/mnt/hda1/boot/grub:
total 204
-rw-r--r-- 1 root root    197 2008-10-15 05:41 default
-rw-r--r-- 1 root root     15 2008-09-26 01:05 device.map
-rw-r--r-- 1 root root   8056 2008-10-15 05:41 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-10-15 05:41 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-10-15 05:41 installed-version
-rw-r--r-- 1 root root   8608 2008-10-15 05:41 jfs_stage1_5
-rw-r--r-- 1 root root   5135 2008-12-17 22:42 menu.lst
-rw-r--r-- 1 root root   4580 2008-12-17 22:41 menu.lst~
-rw-r--r-- 1 root root   7324 2008-10-15 05:41 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-10-15 05:41 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-10-15 05:41 stage1
-rw-r--r-- 1 root root 108356 2008-10-15 05:41 stage2
-rw-r--r-- 1 root root   9276 2008-10-15 05:41 xfs_stage1_5
ubuntu@ubuntu:~/Desktop$ cat /mnt/hda1/boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=c8815cb6-c206-49c9-bae1-7bccc479208b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title           Ubuntu 8.04.1, kernel 2.6.24-22-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-22-generic root=UUID=c8815cb6-c206-49c9-bae1-7bccc479208b ro quiet splash
initrd          /boot/initrd.img-2.6.24-22-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-22-generic root=UUID=c8815cb6-c206-49c9-bae1-7bccc479208b ro single
initrd          /boot/initrd.img-2.6.24-22-generic

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=c8815cb6-c206-49c9-bae1-7bccc479208b ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=c8815cb6-c206-49c9-bae1-7bccc479208b ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04.1, kernel 2.6.24-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=c8815cb6-c206-49c9-bae1-7bccc479208b ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=c8815cb6-c206-49c9-bae1-7bccc479208b ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04.1, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by caljohnsmith on 2008-12-18
How about doing:
```
sudo blkid
```
And check that the UUID for hda1 is the same as "c8815cb6-c206-49c9-bae1-7bccc479208b", which is in your menu.lst. If that is correct, then your Ubuntu entries in the menu.lst are OK. If that is the case, I would go ahead with your plan of just doing a fresh install of 8.10. I think that's probably your best bet rather than spend lots of time troubleshooting your current install. Let me know what you decide to do or if you run into problems.

---

### Post by arizonalarry2 on 2008-12-18
> **caljohnsmith said:**
> How about doing:
```
sudo blkid
```
And check that the UUID for hda1 is the same as "c8815cb6-c206-49c9-bae1-7bccc479208b", which is in your menu.lst. If that is correct, then your Ubuntu entries in the menu.lst are OK. If that is the case, I would go ahead with your plan of just doing a fresh install of 8.10. I think that's probably your best bet rather than spend lots of time troubleshooting your current install. Let me know what you decide to do or if you run into problems.


No , the numbers are not the same as what is in menu.lst -

/dev/hda1: UUID="5aff23ed-5390-4e4e-9091-92ad66519781" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda3: UUID="f681980e-d1d1-4587-a9ff-0ca41fbe605b" SEC_TYPE="ext2" TYPE="ext3"

---

### Post by pietjanjaap on 2008-12-18
Try this:

In grub press "esc" and/or "e"
Then change de harddisk number.
Go one step back,
Then press "b" to boot.
Try a lot different harddisks numbers, (HD0,1) or  0,2 0,3 0,4 0,4
1,0 1,1 etc

If you find the wright one, then search for the file, menu.lst, open with gedit, and change de hd number, with the one you found,

---

### Post by caljohnsmith on 2008-12-18
> **arizonalarry2 said:**
> No , the numbers are not the same as what is in menu.lst -

/dev/hda1: UUID="5aff23ed-5390-4e4e-9091-92ad66519781" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda3: UUID="f681980e-d1d1-4587-a9ff-0ca41fbe605b" SEC_TYPE="ext2" TYPE="ext3"
OK, that is a problem then. While you still have hda1 mounted on /mnt/hda1, how about doing:
```
gksudo gedit /mnt/hda1/boot/grub/menu.lst
```
And copy/paste the UUID of hda1 given by blkid into your menu.lst entries for Ubuntu. Then reboot, and see if you get any further about booting Ubuntu.

---

### Post by arizonalarry2 on 2008-12-18
> **caljohnsmith said:**
> OK, that is a problem then. While you still have hda1 mounted on /mnt/hda1, how about doing:
```
gksudo gedit /mnt/hda1/boot/grub/menu.lst
```
And copy/paste the UUID of hda1 given by blkid into your menu.lst entries for Ubuntu. Then reboot, and see if you get any further about booting Ubuntu.

Okay , I copied the '5aff...' number into all the entries and saved the file . Going to try booting now , be back in a few minutes .

---

### Post by arizonalarry2 on 2008-12-18
Success ! It works ! Thank you thank you thank you !


You ROCK ! :guitar:

---

### Post by caljohnsmith on 2008-12-18
That's great news the UUID in your menu.lst was the only problem. One last detail I think you will want to take care of is to change the "kopt" line in your menu.lst to use the correct UUID, because that is probably why your menu.lst was updated incorrectly to begin with. If you correct the kopt line, then next time you get a kernel upgrade your menu.lst shouldn't break. The kopt line in your menu.lst should look like:
```
# kopt=root=UUID=[COLOR="Blue"]d5aff23ed-5390-4e4e-9091-92ad66519781[/COLOR] ro
```
Anyway, cheers and have fun with your Ubuntu install. :)

---

