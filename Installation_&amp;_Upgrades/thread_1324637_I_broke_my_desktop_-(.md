---
title: "I broke my desktop :-("
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by anandamide on 2009-11-12
I was being daft and fiddling around on my desktop while it downloaded all the files for 9.10. 

Leaving it with barely a min to go before finishing the dl, I wander off for a cup of tea, and return to find it hanging with the hard drive going nuts.

I leave it and eventually it calms down; no HD access, but also no movement on screen. Can't get a virtual terminal, can't ctrl-alt-backspace, and the network connection's gone so I can't even try a remote login.

With a degree of trepidation I turn it off and on again, to be greeted with the following (after GRUB)

```

init: procps main process (803) terminated with status 225
One or more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for recovery shell)
/: waiting for /dev/disk/by-uuid/diskid1
/tmp: waiting for (null)
/media/sda1: waiting for diskid2
/media/disk: waiting for diskid3
swap: waiting for diskid4
```

Even more worryingly, I can't bring up a terminal. For some reason I can't boot from CD despite telling the BIOS I want to (don't know if this problem is related, not tried to boot from CD in a while). I cannot access a recovery shell as it requires root privileges and in their infinite wisdom Canonical have removed the automatic root account.

I had been meaning to just to a quick upgrade then move on to finishing a report I have, but it's all gone a bit [XKCD]("http://xkcd.com/349/") :-/

---

### Post by anandamide on 2009-11-12
OK, fixed the boot-from-CD problem (was a completely different issue). So now I can log in to a session.

Any ideas? Anyone? I've checked the UIDs in fstab and they all match.

---

### Post by falconindy on 2009-11-12
You haven't really provided a whole lot of info to go on. Are you able to mount the disks from the live session? Any problems accessing them?

I'll make a guess that your comp hung during initramfs creation for a new kernel and that's why you can't boot. If you're able to mont your drives, what's in your /boot directory? Also, did you by chance run out of disk space?

---

### Post by whoop on 2009-11-12
> **anandamide said:**
> I was being daft and fiddling around on my desktop while it downloaded all the files for 9.10. 

Leaving it with barely a min to go before finishing the dl, I wander off for a cup of tea, and return to find it hanging with the hard drive going nuts.

I leave it and eventually it calms down; no HD access, but also no movement on screen. Can't get a virtual terminal, can't ctrl-alt-backspace, and the network connection's gone so I can't even try a remote login.

With a degree of trepidation I turn it off and on again, to be greeted with the following (after GRUB)

```

init: procps main process (803) terminated with status 225
One or more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for recovery shell)
/: waiting for /dev/disk/by-uuid/diskid1
/tmp: waiting for (null)
/media/sda1: waiting for diskid2
/media/disk: waiting for diskid3
swap: waiting for diskid4
```

Even more worryingly, I can't bring up a terminal. For some reason I can't boot from CD despite telling the BIOS I want to (don't know if this problem is related, not tried to boot from CD in a while). I cannot access a recovery shell as it requires root privileges and in their infinite wisdom Canonical have removed the automatic root account.

I had been meaning to just to a quick upgrade then move on to finishing a report I have, but it's all gone a bit [XKCD]("http://xkcd.com/349/") :-/

Wait, where you upgrading from 9.04 to 9.10 when something went wrong? If yes, anything interesting in /var/log/dist-upgrade/* (like "ERROR" with some info or something)?

---

### Post by anandamide on 2009-11-13
Thanks for the replies

I can mount the drives no problem in the live session. Googling the 'one or more mounts...' problem led me to try out sudo upgrade-grub. This changed the issue as now I just get a blank screen after selecting Ubuntu from grub, or a kernel panic message after selecting a recovery session.

Gimmie a sec and I'll get the extra info...

---

### Post by anandamide on 2009-11-13
Grr, wireless out under livecd :-/
Disk space not an issue, btw.

Here's a bit more info:

```
$ ls -R /media/disk/boot 

/media/disk/boot/:
abi-2.6.28-11-generic
abi-2.6.28-13-generic
abi-2.6.28-15-generic
abi-2.6.28-16-generic
abi-2.6.31-14-generic
config-2.6.28-11-generic
config-2.6.28-13-generic
config-2.6.28-15-generic
config-2.6.28-16-generic
config-2.6.31-14-generic
grub
initrd.img-2.6.28-11-generic
initrd.img-2.6.28-13-generic
initrd.img-2.6.28-15-generic
initrd.img-2.6.28-16-generic
memtest86+.bin
syslinux
System.map-2.6.28-11-generic
System.map-2.6.28-13-generic
System.map-2.6.28-15-generic
System.map-2.6.28-16-generic
System.map-2.6.31-14-generic
vmcoreinfo-2.6.28-11-generic
vmcoreinfo-2.6.28-13-generic
vmcoreinfo-2.6.28-15-generic
vmcoreinfo-2.6.28-16-generic
vmcoreinfo-2.6.31-14-generic
vmlinuz-2.6.28-11-generic
vmlinuz-2.6.28-13-generic
vmlinuz-2.6.28-15-generic
vmlinuz-2.6.28-16-generic
vmlinuz-2.6.31-14-generic

/media/disk/boot/grub:
53373-NightOfUbuntu.xpm
default
device.map
e2fs_stage1_5
fat_stage1_5
installed-version
jfs_stage1_5
menu.lst
menu.lst~
menu.lst.backup
minix_stage1_5
reiserfs_stage1_5
splashimages
stage1
stage2
xfs_stage1_5

/media/disk/boot/grub/splashimages:
53373-NightOfUbuntu.xpm.gz

/media/disk/boot/syslinux:
syslinux.cfg
```

```
$ sudo cat /media/disk/var/log/dist-upgrade/* |grep ERROR
ERROR: Couldn't stat '/var/lib/ufw/user.rules'

ERROR: Couldn't stat '/var/lib/ufw/user.rules'

ERROR: Couldn't stat '/var/lib/ufw/user.rules'

ERROR: Couldn't stat '/var/lib/ufw/user.rules'
ERROR: Couldn't stat '/var/lib/ufw/user.rules'
ERROR: Couldn't stat '/var/lib/ufw/user.rules'
```

And for good measure, here are the last few lines of /var/log/dist-upgrade/main.log:

```
2009-11-09 22:55:49,180 DEBUG plugins for condition 'StartUpgrade' are '[]'
2009-11-09 22:55:49,180 DEBUG plugins for condition 'karmicStartUpgrade' are '[]'
2009-11-09 22:55:49,181 DEBUG plugins for condition 'from_jauntyStartUpgrade' are '[]'
2009-11-09 22:55:49,181 DEBUG quirks: running StartUpgrade
2009-11-09 22:55:49,181 DEBUG check if patch '_usr_sbin_install-docs.268d21f1f1ed5f7a19fffef645ac4d52' needs to be applied
2009-11-09 22:55:49,190 DEBUG skipping 'README' (no '.')
2009-11-09 22:55:49,190 DEBUG check if patch '_usr_sbin_install-docs.3533d3b8e8f08f78c95550a7edcbe316' needs to be applied
2009-11-09 22:55:49,191 DEBUG killing update-notifier
2009-11-09 22:55:49,221 DEBUG killing kblueplugd kbluetooth4
2009-11-09 22:55:49,245 DEBUG killing gnome-screensaver
2009-11-09 22:55:49,298 INFO cache.commit()
2009-11-09 23:21:18,252 DEBUG got a conffile-prompt from dpkg for file: '/etc/modprobe.d/blacklist.conf'
ubuntu@ubuntu:~$ tail  /media/disk/var/log/dist-upgrade/main.log
2009-11-09 22:55:49,181 DEBUG plugins for condition 'from_jauntyStartUpgrade' are '[]'
2009-11-09 22:55:49,181 DEBUG quirks: running StartUpgrade
2009-11-09 22:55:49,181 DEBUG check if patch '_usr_sbin_install-docs.268d21f1f1ed5f7a19fffef645ac4d52' needs to be applied
2009-11-09 22:55:49,190 DEBUG skipping 'README' (no '.')
2009-11-09 22:55:49,190 DEBUG check if patch '_usr_sbin_install-docs.3533d3b8e8f08f78c95550a7edcbe316' needs to be applied
2009-11-09 22:55:49,191 DEBUG killing update-notifier
2009-11-09 22:55:49,221 DEBUG killing kblueplugd kbluetooth4
2009-11-09 22:55:49,245 DEBUG killing gnome-screensaver
2009-11-09 22:55:49,298 INFO cache.commit()
2009-11-09 23:21:18,252 DEBUG got a conffile-prompt from dpkg for file: '/etc/modprobe.d/blacklist.conf'
ubuntu@ubuntu:~$ tail /media/disk/var/log/dist-upgrade/main.log
2009-11-09 22:55:49,181 DEBUG plugins for condition 'from_jauntyStartUpgrade' are '[]'
2009-11-09 22:55:49,181 DEBUG quirks: running StartUpgrade
2009-11-09 22:55:49,181 DEBUG check if patch '_usr_sbin_install-docs.268d21f1f1ed5f7a19fffef645ac4d52' needs to be applied
2009-11-09 22:55:49,190 DEBUG skipping 'README' (no '.')
2009-11-09 22:55:49,190 DEBUG check if patch '_usr_sbin_install-docs.3533d3b8e8f08f78c95550a7edcbe316' needs to be applied
2009-11-09 22:55:49,191 DEBUG killing update-notifier
2009-11-09 22:55:49,221 DEBUG killing kblueplugd kbluetooth4
2009-11-09 22:55:49,245 DEBUG killing gnome-screensaver
2009-11-09 22:55:49,298 INFO cache.commit()
2009-11-09 23:21:18,252 DEBUG got a conffile-prompt from dpkg for file: '/etc/modprobe.d/blacklist.conf'

```

and /var/log/dist-upgrade/term.log

```
Setting up libbonobo2-0 (2.24.2-1) ...
Setting up libbonobo2-dev (2.24.2-1) ...
Setting up libx86-1 (1.1+ds1-4) ...
Setting up libusplash0 (0.5.49) ...
Setting up busybox-initramfs (1:1.13.3-1ubuntu7) ...
Setting up util-linux-locales (2.16-1ubuntu5) ...
Setting up libnewt0.52 (0.52.10-4ubuntu1) ...
Setting up whiptail (0.52.10-4ubuntu1) ...
Setting up module-init-tools (3.10-3) ...
Installing new version of config file /etc/modprobe.d/blacklist-watchdog.conf ...
Configuration file `/etc/modprobe.d/blacklist.conf'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ? Your options are:
    Y or I : install the package maintainer's version
    N or O : keep your currently-installed version
      D : show the differences between the versions
      Z : background this process to examine the situation
 The default action is to keep your current version.
*** blacklist.conf (Y/I/N/O/D/Z) [default=N] ?
```

So it would look like I hardly got anywhere with the actual upgrade.

---

### Post by anandamide on 2009-11-13
Here's /boot/grub/menu.lst for good measure:

```
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
timeout		10

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=b77f53e9-4b83-4565-9336-290b40a813ee ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
# defoptions=splash vga=795

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
# howmany=1

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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


splashimage=(hd0,1)/boot/grub/splashimages/53373-NightOfUbuntu.xpm.gz

title		Ubuntu 9.10, kernel 2.6.31-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=b77f53e9-4b83-4565-9336-290b40a813ee ro splash vga=795 
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=b77f53e9-4b83-4565-9336-290b40a813ee ro  single

title		Ubuntu 9.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by anandamide on 2009-11-14
[bump]

Anybody any more ideas?

---

