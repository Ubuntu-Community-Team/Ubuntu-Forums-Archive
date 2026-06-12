---
title: "Seperate home install 8.04 over a 6.06"
date: 2009-02-14
forum: Installation &amp; Upgrades
---

### Post by Dutch on 2009-02-14
Hi,

have Ubuntu 6.06 installed with a seperate /home

/dev/sda1  ntfs  15002 Mb (with Windows)
/dev/sda3  ext3  15002 Mb (running Ubuntu)
/dev/sda5  ext3  46003 Mb (data for Ubuntu= /home)
/dev/sda6  swap   1398 Mb (swap)
/dev/sda2  fat32  2623 Mb (W98 trubble shoot)

Oke starting up the 8.04 CD I arived at the partition thing, and really got stuck.
My goal is to just install the Ubuntu 8.04 on the sda3, leave the seperate home.
(oh upgrading is not an option, the sytem is ****** up :-)

---

### Post by frost151n on 2009-02-14
hey.
I think if you mount your sda5 as /home and DON'T format, you'll be fine.

Go manual, select sda3, select edit, choose '/' and check 'format' -Ok
select sda5 select edit, choose '/home' and UNcheck 'format' -Ok

Continue...

---

### Post by Dutch on 2009-02-14
Oke frost thanks, I'll try and let you know.

Mmmmm not everything went well.
After the HD instructions, I've checked the option "*Import settings and ....from 6.06*"

I wont bother you with losing the password.

But this is what I got:
All my earlyer settings are gone. My two Thunderbirds are gone and all the extra programms installed are gone. (don't bother, I've got them saved (Thank God for the 16Gb USB sticks :-)

Sda3 has indeed the program on it.
But the hda5 I have to find through system ==> HD ==> partitions
On the HDA5 are files named "root volume" and there are also the maps: bin,dev, etc, home (with the new account: paul, but totaly empty)
and also my old account, with my old desktop and the maps on that desktop.


What happened ?
Can I just remove the extra bin,dev,etc files on the hda5 ?

---

### Post by frost151n on 2009-02-15
So your problems are thus
1. Your sda5 will not mount automatically at bootup
2. Your sda5 is not your /home/(username)
3. There are files on your sda5 that should not be there
4. You have lost your settings and programs

Download [this]("http://sourceforge.net/project/downloading.php?group_id=250055&use_mirror=jaist&filename=boot_info_script024.sh&67504019") file. Then post the output of ```
sudo bash boot_info_script*.sh

```
This should shed light on the first 2 issues.

3- Maybe Ubuntu made those directories because you imported your settings. I have never in my life imported anything when installing Ubuntu so I don't really know what it does.

4- This I expected because we formated your sda3 which was necesary because you were installing 8.10 over 6.06. Good thing you have backups!!!

---

### Post by Dutch on 2009-02-15
Oke Frost,

thanks for replying.
Extra information: I've checked the version of Ubuntu.
I used the 8.04 edition and the 6.06 edition is installed :-)
I thought with copying the old settings my old programms would be saved.

Indeed I'm glad that the USB 18 Gb existst ! And I'm glad with a new start.
Indeed I asked help with a new install, not with a upgrade. (But next time you may notice that :-)

Oke, I downloaded your file, but what do I have to do to install it ?
Because when I use you're code it does not reconise the command.

Thanks.

---

### Post by Elfy on 2009-02-15
What problem do you actually have - while that script is useful in some situations - it gives a lot of information that probably is unnecessary.

> On the HDA5 are files named "root volume" and there are also the maps: bin,dev, etc, home (with the new account: paul, but totaly empty)
and also my old account, with my old desktop and the maps on that desktop.
This would imply to me that you didn't actually have a seperate home in the first place :)

Could you run these and post the outputs please

```
sudo fdisk -l
cat /etc/fstab
df -h
```

Copying the configs does just that - the program itself will still need to be installed.

---

### Post by Dutch on 2009-02-15
```

paul@Paul-IBM:~$ sudo fdisk -l
Password:

Schijf /dev/hda: 80.0 GB, 80032038912 bytes
255 koppen, 63 sectoren/spoor, 9730 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hda1   *           1        1824    14651248+   7  HPFS/NTFS
/dev/hda2            9412        9730     2562367+  1c  Verborgen W95 FAT32 (LBA)
/dev/hda3            1825        3648    14651280   83  Linux
/dev/hda4            3649        9411    46291297+   5  Uitgebreid
/dev/hda5            3649        9241    44925741   83  Linux
/dev/hda6            9242        9411     1365493+  82  Linux-swap / Solaris

Partitietabel ingangen zijn niet in schijfvolgorde

Schijf /dev/sda: 16.7 GB, 16777216000 bytes
253 koppen, 63 sectoren/spoor, 2055 cylinders
Eenheden = cylinders van 15939 * 512 = 8160768 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/sda1   *           1        2056    16383937    c  W95 FAT32 (LBA)

Schijf /dev/sdb: 16.7 GB, 16777216000 bytes
253 koppen, 63 sectoren/spoor, 2055 cylinders
Eenheden = cylinders van 15939 * 512 = 8160768 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/sdb1   *           1        2056    16383937    c  W95 FAT32 (LBA)

```

```

paul@Paul-IBM:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hda2       /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1/dev/hda3       /media/hda3     ext3    defaults        0       2
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
paul@Paul-IBM:~$


```

```

paul@Paul-IBM:~$ df -h
Bestandssysteem            Grtte  Gebr Besch Geb% Aangekoppeld op
/dev/hda5              43G   33G  7,9G  81% /
varrun                490M   80K  490M   1% /var/run
varlock               490M  4,0K  490M   1% /var/lock
udev                  490M  176K  490M   1% /dev
devshm                490M     0  490M   0% /dev/shm
lrm                   490M   19M  472M   4% /lib/modules/2.6.15-23-386/volatile
/dev/hda1              14G   11G  3,6G  75% /media/hda1
/dev/hda2             2,5G  2,3G  201M  92% /media/hda2
/dev/hda3              14G  2,2G   12G  17% /media/hda3
/dev/sda1              16G  7,6G  8,1G  49% /media/usbdisk
/dev/sdb1              16G  2,5G   14G  16% /media/BRIEVEN_USB
paul@Paul-IBM:~$

```

---

### Post by Elfy on 2009-02-15
Well I would say that you have installed over your old /home

> /dev/sda5 ext3 46003 Mb (data for Ubuntu= /home)

/dev/hda5       /               ext3    defaults,errors=remount-ro 0  1

Also does your fstab actually look like that?

```
/dev/hda2       /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1/dev/hda3 
``` or is it the way it has pasted?

You could double check - look at the menu.lst and compare the UUID

```
blkid
cat /boot/grub/menu.lst
```
IT should show UUID instead of root in the menu list. If you are not sure what you are looking at then post the blkid and menu, but I think it will confirm what I am thinking

---

### Post by Dutch on 2009-02-15
Thanks.
Need explanation, because the autcome is acacadabra to me :-(
```

paul@Paul-IBM:~$ blkid
/dev/hda6: TYPE="swap" UUID="99bf63ac-1256-488c-8892-070460ca596a"
/dev/sda1: UUID="C0EB-3A3B" TYPE="vfat"
/dev/sdb1: UUID="242F-DB2E" TYPE="vfat"
paul@Paul-IBM:~

```

```

paul@Paul-IBM:~$ cat /boot/grub/menu.lst
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# kopt=root=/dev/hda5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-53-386
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-53-386 root=/dev/hda5 ro quiet splash
initrd          /boot/initrd.img-2.6.15-53-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-53-386 (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-53-386 root=/dev/hda5 ro single
initrd          /boot/initrd.img-2.6.15-53-386
boot

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda5 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda5 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd0,4)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title           Ubuntu, kernel 2.6.15-27-686 (on /dev/hda3)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-27-686 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title           Ubuntu, kernel 2.6.15-27-686 (recovery mode) (on /dev/hda3)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-27-686 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.15-27-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title           Ubuntu, kernel 2.6.15-27-386 (on /dev/hda3)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title           Ubuntu, kernel 2.6.15-27-386 (recovery mode) (on /dev/hda3)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title           Ubuntu, kernel 2.6.15-26-686 (on /dev/hda3)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title           Ubuntu, kernel 2.6.15-26-686 (recovery mode) (on /dev/hda3)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.15-26-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title           Ubuntu, kernel 2.6.15-26-386 (on /dev/hda3)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title           Ubuntu, kernel 2.6.15-26-386 (recovery mode) (on /dev/hda3)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title           Ubuntu, memtest86+ (on /dev/hda3)
root            (hd0,2)
kernel          /boot/memtest86+.bin
savedefault
boot

paul@Paul-IBM:~$

```

Plus again the fstab

```

paul@Paul-IBM:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hda2       /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1/dev/hda3       /media/hda3     ext3    defaults        0       2
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
paul@Paul-IBM:~$

```

---

### Post by Elfy on 2009-02-15
As I thought your old /home partition has been overwritten by the install.

Your current menu boots on hda5 - which according to your first post is where you had your home.

So what issue do you actually have to deal with here?

---

### Post by Dutch on 2009-02-15
Thanks, so to keep this post oke for other readers, we conculde to don't use the:
> 
Go manual, select sda3, select edit, choose '/' and check 'format' -Ok
select sda5 select edit, choose '/home' and UNcheck 'format' -Ok


From the first reply on this issue.

My goals:

1. Keep the information from the old account: paulaccount
2. have a seperate root and home
3. Running on Ubuntu 8.04 with in the home the "old information" from 
    paulaccount.
4. Want tu use the EXT3 for Linux.
5. The other Windows parts must be untouched.
   ```

/dev/sda1 ntfs 15002 Mb (with Windows)
/dev/sda6 swap 1398 Mb (swap)
/dev/sda2 fat32 2623 Mb (W98 trubble shoot)

```

If something of my goals is not clear to you please let me know.

---

### Post by Elfy on 2009-02-15
OK well you can use [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) to deal with the maing of a new /home and getting it mounted - but if you've only just installed I would be inclined to start again if it was me. If you have downloaded all the updates you could also back them up and copy them when you are done.

> we conculde to don't use the:I have done this many many times and would suggest that possibly you made a mistake while doing it.

Indeed, if you didn't want to go through the psychocat how to then my suggestion would be to in fact do exactly that.

However that said your current install on hda5 si using 33Gb which would imply that the old data is there - unless you copied it from the stick.

---

### Post by Dutch on 2009-02-15
Thanks.
No I did not copy anything from the stick.
But what is on hda3 at this moment, if Ubuntu is installed on the hda5 ?
Because the hda3 has also the, bin, boot, dev, etc, home, initrd etc.

Oke, I'm with you about starting all over.
Can it be done with keeping the old info (paulaccount) on the hda5 and a frech install of Ubuntu 8.04 on the hda3 ?(because not everything could be copied to the USB stick)

And how do I manage that ?

---

### Post by Elfy on 2009-02-15
One more question then - are you saying that on your hda5 you currently have all your old /home data as well as the new install?

If that is the case then we can install to hda3 and call hda5 /home - it will also at that point have the old install on it - we can use that to get updates - save downloading them again.

If that is the case then - boot with the livecd and come back - I'm about for a good while now - also check your messages on the forum for a pm.

---

### Post by Dutch on 2009-02-15
red the private
If its oke with you I like to stay here. Because this install has nothing but my browser on it.

Maybe it is best if I gave you fisrt a ls of the HDA3 and the HDA5 so you can see what I've done and what is installed where ?

---

### Post by Elfy on 2009-02-15
yea ok - cool - do that before you boot the livecd and start the install again

---

### Post by Dutch on 2009-02-15
Ok, I'll try.

The system is really ****** up :-(
See you in 30 minutes: I've got to walk the dog (it's already 13:17 over here and the poor things has not has his morning walk :-()

I'll be back round 13:45 (Amsterdam time)

---

### Post by Elfy on 2009-02-15
If you can't get the information form the install - boot the livecd and we can get it there - just easier if you do it from the command line than trying to get nautilus and permissions going.

You could from the terminal do this

```
sudo mkdir /media/sda3 /media/sda5
sudo mount -t ext3 /dev/sda3 /media/sda3
sudo mount -t ext3 /dev/sda5 /media/sda5
```

---

### Post by Dutch on 2009-02-15
Oke I just used the first two lines of code

```

paul@Paul-IBM:~$ sudo mkdir /media/sda3 /media/sda5
Password:
paul@Paul-IBM:~$ sudo mount -t ext3 /dev/sda3 /media/sda3
mount: speciale apparaat /dev/sda3 bestaat niet
paul@Paul-IBM:~$

```

because of this outcome, I thought it is better to wait with the 3de code line
hda3 is located direct on the desktop of this new install.
I'm trying to find out where sda5 is located

==**bestaat niet**== means "*does not excist*" (Y'll get a free course in Dutch :-)

---

### Post by Elfy on 2009-02-15
Is this in the livecd? You only need to do that in there - the drives are apparently already mounted in the installed system.

It could also be that you need to use hda.

If you can get the information in the install do so - if not boot the livecd and tthen mount the 2 drives there from the command line.

This is in danger of getting to complicated for words :D

Basically all we need to do is to install to sda3 and have it use sda5 as your home.

---

### Post by Dutch on 2009-02-15
Oke I'll go after this post to the live CD.
Please give me the command to mount the sda3 and sda5 when I'm using the live CD.

I'm now going through the transformation of the live CD :-)
Hope to see u on the other side.

---

### Post by Elfy on 2009-02-15
In my previous post 18 - but try this 

```
sudo mkdir /media/hda3 /media/hda5
sudo mount -t ext3 /dev/hda3 /media/hda3
sudo mount -t ext3 /dev/hda5 /media/hda5
```

I'm a bit unsure as to why it's using hda - they should be reporting as sda

But not to worry

---

### Post by Dutch on 2009-02-15
Oke, give me some time to download a CD-burning programm.
So I can save the "paulaccount stuf" which I could not copy to the USB Stick.

Because if we are busy on the live CD  I want to be sure my letters and documents are safe(d)

---

### Post by Dutch on 2009-02-15
By copying extra stuf to the USB Stick the stick came on the great idea to overwrite it self.........

Seem to have lost the Thunderbird mails, ore are they still on the old account: paulaccount ?
Do you have an idea in what folder ?

---

### Post by Elfy on 2009-02-15
they could possibly be there - if they are they will be in ~/.mozilla-thunderbird

---

### Post by Dutch on 2009-02-15
> **forestpixie said:**
> they could possibly be there - if they are they will be in ~/.mozilla-thunderbird

Oke forest, seem to have lost 3.4 Gb of mail.
The In-mail does not matter, it's still on the mailserver.
But the send mail seem to be lost and that is ofcourse not saved on the mailserver.

I'm taking a pause here.

---

### Post by Elfy on 2009-02-15
You need to be sure that you are looking in the right place - it would seem from the information that I have that there are 2 installs - 1 is the old one which wasn't overwritten - the other is the 'new' one over the top of your original /home

There's no rush at all 

Hope you do manage to find your data

---

### Post by bulldog on 2009-02-15
Maybe you already know this,but I'm telling you anyway.:)
Don't use the same username and password for the new install as you used by the old ubuntu.
By creating a new username and password,there will be a new folder created on your /home,leaving the old one as it is.
By doing so,you can copy your data to the new account.

---

### Post by Elfy on 2009-02-15
I knew - we're at a bit of pickling up the pieces stage at the moment I think - looks to me like it went wrong yesterday

---

