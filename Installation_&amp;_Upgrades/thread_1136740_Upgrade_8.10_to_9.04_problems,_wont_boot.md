---
title: "Upgrade 8.10 to 9.04 problems, wont boot"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by foo-monger on 2009-04-25
Hi,
 
I hope someone can help me with this problem.  I am really new to Linux.
I had 8.10 working really well on my laptop and upgraded through update manager.  At first it said I could only do a partial upgrade then it down loaded over 800 updates.  When I rebooted I get the option to boot either with Windows or 8.10 but then it 'hangs' and says that something is missing.
I tried to resolve the problem with the Alternate Boot CD but it was too complicated for me to understand.

I have done what someone suggested on another thread and got this result.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcc6d2272

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   168,007,769   168,005,722   7 HPFS/NTFS
/dev/sda2         168,007,770   234,436,544    66,428,775   5 Extended
/dev/sda5         168,007,833   231,609,104    63,601,272  83 Linux
/dev/sda6         231,609,168   234,436,544     2,827,377  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="F610C94F10C9178F" TYPE="ntfs" 
/dev/sda5: UUID="3c61aadf-6077-4dd3-8f80-a16daab8fde5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="f998a919-b5d0-47c3-9a69-d71f177c3358" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== sda1: Location of files loaded by Grub: ===================


  14.2GB: boot/grub/stage2

=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=3c61aadf-6077-4dd3-8f80-a16daab8fde5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3c61aadf-6077-4dd3-8f80-a16daab8fde5

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

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		3c61aadf-6077-4dd3-8f80-a16daab8fde5
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=3c61aadf-6077-4dd3-8f80-a16daab8fde5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		3c61aadf-6077-4dd3-8f80-a16daab8fde5
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=3c61aadf-6077-4dd3-8f80-a16daab8fde5 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, memtest86+
uuid		3c61aadf-6077-4dd3-8f80-a16daab8fde5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=3c61aadf-6077-4dd3-8f80-a16daab8fde5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=f998a919-b5d0-47c3-9a69-d71f177c3358 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  86.3GB: boot/grub/menu.lst
  86.2GB: boot/grub/stage2
  86.3GB: boot/initrd.img-2.6.27-14-generic
  86.3GB: boot/vmlinuz-2.6.27-14-generic
  86.3GB: initrd.img
  86.3GB: vmlinuz
```


I hope this makes sense to someone because I had lots of stuff in Ubuntu that I dont want to loose.

Thanks in anticipation.

---

### Post by meierfra. on 2009-04-25
The 9.04 kernel did not get installed. Try this:


Boot from the LiveCD and open a terminal.Then


```
sudo mount /dev/sda5 /mnt
cd /mnt
sudo cp {/,}etc/resolv.conf
sudo mount --bind {/,}proc
sudo mount --bind {/,}sys
sudo mount --bind {/,}dev
sudo chroot /mnt
```

and at the new prompt

```
apt-get update
apt-get dist-upgrade

```
Post the whole content of the terminal.

---

### Post by foo-monger on 2009-04-26
Thanks for the help.

After the first part I get this.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ cd /mnt
ubuntu@ubuntu:/mnt$ sudo cp {/,}etc/resolv.conf
ubuntu@ubuntu:/mnt$ sudo mount --bind {/,}proc
ubuntu@ubuntu:/mnt$ sudo mount --bind {/,}sys
ubuntu@ubuntu:/mnt$ sudo mount --bind {/,}dev
ubuntu@ubuntu:/mnt$ sudo chroot /mnt
root@ubuntu:/# apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/universe Packages
Reading package lists... Done
root@ubuntu:/# ```

```



Then this.


   /etc/rc2.d/S28NetworkManager
   /etc/rc3.d/S28NetworkManager
   /etc/rc4.d/S28NetworkManager
   /etc/rc5.d/S28NetworkManager
 Adding system startup for /etc/init.d/NetworkManager ...
   /etc/rc2.d/S50NetworkManager -> ../init.d/NetworkManager
   /etc/rc3.d/S50NetworkManager -> ../init.d/NetworkManager
   /etc/rc4.d/S50NetworkManager -> ../init.d/NetworkManager
   /etc/rc5.d/S50NetworkManager -> ../init.d/NetworkManager

Setting up network-manager-gnome (0.7.1~rc4.1-0ubuntu2) ...
Installing new version of config file /etc/xdg/autostart/nm-applet.desktop ...
Installing new version of config file /etc/dbus-1/system.d/nm-applet.conf ...

Setting up notification-daemon (0.4.0-0ubuntu4) ...
notification-daemon: no process killed

Setting up odt2txt (0.4-1ubuntu2) ...

Setting up pidgin-libnotify (0.14-1ubuntu9) ...
Setting up pulseaudio-module-gconf (1:0.9.14-0ubuntu20) ...
Setting up pulseaudio-module-hal (1:0.9.14-0ubuntu20) ...
Setting up pulseaudio-module-x11 (1:0.9.14-0ubuntu20) ...
Setting up python-smbc (1.0.6-0ubuntu2) ...

Setting up redland-utils (1.0.8-1) ...
Setting up rhythmbox (0.12.0-0ubuntu4) ...

Setting up seahorse-plugins (2.26.1-0ubuntu1) ...

Setting up system-config-printer-common (1.1.3+git20090218-0ubuntu19.1) ...
Installing new version of config file /etc/dbus-1/system.d/newprinternotification.conf ...

Setting up totem-common (2.26.1-0ubuntu5) ...

Setting up totem-gstreamer (2.26.1-0ubuntu5) ...

Setting up totem-plugins (2.26.1-0ubuntu5) ...

Setting up totem (2.26.1-0ubuntu5) ...
Setting up vino (2.26.1-0ubuntu1) ...

Setting up xulrunner-1.9 (1.9.0.9+nobinonly-0ubuntu0.9.04.1) ...

Setting up xulrunner-1.9-gnome-support (1.9.0.9+nobinonly-0ubuntu0.9.04.1) ...

Setting up brltty (4.0~svn4301-0ubuntu4) ...
Installing new version of config file /etc/brltty/brltty-al.hlp ...
Installing new version of config file /etc/brltty/brltty-at.hlp ...
Installing new version of config file /etc/brltty/brltty-ba.hlp ...
Installing new version of config file /etc/brltty/brltty-bd.hlp ...
Installing new version of config file /etc/brltty/brltty-bl.hlp ...
Installing new version of config file /etc/brltty/brltty-bm.hlp ...
Installing new version of config file /etc/brltty/brltty-bn.hlp ...
Installing new version of config file /etc/brltty/brltty-cb.hlp ...
Installing new version of config file /etc/brltty/brltty-ec.hlp ...
Installing new version of config file /etc/brltty/brltty-eu.hlp ...
Installing new version of config file /etc/brltty/brltty-fs.hlp ...
Installing new version of config file /etc/brltty/brltty-ht.hlp ...
Installing new version of config file /etc/brltty/brltty-il.hlp ...
Installing new version of config file /etc/brltty/brltty-lt.hlp ...
Installing new version of config file /etc/brltty/brltty-mb.hlp ...
Installing new version of config file /etc/brltty/brltty-md.hlp ...
Installing new version of config file /etc/brltty/brltty-mn.hlp ...
Installing new version of config file /etc/brltty/brltty-tn.hlp ...
Installing new version of config file /etc/brltty/brltty-ts.hlp ...
Installing new version of config file /etc/brltty/brltty-tt.hlp ...
Installing new version of config file /etc/brltty/brltty-vd.hlp ...
Installing new version of config file /etc/brltty/brltty-vo.hlp ...
Installing new version of config file /etc/brltty/brltty-vr.hlp ...
Installing new version of config file /etc/brltty/brltty-vs.hlp ...
Installing new version of config file /etc/brltty/countries.cti ...
Installing new version of config file /etc/brltty/en-us-g2.ctb ...
Installing new version of config file /etc/brltty/fr-abrege.ctb ...
Installing new version of config file /etc/brltty/fr-integral.ctb ...
Installing new version of config file /etc/brltty/zh-tw-polyphone.cti ...
Installing new version of config file /etc/brltty/zh-tw-ucb.ctb ...
Installing new version of config file /etc/brltty/zh-tw.ctb ...
Installing new version of config file /etc/init.d/brltty ...
Installing new version of config file /etc/brltty.conf ...
update-initramfs: deferring update (trigger activated)

Setting up brltty-x11 (4.0~svn4301-0ubuntu4) ...
Installing new version of config file /etc/brltty/brltty-xw.hlp ...
Setting up evolution-indicator (0.1.13-0ubuntu1) ...

Setting up libmbca0 (0.0.4+bzr66-0ubuntu1) ...

Setting up mplayer (2:1.0~rc2-0ubuntu19) ...

Setting up quicktime-utils (2:1.1.0+debian-1build1) ...
Setting up xawtv-plugin-qt (3.95.dfsg.1-8.1ubuntu1) ...
Setting up language-support-translations-en (1:9.04+20090401) ...
Generating locales...
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NG.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.

Processing triggers for menu ...
Setting up firestarter (1.0.3-7ubuntu5) ...
Installing new version of config file /etc/firestarter/non-routables ...
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)

(firestarter:26500): GLib-CRITICAL **: g_ascii_strcasecmp: assertion `s1 != NULL' failed
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
Firewall script saved as /etc/firestarter/firewall
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
 * Stopping the Firestarter firewall...                                         (null): error fetching interface information: Device not found
(null): error fetching interface information: Device not found
(null): error fetching interface information: Device not found
                                                                         [ OK ]
 * Starting the Firestarter firewall...                                         (null): error fetching interface information: Device not found
(null): error fetching interface information: Device not found
(null): error fetching interface information: Device not found
                                                                         [fail]
invoke-rc.d: initscript firestarter, action "restart" failed.

Processing triggers for menu ...
Setting up xserver-xorg-core (2:1.6.0-0ubuntu14) ...

Setting up xserver-xorg-input-kbd (1:1.3.1-2ubuntu1) ...
Setting up libmono-security2.0-cil (2.0.1-4) ...
Setting up mono-2.0-runtime (2.0.1-4) ...
Setting up mono-runtime (2.0.1-4) ...
Setting up libmagickwand1 (7:6.4.5.4.dfsg1-1ubuntu3) ...

Setting up libmagickcore1 (7:6.4.5.4.dfsg1-1ubuntu3) ...

Setting up rss-glx (0.8.2-1ubuntu3) ...
Setting up ubuntu-desktop (1.140) ...
Setting up soprano-daemon (2.2.2+dfsg.1-1ubuntu1) ...
Setting up libsoprano4 (2.2.2+dfsg.1-1ubuntu1) ...

Setting up kdelibs-bin (4:4.2.2-0ubuntu5) ...
Setting up kdelibs5 (4:4.2.2-0ubuntu5) ...

Setting up libxine1-misc-plugins (1.1.16.3-0ubuntu1) ...

Setting up libxine1 (1.1.16.3-0ubuntu1) ...

Setting up kdebase-runtime-bin-kde4 (4:4.2.2-0ubuntu1) ...
Setting up kdebase-runtime (4:4.2.2-0ubuntu1) ...

Setting up libplasma3 (4:4.2.2-0ubuntu5) ...

Setting up kdebase-workspace-libs4+5 (4:4.2.2-0ubuntu2) ...

Setting up indicator-messages (0.1.6-0ubuntu1) ...
Setting up kdebluetooth (1:0.3-0ubuntu4) ...
Setting up khelpcenter4 (4:4.2.2-0ubuntu1) ...
Setting up libmono1.0-cil (2.0.1-4) ...
Setting up xserver-xorg-video-voodoo (1:1.2.0-1ubuntu1) ...
Setting up xserver-xorg-video-vmware (1:10.16.5-2) ...
Setting up xserver-xorg-video-vesa (1:2.0.0-1ubuntu6) ...
Setting up xserver-xorg-video-v4l (1:0.2.0-1ubuntu5) ...
Setting up xserver-xorg-video-tseng (1:1.2.0-1ubuntu1) ...
Setting up xserver-xorg-video-trident (1:1.3.0-1ubuntu1) ...
Setting up xserver-xorg-video-tdfx (1:1.4.0-2) ...
Setting up xserver-xorg-video-sisusb (1:0.9.0-4) ...
Setting up xserver-xorg-video-sis (1:0.10.1-1) ...
Setting up xserver-xorg-video-siliconmotion (1:1.7.0-1) ...
Setting up xserver-xorg-video-savage (1:2.2.1-4ubuntu2) ...
Setting up xserver-xorg-video-s3virge (1:1.10.2-1) ...
Setting up xserver-xorg-video-s3 (1:0.6.1-1) ...
Setting up xserver-xorg-video-rendition (1:4.2.0.dfsg.1-2ubuntu1) ...
Setting up xserver-xorg-video-radeon (1:6.12.1-0ubuntu2) ...
Setting up xserver-xorg-video-r128 (6.8.0+git20090201.08d56c88-1) ...
Setting up xserver-xorg-video-openchrome (1:0.2.903+svn713-1ubuntu1) ...

Setting up xserver-xorg-video-nv (1:2.1.12-1ubuntu5) ...
Setting up xserver-xorg-video-neomagic (1:1.2.2-1) ...
Setting up xserver-xorg-video-mga (1:1.4.9.dfsg-3) ...
Setting up xserver-xorg-video-mach64 (6.8.0-3) ...
Setting up xserver-xorg-video-intel (2:2.6.3-0ubuntu9) ...

Setting up xserver-xorg-video-i740 (1:1.2.0-2) ...
Setting up xserver-xorg-video-i128 (1:1.3.1-2ubuntu1) ...
Setting up xserver-xorg-video-geode (2.11.1-1) ...
Setting up xserver-xorg-video-fbdev (1:0.4.0-3) ...
Setting up xserver-xorg-video-cirrus (1:1.2.1-3) ...
Setting up xserver-xorg-video-chips (1:1.2.1-1) ...
Setting up xserver-xorg-video-ark (1:0.7.1-1) ...
Setting up xserver-xorg-video-apm (1:1.2.1-1) ...
Setting up xserver-xorg-input-vmmouse (1:12.5.1-4ubuntu5) ...
Setting up xserver-xorg-input-wacom (1:0.8.2.2-0ubuntu2) ...
 Removing any system startup links for /etc/init.d/xserver-xorg-input-wacom ...
   /etc/rc2.d/S10xserver-xorg-input-wacom
   /etc/rc3.d/S10xserver-xorg-input-wacom
   /etc/rc4.d/S10xserver-xorg-input-wacom
   /etc/rc5.d/S10xserver-xorg-input-wacom

Setting up xserver-xorg-input-synaptics (0.99.3-2ubuntu4) ...
Setting up xserver-xorg-input-mouse (1:1.4.0-1) ...
Setting up xserver-xorg-input-evdev (1:2.1.1-1ubuntu4) ...
Setting up xserver-xorg (1:7.4~5ubuntu18) ...

Setting up xserver-xorg-video-ati (1:6.12.1-0ubuntu2) ...
Setting up libmono-system2.0-cil (2.0.1-4) ...
Setting up libmono-data-tds2.0-cil (2.0.1-4) ...
Setting up libmono-system-data2.0-cil (2.0.1-4) ...
Setting up libmono-sqlite2.0-cil (2.0.1-4) ...
Setting up libmono-posix2.0-cil (2.0.1-4) ...
Setting up libmono-sharpzip2.84-cil (2.0.1-4) ...
Setting up libmono-getoptions2.0-cil (2.0.1-4) ...
Setting up libmono-data2.0-cil (2.0.1-4) ...
Setting up mono-2.0-gac (2.0.1-4) ...
Setting up mono-gac (2.0.1-4) ...
* Installing 1 assembly from libflickrnet2.1.5-cil into Mono
* Installing 1 assembly from libgmime2.2a-cil into Mono
* Installing 1 assembly from libgnome-keyring1.0-cil into Mono
* Installing 7 assemblies from libmono-addins0.2-cil into Mono
* Installing 3 assemblies from libmono-addins-gui0.2-cil into Mono
* Installing 1 assembly from libndesk-dbus1.0-cil into Mono
* Installing 1 assembly from libndesk-dbus-glib1.0-cil into Mono
* Installing 1 assembly from policy.2.1.FlickrNet into Mono

Setting up libmono2.0-cil (2.0.1-4) ...
Setting up libglib2.0-cil (2.12.8-2) ...
Setting up libgconf2.24-cil (2.24.0-3ubuntu1) ...
Setting up libgmime2.2a-cil (2.2.22-2ubuntu1) ...
* Installing 1 assembly from libgmime2.2a-cil into Mono

Setting up libart2.24-cil (2.24.0-3ubuntu1) ...
Setting up libgtk2.0-cil (2.12.8-2) ...
Setting up libglade2.0-cil (2.12.8-2) ...
Setting up libgnome-vfs2.24-cil (2.24.0-3ubuntu1) ...
Setting up libgnome2.24-cil (2.24.0-3ubuntu1) ...
Setting up libgnomepanel2.24-cil (2.24.0-1ubuntu1) ...
Setting up libmono-addins0.2-cil (0.4-3) ...
* Installing 7 assemblies from libmono-addins0.2-cil into Mono

Setting up libmono-addins-gui0.2-cil (0.4-3) ...
* Installing 3 assemblies from libmono-addins-gui0.2-cil into Mono

Setting up libndesk-dbus1.0-cil (0.6.0-1ubuntu1) ...
* Installing 1 assembly from libndesk-dbus1.0-cil into Mono

Setting up tomboy (0.14.0-0ubuntu1) ...

Setting up libgnome-keyring1.0-cil (1.0.0~svn.r87622-2) ...
* Installing 1 assembly from libgnome-keyring1.0-cil into Mono

Setting up indicator-applet (0.1.6-0ubuntu1) ...

Setting up libmono-system-web2.0-cil (2.0.1-4) ...
Setting up libflickrnet2.1.5-cil (25277-6ubuntu4) ...
* Installing 1 assembly from libflickrnet2.1.5-cil into Mono

Setting up f-spot (0.5.0.3-1ubuntu6) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
Processing triggers for menu ...
root@ubuntu:/# 
```

```

Thanks.

---

### Post by foo-monger on 2009-04-26
After a restart the computer works fine and has 9.04 installed correctly.

Thank you very much for your advice.

Foo.:)

---

### Post by meierfra. on 2009-04-26
> After a restart the computer works fine and has 9.04 installed correctly.

Great.


> Thank you very much for your advice.

You are welcome.

---

### Post by djokela1 on 2009-04-26
Hi,
I'm also having a problem booting up after upgrading from 8.10 to 9.04 through the manager. Upon booting up, the Ubuntu load screen appears for a few seconds, and then it goes black and a bunch of text appears. Among that text are the following lines (roughly):

Mount: cannot setup loop device: no such file or directory
Mount: mounting /dev on /root/dev failed: no such file or directory
Mount: mounting /sys on /root/sys failed: no such file or directory
Mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have /sbin/init
No init found. Try passing init= bootarg

BusyBox v1.10.2 (Ubuntu [something]) built-in shell (ash)
Enter "Help" for a list of built-in commands
(initramfs)

I am then left with the (initramfs) prompt.

"Kernel 2.6.27-11-generic" is also displayed, if that helps with anything.

--

I am now running Ubuntu off a LiveCD. I tried entering the aforementioned code (sudo mount /dev/sda5 /mnt) and got "mount: special device /dev/sda5 does not exist"

Any thoughts?

Sorry if I should have posted this in a new thread. I'm brand new to Ubuntu, and this is my first post on ubuntuforums. I have a very shallow understanding of code, so please don't throw too much at me...

Thanks!

---

### Post by jmomandia on 2009-04-27
I got the same problem after upgrading from the web. I have no CD.

I get the following:


   -Check rootdelay= (did the system wait long enough?)
   -Check root= (did the system wait for the right device?
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sda5 does not exist. Dropping to a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)



Thanks!

---

### Post by djokela1 on 2009-04-27
> **jmomandia said:**
> I got the same problem after upgrading from the web. I have no CD.

I get the following:


   -Check rootdelay= (did the system wait long enough?)
   -Check root= (did the system wait for the right device?
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sda5 does not exist. Dropping to a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)



Thanks!
[COLOR=Black][jmomandia]("http://ubuntuforums.org/member.php?u=203865"), [/COLOR]I solved my problem! Right when Ubuntu is loading (before it get's to the graphical loacing screen) I am given an option to press ESC for more options along with a countdown from 8 seconds. I pressed ESC and got something like the following options:

Ubuntu 8.10, Kernel 2.6.27-14-generic
Ubuntu 8.10, Kernel 2.6.27-14-generic (recovery mode)
Ubuntu 8.10, Kernel 2.6.27-11-generic 
Ubuntu 8.10, Kernel 2.6.27-11-generic (recovery mode)

I chose the bottom one (Kernel with the lower last number, in recovery mode). At the next screen, there was an option to "Repair broken packages." I did that, it scrolled through a bunch of text installing packages and what not, and then I was brought back to the recovery mode menu. I clicked the first option (" boot Ubuntu normally" or something) and it went right into 9.04!

Sorry if this a bit imprecise, but I recalling it from memory. I hope this helps you!

---

### Post by TheAbyssDragon on 2009-04-27
> **meierfra. said:**
> Boot from the LiveCD and open a terminal.Then


```
sudo mount /dev/sda5 /mnt
cd /mnt
sudo cp {/,}etc/resolv.conf
sudo mount --bind {/,}proc
sudo mount --bind {/,}sys
sudo mount --bind {/,}dev
sudo chroot /mnt
```

and at the new prompt

```
apt-get update
apt-get dist-upgrade

```

I had this issue as well. Following the above commands (except using a different /dev) updated a bunch of packages and installed a few new ones without any errors. After reboot, it started up Jaunty without a problem. Thanks!

---

### Post by meierfra. on 2009-04-27
**jmomandia:**  Your problems seems to be different than the others in this thread. In order to get a clearer picture of your setup, I suggest to boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, (use the code tags)

---

### Post by leonbravo on 2009-05-21
Hi there,  

I've got the same sort of errors and I am trying the same solution.

I mounted sda3 where ubuntu is since I doing this at a private network some problems arise. 

First (not related) says : 

cp: not writing through dangling symlink `etc/resolv.conf'


Second, 

 Could not resolve 'security.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://mirror.optus.net/ubuntu/dists/jaunty-updates/Release.gpg](http://mirror.optus.net/ubuntu/dists/jaunty-updates/Release.gpg)  Could not resolve 'mirror.optus.net'

Thanks

---

### Post by peacechicken on 2009-06-29
> **meierfra. said:**
> The 9.04 kernel did not get installed. Try this:

Boot from the LiveCD and open a terminal.Then

```
sudo mount /dev/sda5 /mnt
cd /mnt
sudo cp {/,}etc/resolv.conf
sudo mount --bind {/,}proc
sudo mount --bind {/,}sys
sudo mount --bind {/,}dev
sudo chroot /mnt
```

and at the new prompt

```
apt-get update
apt-get dist-upgrade

```
Post the whole content of the terminal.

I tried this (actually just this part, because sudo cp {/,}etc/resolv.conf didn't work):
```
sudo mount /dev/sda1 /mnt
cd /mnt
apt-get update
apt-get dist-upgrade
```

It updated and installed a bunch of packages, but when I restarted it wouldn't even show my harddrive, it's no longer a boot option. It flashes some error screen about checking the drive cable. I never got that message before I tried the above commands.

Did something happen when I mounted the drive, and now I need to unmount it? And how would I do that when it no longer recognizes anything there?

I feel like the more I try to troubleshoot this problem, the worse it gets. I even tried to reinstall from the beginning, but couldn't because the partitioner couldn't find any drives.

I highly encourage people to NOT upgrade to 9.04!!!

---

### Post by visualdeception on 2009-06-29
Peacechicken I would try unmounting the drive

sudo -f umount

I think an error occurred in the upgrade screwing up your grub and/or your MBR. Do you have any other operating systems installed?

Also do you have a lot of data on your hard drive?

---

### Post by peacechicken on 2009-06-29
> **visualdeception said:**
> Peacechicken I would try unmounting the drive

sudo -f umount

I think an error occurred in the upgrade screwing up your grub and/or your MBR. Do you have any other operating systems installed?

Also do you have a lot of data on your hard drive?

Thanks, I'll try this tonight when I get home. What should I do next if the unmount is successful? Or what if it doesn't recognize anything there to unmount?

To answer your other questions -- no, there's other OS installed, and I do have some data I'd like to backup, otherwise I wouldn't be putting up such a fight. :-/

---

### Post by peacechicken on 2009-06-29
> **peacechicken said:**
> Thanks, I'll try this tonight when I get home. What should I do next if the unmount is successful? Or what if it doesn't recognize anything there to unmount?

"sudo -f umount" returns "illegal option -f" so I tried:
```
ubuntu@ubuntu:~$ sudo umount -f /dev/sda1
umount2: No such file or directory
umount: /dev/sda1: not found
```

---

### Post by visualdeception on 2009-06-29
What is your output if you 

```
sudo fdisk -l
```

---

### Post by peacechicken on 2009-06-29
sudo fdisk -l wasn't returning anything at all.

Good news is: I decided to open the case and re-attach the harddrive just in case it was a connection issue and sure enough -- I restarted the computer and it started up completely fine. I think one of the cables may have been slightly loose. We'll see if this latest theory holds true, depending on what happens when I decide to leave it alone for a bit. If it locks up again, I still have a problem and may be back here. But hopefully I fixed the core issue.

---

### Post by peacechicken on 2009-07-07
> **peacechicken said:**
> Good news is: I decided to open the case and re-attach the harddrive just in case it was a connection issue and sure enough -- I restarted the computer and it started up completely fine. I think one of the cables may have been slightly loose. We'll see if this latest theory holds true, depending on what happens when I decide to leave it alone for a bit. If it locks up again, I still have a problem and may be back here. But hopefully I fixed the core issue.

Nope, I was wrong, all the problems are back again. I'm gonna try to go back to 8.10, Jaunty Jackalope has been a total nightmare.

---

### Post by visualdeception on 2009-07-08
Is the connection to the hard drive loose again?

I wonder if this is somehow hardware related. Do you jar your computer, or is it anywhere that it could be accidently bumped?

Have you tried installing 9.04 on another computer?

---

### Post by peacechicken on 2009-07-10
> **visualdeception said:**
> Is the connection to the hard drive loose again?

I wonder if this is somehow hardware related. Do you jar your computer, or is it anywhere that it could be accidently bumped?

Have you tried installing 9.04 on another computer?

I'm now seriously wondering if my hard drive is failing. No it isn't moved around, hasn't been dropped or anything traumatic. The connection is fine, I just checked it again.

It makes a clicking sound randomly, every few minutes or so. Even clicked when I was running a live Linux Mint CD, which leads me to think it's not my Ubuntu install. I found [a YouTube video about harddrive clicks]("http://www.youtube.com/watch?v=vbq8vfs1wYY"), but flash isn't working on the Live CD I'm using now so I can't watch it. :-/

Before I go out and buy a new harddrive (or RMA my existing one) how can I verify it's *actually* failing? I'm hesitant only because I didn't have these problems until I upgraded to 9.04.

Is [this]("http://twitpic.com/8w574") evidence enough? Or [this]("http://twitpic.com/8w5kx")? 

Here's the harddrive I have: [http://www.newegg.com/Product/Product.aspx?Item=N82E16822144415](http://www.newegg.com/Product/Product.aspx?Item=N82E16822144415)

---

