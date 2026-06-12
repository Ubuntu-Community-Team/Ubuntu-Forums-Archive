---
title: "mount ntfs partition , dual boot with xp!!??"
date: 2008-07-12
forum: General Help
---

### Post by linuxn006 on 2008-07-12
Hi i installed Hardy ,had Xp installed already,i was hoping for a dual boot option..but was magiked when i saw ubuntu booting up and now i cant access my ntfs partitions.

below is what i get from sudo fdisk -l


Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f6d0f6c

   Device     Boot      Start         End      Blocks   Id  System

/dev/sda2       *          1        2433     19543041    f  W95 Ext'd (LBA)
/dev/sda5               1219        2002     6289888+    7  HPFS/NTFS
/dev/sda6               2002        2433     3462448+    7  HPFS/NTFS
/dev/sda7               1           747     6000183      83  Linux
/dev/sda8               748         808      489951     82  Linux swap/Solaris

Partition table entries are not in disk order

Can anybody ,tell me how to edit grub i.e. what should be the entry for my winXP hd(0,5) etc....entry for linux is hd(0,6)
I really need to access the data on my NTFS partitions =(

---

### Post by dracayr on 2008-07-12
hi,

in a terminal type:
```
sudo mkdir /mnt/windows1 /mnt/windows2
sudo mount /dev/sda5 /mnt/windows1
sudo mount /dev/sda6 /mnt/windows2
```

If those commands gave no output, you should be able to access your windows files by directing your file browser to /mnt/windows1 or /mnt/windows2. If they gave an output, post it here.

dracayr

---

### Post by sisco311 on 2008-07-12
```
gksu gedit /boot/grub/menu.lst
```
> title         Windows 
root          (hd0,5)
makeactive
chainloader   +1


---

### Post by nikgare on 2008-07-12
Can you please post your **/boot/grub/menu.lst** file please

---

### Post by linuxn006 on 2008-07-12
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 /mnt/windows2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 /mnt/windows2 ntfs-3g force 0 0


This is the output i get when i mounted as you suggested

---

### Post by linuxn006 on 2008-07-12
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=9f762b4b-13d6-4ef9-91c2-bf530d6147d2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=9f762b4b-13d6-4ef9-91c2-bf530d6147d2 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=9f762b4b-13d6-4ef9-91c2-bf530d6147d2 ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,6)
kernel        /boot/memtest86+.bin
quiet

title        Windows xp
root            (hd0,5)
makeactive
chainloader    +1

### END DEBIAN AUTOMAGIC KERNELS LIST


This is my menu.lst file the whole thingy :-P as nikgare requested.

Thanks a TONNE guys for responding.I am totally floored by the quick response you guys gave me.. =)

---

### Post by dexter.deepak on 2008-07-12
reboot your system, go to xp, shutdown xp properly..probably you hibernated there.

---

### Post by boblemur on 2008-07-12
this will mount your 2 drives into win1 and win2 folders inside /media

```

sudo mkdir /media/win1 
sudo mkdir /media/win2
sudo mount /dev/sda5 /media/win1 -t ntfs-3g -o force
sudo mount /dev/sda6 /media/win2 -t ntfs-3g -o force
```

and you can use (dont just copy paste, these are my values...):

```
UUID=7860829960825DAE /media/data   ntfs-3g defaults,force 0 0
UUID=4090C42C90C429EC /media/win    ntfs-3g defaults,force 0 0
```

as an /etc/fstab entry to mount them on boot

the strange UUID number can be found from sudo blkid

or /dev/sda5 should work also

---

### Post by boblemur on 2008-07-12
> **dexter.deepak said:**
> reboot your system, go to xp, shutdown xp properly..probably you hibernated there.

thats not always the case.... my dual boot locks my partitions anywayz, regardless of clean shutdown(just an annoying windows thing) iv neva found anything bad happening from force mounting... but id say it would really not like being woken from hibernation after this..

---

### Post by dexter.deepak on 2008-07-12
> **boblemur said:**
> thats not always the case.... my dual boot locks my partitions anywayz, regardless of clean shutdown(just an annoying windows thing) iv neva found anything bad happening from force mounting... but id say it would really not like being woken from hibernation after this..

well, i have only experienced mount failures in case of unclean shutdown. have you tried investigating into this matter of constant mount-failures ?
i dont know about ntfs, but i read somewhere that forced mounting defeats the entire piurpose of ext3 !!

to the OP i would advice to first try rebooting,if it yet fails then he may go for forced mount and only if that fails, he should go for editing /etc/fstab.

---

### Post by linuxn006 on 2008-07-12
> **dexter.deepak said:**
> reboot your system, go to xp, shutdown xp properly..probably you hibernated there.
No deepak i did not hibernate..And i CANT GO TO XP..thats the prob..i think you missed that :-)

---

### Post by boblemur on 2008-07-12
give what i said a go, at least then you can get to your files...but yes hes right, dont add to fstab unless you have to...

i just find that my windows locks itself... i dono why

your windows thing would be their in theory it appears on the boot list...

so you could try making the default windows, but then you may get stuck in windows and thats not good... because you cant change your grub settings from inside windows...

but what do you see when you boot?? do you have the list of things you can boot? the 3 linux's?

---

### Post by linuxn006 on 2008-07-12
yes i can see the 3 linux's i posted my menu.lst and i CAN boot the 3 linux's...the thing is i am not sure which partition has windows hd0,5  or hd0,4 etc.(barring the ones which have linux) ... so i am not sure what value should i give under #root.

I need to dual boot with windows as there are no linux drivers for my ADSL router and i dont have ethernet port :-P

---

### Post by dexter.deepak on 2008-07-12
i am sorry for misunderstanding the question.
now i can understand that you are getting no option for "booting" xp
i still cant understand whether you can "access" i.e mount/read/write to your ntfs partitions or not ..please make it clear.

---

### Post by boblemur on 2008-07-12
does windows show up on the list at all in grub??? because you can go 'e' and edit it and change the number at boot ( they are tmp changes)

this is why i said MOUNT it... so you can look inside the paritions and see which one you are aiming to mount...

---

### Post by borlosky on 2008-07-12
i'm having a similar issue, i dual booted xp and ubuntu, and can boot into both fine, but i have 2 physical hard drives, both 500 gig. the 1st hdd is partitioned into 4 partitions (1 for windows, 1 for ubuntu, 1 for swap for ubuntu, and 1 for storage.) the second hdd is all just one physical drive un-partitioned. when i boot to ubuntu however, i can access the windows partition, the ubuntu partition and the 500 gig hdd, but i can't access the 3rd partition on my main drive in ubuntu for some reason. it doesn't show up in my places/computer menus. but say i enable screenlets with hard drive monitors, i'm able to select that 3rd partition and see how much space is used, but still can't access any data or even see that the drive is there?

::edit:: all partitions (excluding swap and partition for ubuntu which are swap/ext3 respectively) are all ntfs for use with windows. and i can access ALL partitions fine in xp.

so in summation, i should see 4 partitions within ubuntu, but I am only seeing 3.

---

### Post by boblemur on 2008-07-12
the third parition being storage??

so its either ntfs? or fat? right?

run
```

sudo fdisk -l | grep '/dev/sda'
```

is the parition listed there??

or in:

```
sudo blkid
```

try find its /dev/sda* number... for eg 3 maybe...

---

### Post by borlosky on 2008-07-12
> **boblemur said:**
> the third parition being storage??

so its either ntfs? or fat? right?

run
```

sudo fdisk -l | grep '/dev/sda'
```

is the parition listed there??

or in:

```
sudo blkid
```

try find its /dev/sda* number... for eg 3 maybe...

yes 3rd partition is storage, and it's ntfs, i will have to try that when i get home, i'm at work right now.

---

### Post by boblemur on 2008-07-12
so if its ntfs and the number is say 3

/dev/sda3 is what you are trying to mount

to mount it once... 

```
sudo mkdir /media/win_storage
sudo mount /dev/sda3 /media/win_storage -t ntfs-3g
```

and if it says you can do it it... its ok to add -o force on the end

and if you want to add it to your fstab ( remba to backup first)

add..
```
/dev/sda3 /media/win_storage  ntfs-3g defaults 0 0
                              ntfs-3g defaults,force 0 0(to force it, dont if you dont need to)
```

---

### Post by linuxn006 on 2008-07-12
> **dexter.deepak said:**
> i am sorry for misunderstanding the question.
now i can understand that you are getting no option for "booting" xp
i still cant understand whether you can "access" i.e mount/read/write to your ntfs partitions or not ..please make it clear.

I installed hardy heron using "demo and installation" option on a seperate(not the winXP) partition.After installation i did not get the windows XP option in the boot menu..so i edited using "gedit" .But i am not sure which partition has windows if it is hd0,5 etc.,so i am not sure what value to enter under "root" in the "menu.list"I have posted my menu.list also the output of ::>

sudo fdisk -l

The main issue is that i cant boot my windows :(

---

### Post by dexter.deepak on 2008-07-12
so the problem is in grub, and all of us have been thinking about other issues till now:)
nyways, can you give me the link to your installation guide ? during installation, while partitioning, you have an option to make your / either primary/logical drive , i think you went for primary and thus you have such errors.

---

### Post by borlosky on 2008-07-12
> **boblemur said:**
> the third parition being storage??

so its either ntfs? or fat? right?

run
```

sudo fdisk -l | grep '/dev/sda'
```

is the parition listed there??

or in:

```
sudo blkid
```

try find its /dev/sda* number... for eg 3 maybe...

yes, the partition shows up in the both commands. here's the results:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
/dev/sda1   *           1        7139    57343986    7  HPFS/NTFS
/dev/sda2            7140       60801   431040015    f  W95 Ext'd (LBA)
/dev/sda5            7140       19887   102398278+   7  HPFS/NTFS
/dev/sda6           19888       22319    19535008+  83  Linux
/dev/sda7           22320       22562     1951866   82  Linux swap / Solaris
/dev/sda8           22563       60801   307154736    7  HPFS/NTFS

____________________________________________________________

/dev/sda1: UUID="AEE8D7B0E8D77555" TYPE="ntfs" 
/dev/sda5: UUID="C26C48AE6C489F53" LABEL="Games" TYPE="ntfs" 
/dev/sda6: UUID="1a35f873-39d2-44e5-a058-2bedcc21d030" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="039f24d8-460c-43f7-bbbc-94fc9106ae64" 
/dev/sda8: UUID="E0DC2450DC2422F0" LABEL="Storage" TYPE="ntfs" 
/dev/sdb1: UUID="D41C20C11C20A08A" LABEL="Music" TYPE="ntfs" 


the drive thats not accessible in ubuntu is /dev/sda8 (the one labeled "storage"

---

### Post by boblemur on 2008-07-12
so now try

```
sudo mkdir /mnt/storage
sudo mount /dev/sda8 /mnt/storage -t ntfs-3g
```

and if the second command fails use.. 

```
sudo mount /dev/sda8 /mnt/storage -t ntfs-3g -o force
```

that should give u access to it... and you can then add it to fstab later

---

### Post by borlosky on 2008-07-12
> **boblemur said:**
> so now try

```
sudo mkdir /mnt/storage
sudo mount /dev/sda8 /mnt/storage -t ntfs-3g
```

and if the second command fails use.. 

```
sudo mount /dev/sda8 /mnt/storage -t ntfs-3g -o force
```

that should give u access to it... and you can then add it to fstab later

tried both, the first command gave no errors, but i still don't see the drive any where, the second command gave me this error:

brandon@BeeMoney:~$ sudo mount /dev/sda8 /mnt/storage -t ntfs-3g -o force
fuse: mount failed: Device or resource busy

---

### Post by boblemur on 2008-07-12
if it worked it will be in /mnt/storage look in there and that should be the contence of the disk...

and if its their then you can add it to fstab so it gets loaded on boot...

---

### Post by borlosky on 2008-07-12
> **boblemur said:**
> if it worked it will be in /mnt/storage look in there and that should be the contence of the disk...

and if its their then you can add it to fstab so it gets loaded on boot...

yea, your totally right, it's there, and in file system/media, now how would i use fstab to mount it so i can get to it from places?

::edit:: actually double checking the contents, there's nothing in the folder? and there are files/folders present on the drive. but if i go to media folder in file system, there's now a disk labeled "storage" but clicking on it from there only bring up the windows partition i was previously able to get to

---

### Post by boblemur on 2008-07-12
hmmm thats strange


well you can go put this...

```
UUID=E0DC2450DC2422F0 /mnt/storage   ntfs-3g defaults,force 0 0
```


in your fstab( remember to backup fstab)

then run

```
sudo mount -a
```

or restart...

and if its not in your places menu already you can go...

into places > filesystem > mnt > storage >  then click bookmarks add bookmark and it should be in your places menu... its kinda a clumsy solution but should still work

---

### Post by borlosky on 2008-07-12
> **boblemur said:**
> hmmm thats strange


well you can go put this...

```
UUID=E0DC2450DC2422F0 /mnt/storage   ntfs-3g defaults,force 0 0
```


in your fstab( remember to backup fstab)

then run

```
sudo mount -a
```

or restart...

and if its not in your places menu already you can go...

into places > filesystem > mnt > storage >  then click bookmarks add bookmark and it should be in your places menu... its kinda a clumsy solution but should still work
 

actually i think i found what the issue was, looking at the file spaces on from the results from earlier, the correct drive should be /dev/sda5, i think the label somehow got mis-read (maybe something left over from formatting the drive in windows?) so corrected the previous line of code, and now it appears in the mnt folder and shows the correct contents:)... weird


now as far as fstab goes, i'm not familiar with using that or how to use it...still a linux noob :-(

---

### Post by boblemur on 2008-07-13
ok the fstab entry i said to add...



```
[COLOR="Red"]UUID=E0DC2450DC2422F0[/COLOR] [COLOR="Blue"]/mnt/storage[/COLOR]   [COLOR="SeaGreen"]ntfs-3g[/COLOR] [COLOR="Orange"]defaults,force[/COLOR] [COLOR="Black"]0 0[/COLOR]
```

ok well...

[COLOR="Red"]red[/COLOR] : is what you are mounting ( that number came from sudo blkid, but u can use /sda? if you want)

[COLOR="Blue"]blue[/COLOR]: where it gets mounted to

[COLOR="SeaGreen"]green[/COLOR]: the filesystem format... in this case ntfs ( note the -3g is not necessary but without it ntfs is read only)

[COLOR="Orange"]orange[/COLOR]: this add default options plus force mounts it in case windows didnt have a clean shutdown

black: im not sure what these do but iv always left them as 0 0

---

### Post by borlosky on 2008-07-13
> **boblemur said:**
> ok the fstab entry i said to add...



```
[COLOR="Red"]UUID=E0DC2450DC2422F0[/COLOR] [COLOR="Blue"]/mnt/storage[/COLOR]   [COLOR="SeaGreen"]ntfs-3g[/COLOR] [COLOR="Orange"]defaults,force[/COLOR] [COLOR="Black"]0 0[/COLOR]
```

ok well...

[COLOR="Red"]red[/COLOR] : is what you are mounting ( that number came from sudo blkid, but u can use /sda? if you want)

[COLOR="Blue"]blue[/COLOR]: where it gets mounted to

[COLOR="SeaGreen"]green[/COLOR]: the filesystem format... in this case ntfs ( note the -3g is not necessary but without it ntfs is read only)

[COLOR="Orange"]orange[/COLOR]: this add default options plus force mounts it in case windows didnt have a clean shutdown

black: im not sure what these do but iv always left them as 0 0

ok, so in this case i'd type:

/dev/sda5 /mnt/storage   ntfs-3g defaults,force 0 0

since i found the correct drive to be /dev/sda5 correct?

---

### Post by boblemur on 2008-07-13
/dev/sda1: UUID="AEE8D7B0E8D77555" TYPE="ntfs"
/dev/sda5: UUID="C26C48AE6C489F53" LABEL="Games" TYPE="ntfs"
/dev/sda6: UUID="1a35f873-39d2-44e5-a058-2bedcc21d030" TYPE="ext3"
/dev/sda7: TYPE="swap" UUID="039f24d8-460c-43f7-bbbc-94fc9106ae64"
/dev/sda8: UUID="E0DC2450DC2422F0" LABEL="Storage" TYPE="ntfs"
/dev/sdb1: UUID="D41C20C11C20A08A" LABEL="Music" TYPE="ntfs"


from this... you can either use /dev/sda5 or you can use UUID=C26C48AE6C489F53 for the first feild and the rest is fine yes :)

---

### Post by borlosky on 2008-07-13
> **boblemur said:**
> /dev/sda1: UUID="AEE8D7B0E8D77555" TYPE="ntfs"
/dev/sda5: UUID="C26C48AE6C489F53" LABEL="Games" TYPE="ntfs"
/dev/sda6: UUID="1a35f873-39d2-44e5-a058-2bedcc21d030" TYPE="ext3"
/dev/sda7: TYPE="swap" UUID="039f24d8-460c-43f7-bbbc-94fc9106ae64"
/dev/sda8: UUID="E0DC2450DC2422F0" LABEL="Storage" TYPE="ntfs"
/dev/sdb1: UUID="D41C20C11C20A08A" LABEL="Music" TYPE="ntfs"


from this... you can either use /dev/sda5 or you can use UUID=C26C48AE6C489F53 for the first feild and the rest is fine yes :)

ok, i've tried a few different things here, i've tried dev/sda5, and dev/sda8, but it seems which ever i change it to, i can see the missing drive, but it seems to take the place of the windows partition. (which i've allways been able to see) and looking closer at my fstab, is seems that the partition i'm trying to get working, and my windows partition are some how using the same directories: here's my fstab entries: (i've highlighted red to show the errors)

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=1a35f873-39d2-44e5-a058-2bedcc21d030 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda8 :
[COLOR="Red"]UUID=E0DC2450DC2422F0 /windows ntfs-3g defaults,locale=en_US.UTF-8 0 1[/COLOR]
# Entry for /dev/sda7 :
UUID=039f24d8-460c-43f7-bbbc-94fc9106ae64 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
[COLOR="Red"]/dev/sda1 /media/Storage ntfs-3g defaults,locale=en_US.UTF-8 0 0[/COLOR]
/dev/sdb1 /media/Music ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda5 /media/Games ntfs-3g defaults,locale=en_US.UTF-8 0 0


so my next question; should i try to change the "label" for those entries to try and correct this issue? ie; change:
UUID=E0DC2450DC2422F0 /windows ntfs-3g
to UUID=E0DC2450DC2422F0 /storage ntfs-3g

and change /dev/sda1 /media/Storage ntfs-3g defaults,locale=en_US.UTF-8 0 0
to /dev/sda1 /media/Windows ntfs-3g defaults,locale=en_US.UTF-8 0 0

---

### Post by dexter.deepak on 2008-07-13
> **borlosky said:**
> ok, i've tried a few different things here, i've tried dev/sda5, and dev/sda8, but it seems which ever i change it to, i can see the missing drive, but it seems to take the place of the windows partition. (which i've allways been able to see) and looking closer at my fstab, is seems that the partition i'm trying to get working, and my windows partition are some how using the same directories: here's my fstab entries: (i've highlighted red to show the errors)

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=1a35f873-39d2-44e5-a058-2bedcc21d030 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda8 :
[COLOR="Red"]UUID=E0DC2450DC2422F0 /windows ntfs-3g defaults,locale=en_US.UTF-8 0 1[/COLOR]
# Entry for /dev/sda7 :
UUID=039f24d8-460c-43f7-bbbc-94fc9106ae64 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
[COLOR="Red"]/dev/sda1 /media/Storage ntfs-3g defaults,locale=en_US.UTF-8 0 0[/COLOR]
/dev/sdb1 /media/Music ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda5 /media/Games ntfs-3g defaults,locale=en_US.UTF-8 0 0


so my next question; should i try to change the "label" for those entries to try and correct this issue? ie; change:
UUID=E0DC2450DC2422F0 /windows ntfs-3g
to UUID=E0DC2450DC2422F0 /storage ntfs-3g

and change /dev/sda1 /media/Storage ntfs-3g defaults,locale=en_US.UTF-8 0 0
to /dev/sda1 /media/Windows ntfs-3g defaults,locale=en_US.UTF-8 0 0

if you ahve got  a mount point as /media/Windows, you CAN mount your drive there. labels dont have to be taken care of.
i think you should edit your surrent fstab and edit this lime:
```
/dev/sda5 /mnt/storage ntfs-3g defaults,force 0 0
```to
```
/dev/sda5 /mnt/storage ntfs-3g defaults,rw,force 0 0
```

---

### Post by boblemur on 2008-07-13
the filesystem ntfs-3g is enabling rw by default i think...

from what i know.. thats the difference between ntfs and ntfs-3g

---

### Post by linuxn006 on 2008-07-13
Well..i didnt follow any web guide etc. deepak...yes i  used primary instead of logical.

So i dont have windows installed on my first drive,its in the last to be precise.

So do i get to reboot my original windows?Or do i have to install in linux using vmware etc. :(

---

### Post by linuxn006 on 2008-07-13
```
Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f6d0f6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        2433    19543041    f  W95 Ext'd (LBA)
/dev/sda5            1219        2002     6289888+   7  HPFS/NTFS
/dev/sda6            2002        2433     3462448+   7  HPFS/NTFS
/dev/sda7               1         747     6000183   83  Linux
/dev/sda8             748         808      489951   82  Linux swap / Solaris
```

From this i am guessing that windows is on sda6,so should the entry in grub"root" be (hd0,6),but then it would be the same as linux !!1:confused: (i have posted my menu.lst previously)

---

### Post by mempman on 2008-07-13
> **linuxn006 said:**
> ```
Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f6d0f6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        2433    19543041    f  W95 Ext'd (LBA)
/dev/sda5            1219        2002     6289888+   7  HPFS/NTFS
/dev/sda6            2002        2433     3462448+   7  HPFS/NTFS
/dev/sda7               1         747     6000183   83  Linux
/dev/sda8             748         808      489951   82  Linux swap / Solaris
```

From this i am guessing that windows is on sda6,so should the entry in grub"root" be (hd0,6),but then it would be the same as linux !!1:confused: (i have posted my menu.lst previously)

I think your winxp is on sda2 - since it has bootable flag.  Try editing your menu.lst file that you posted earlier, specifically, the window entry in that file should refer to sda2.  i.e.

> 
title Windows xp
root (hd0,1)  <-- referring to sda2...since grub numbers starting at 0.
makeactive
chainloader +1


---

### Post by linuxn006 on 2008-07-13
i have tried (hd0,1) to (hd0,6) before making this post,nothing seems to work :(

---

### Post by dexter.deepak on 2008-07-13
@boblemur
ntfs and ntfs-3g are both synonymous in hardy and both have default write permissions..i was asking for 'rw' only as a possible solution.

@mempman
since linuxn006 has installed ubuntu on a "primary" partition, the "extended" partition has turned to a "primary" and is now marked "active"
so the "*" you are seeing only tells that /dev/sda2 is now active and primary.
so windows (on /dev/sda1) is not being shown by fdisk

@linuxn006
honestly speaking , i have not yet faced a problem like this,but seems you have two methods :
1. try "root (hd0,0)" in grub.
2. you need to make the /dev/sda1 as "active" , probably a "fixmbr" through a windows cd could do it,as it will mark windows as "active",but dont try "fixboot" or your grub will be overwritten.

**** i am not sure if these methods will work perfectly for you..you may even lose ubuntu this way.

---

### Post by linuxn006 on 2008-07-13
I have tried (hd0,0) deepak,did not work,either i get error 12 or 22.I have one simple prob while using recovery [fixmbr],it asks me for admin password and i dont have one,leaving it blank does not work either :o

---

### Post by dexter.deepak on 2008-07-13
12 or 22 ?

---

### Post by linuxn006 on 2008-07-13
12

---

### Post by dexter.deepak on 2008-07-13
again i must remind you that i havent tried these stuff on my system, so there IS a risk of losing your "better" settings to "worse".

try this command:
```
sudo fdisk /dev/sda
```
give an option 'a' for changing the active flag
then it will ask for a partition number...give it 6 , as your windows is on /dev/sda6
then reboot.

---

### Post by dexter.deepak on 2008-07-13
^^ also try this both for root (hd0,0) and (hd0,5).

---

### Post by linuxn006 on 2008-07-14
I am sure its on sda6,from the size of partition.But,it still did not work yaar :P ,gives Error 12

---

