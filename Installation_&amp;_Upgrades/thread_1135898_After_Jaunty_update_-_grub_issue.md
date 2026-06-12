---
title: "After Jaunty update - grub issue"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by telestrial on 2009-04-24
Hey. I am fairly new to linux so please bear with anything I say that seems false or messed up. Yesterday I checked my updates to see if Jaunty was out. I downloaded all the availible ones and then clicked the upgrade for the distribution. The installer ran and I rebooted, but nothing seemed different. Earlier today my update manager popped on and told me I had 816 new updates...so..I installed them. This changed my background and added adobe and all that, so I figured this was the distribution upgrade. At the end, I clicked on "restart required" and told it to continue. Upon restart, grub had "Ubuntu 8.10" listed. This was strange, but I pressed enter. When I did it started the ubuntu loader and the loading bar started doing it's thing. Suddenly, it kicked me into the shell and told me that the uuid didn't exist...or match..or whatever. I am guessing (and praying) that it's just a problem with grub not being able to recognize my hard drive. I used "Super Grub Disk" and used its automated fix feature, but this did not solve the problem. Nothing changed. However, I did learn that the IDE code thing is "hda6" and the SCSI id is "sda6". I browsed many forums and tried to edit grub to make it recognize the hard disk. I replaced the ```
root=uuid=X
``` with ```
root=/dev/sda6
```I have also tried "hda6"..
 
I use a Sony Vaio VGN-FW139E laptop. I dual boot with vista.
 
Any and all help would be much appreciated.

---

### Post by foo-monger on 2009-04-24
Hi,
Ive got exactly the same problem, but im obviously not as savvy as you, so any help would be appreciated as I dont want to loose all the stuff Ive got on 8.10.

Cheers in anticipation.

---

### Post by telestrial on 2009-04-24
I am unsure if bumps are allowed here. I haven't seen anything to the contrary...so...
 
 
::BUMP::

---

### Post by meierfra. on 2009-04-24
> I am unsure if bumps are allowed here.
bumps are allowed. But you should wait for 24 hours before bumping.


In order to get a clearer picture of your setup, I suggest to boot  from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by meierfra. on 2009-04-24
**foo-monger:**  Could you start a new thread with your problem? Trying to solve two cases in one thread can be very confusing. Feel free to send me  a PM with a  link to your new thread. Thanks.

---

### Post by telestrial on 2009-04-24
All worked out. Thanks for you help. Sorry about the bump. Here are the results:
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0f7f14c6

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    17,299,455    17,297,408  27 Hidden HPFS/NTFS
/dev/sda2    *     17,299,456   423,801,191   406,501,736   7 HPFS/NTFS
/dev/sda3         423,810,765   488,392,064    64,581,300   5 Extended
/dev/sda5         423,810,828   435,795,254    11,984,427  82 Linux swap / Solaris
/dev/sda6         435,795,318   488,392,064    52,596,747  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="6A02839A02836A41" LABEL="Recovery" TYPE="ntfs" 
/dev/sda2: UUID="AC1C474E1C4712AE" TYPE="ntfs" 
/dev/sda5: UUID="52030cd0-42f0-4b10-a87e-a2550fa774fc" TYPE="swap" 
/dev/sda6: UUID="8f45b3cf-2e1e-4647-8a2d-5001ac882729" SEC_TYPE="ext2" TYPE="ext3" 

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


=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=8f45b3cf-2e1e-4647-8a2d-5001ac882729 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8f45b3cf-2e1e-4647-8a2d-5001ac882729

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

title        Ubuntu 8.10, kernel 2.6.27-11-generic
uuid        8f45b3cf-2e1e-4647-8a2d-5001ac882729
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=8f45b3cf-2e1e-4647-8a2d-5001ac882729 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid        8f45b3cf-2e1e-4647-8a2d-5001ac882729
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=8f45b3cf-2e1e-4647-8a2d-5001ac882729 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10, memtest86+
uuid        8f45b3cf-2e1e-4647-8a2d-5001ac882729
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista/Longhorn (loader)
root        (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=8f45b3cf-2e1e-4647-8a2d-5001ac882729 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=52030cd0-42f0-4b10-a87e-a2550fa774fc none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda2 /media/WindowsHD ntfs-3g defaults,locale=en_US.UTF-8 0 0
#Entry for usbfs - Lexmark
usbfs /proc/bus/usb usbfs devgid=14,devmode=0660 0 0

=================== sda6: Location of files loaded by Grub: ===================


 228.6GB: boot/grub/menu.lst
 228.5GB: boot/grub/stage2
 228.6GB: boot/initrd.img-2.6.27-11-generic
 228.5GB: boot/vmlinuz-2.6.27-11-generic
 228.6GB: initrd.img
 228.5GB: vmlinuz

```

---

### Post by meierfra. on 2009-04-24
> All worked out.
??????

Does that mean you solved your problem?

Grub and fstab seem to be configured correctly, but you are still using the Ubuntu 8.10 kernels.  So if you are  still are having problems, I can show you how to chroot into Ubuntu and try to install the correct kernels.

---

### Post by telestrial on 2009-04-24
I meant your instructions were easy to read and worked out. I am still having my problem.

I noticed in grub it was pointing to 8.10..but I had no clue I was using the WRONG kernel.

Please guide me, wise one!

---

### Post by meierfra. on 2009-04-25
I'm puzzled why the new kernel did not get installed automatically. So instead of installing the kernel manually I suggest to run an update and see whether that installs the kernel.

Boot from the LiveCD and open a terminal.Then

```
sudo mount /dev/sda6 /mnt
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
apt-get upgrade

```
Post the whole content of the terminal.

```
exit
```

---

### Post by telestrial on 2009-04-25
apt-get update:
```
root@ubuntu:/# apt-get update
Hit http://archive.canonical.com jaunty Release.gpg
Ign http://archive.canonical.com jaunty/partner Translation-en_US
Get:1 http://archive.ubuntu.com jaunty Release.gpg [189B]
Ign http://archive.ubuntu.com jaunty/main Translation-en_US
Hit http://archive.canonical.com jaunty Release   
Ign http://archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://archive.ubuntu.com jaunty/multiverse Translation-en_US
Get:2 http://archive.ubuntu.com jaunty-updates Release.gpg [189B]
Ign http://archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Get:3 http://archive.ubuntu.com jaunty-security Release.gpg [189B]
Ign http://archive.ubuntu.com jaunty-security/main Translation-en_US
Ign http://archive.canonical.com jaunty/partner Packages
Ign http://archive.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://archive.canonical.com jaunty/partner Sources
Ign http://archive.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://archive.ubuntu.com jaunty-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com jaunty Release   
Hit http://archive.ubuntu.com jaunty-updates Release                
Hit http://archive.ubuntu.com jaunty-security Release               
Hit http://archive.canonical.com jaunty/partner Packages            
Hit http://archive.ubuntu.com jaunty/main Packages
Hit http://archive.canonical.com jaunty/partner Sources
Hit http://archive.ubuntu.com jaunty/restricted Packages
Hit http://archive.ubuntu.com jaunty/main Sources
Hit http://archive.ubuntu.com jaunty/restricted Sources
Hit http://archive.ubuntu.com jaunty/universe Packages
Hit http://archive.ubuntu.com jaunty/universe Sources
Hit http://archive.ubuntu.com jaunty/multiverse Packages
Hit http://archive.ubuntu.com jaunty/multiverse Sources
Hit http://archive.ubuntu.com jaunty-updates/main Packages
Hit http://archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://archive.ubuntu.com jaunty-updates/main Sources
Hit http://archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://archive.ubuntu.com jaunty-updates/universe Packages
Hit http://archive.ubuntu.com jaunty-updates/universe Sources
Hit http://archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://archive.ubuntu.com jaunty-updates/multiverse Sources
Hit http://archive.ubuntu.com jaunty-security/main Packages
Hit http://archive.ubuntu.com jaunty-security/restricted Packages
Hit http://archive.ubuntu.com jaunty-security/main Sources
Hit http://archive.ubuntu.com jaunty-security/restricted Sources
Hit http://archive.ubuntu.com jaunty-security/universe Packages
Hit http://archive.ubuntu.com jaunty-security/universe Sources
Hit http://archive.ubuntu.com jaunty-security/multiverse Packages
Hit http://archive.ubuntu.com jaunty-security/multiverse Sources
Fetched 567B in 1s (310B/s)
Reading package lists... Done
```apt-get upgrade:
```

root@ubuntu:/# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  aircrack-ng alsa-utils audacity bind9-host bluez brasero brltty brltty-x11
  capplets-data cheese compiz compiz-core compiz-fusion-plugins-extra
  compiz-fusion-plugins-main compiz-gnome compiz-plugins
  compizconfig-settings-manager cups deskbar-applet dmsetup dnsutils ekiga eog
  espeak espeak-data evince evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-exchange evolution-plugins
  evolution-webcal f-spot flashplugin-nonfree foo2zjs fuse-utils gdesklets
  gedit gedit-common ghostscript gimp gimp-data gnome-applets
  gnome-applets-data gnome-control-center gnome-keyring gnome-panel
  gnome-panel-data gnome-screensaver gnome-settings-daemon gnome-themes
  gnome-utils gparted grub gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-ugly gvfs gvfs-backends gvfs-bin gvfs-fuse hal hdparm
  hwtest hwtest-gtk ifupdown language-support-translations-en libavformat52
  libbind9-40 libcairo2 libcanberra-gtk-module libcanberra-gtk0 libcanberra0
  libcompizconfig0 libdjvulibre21 libdvdnav4 libecal1.2-7 libedata-cal1.2-6
  libeel2-2 libespeak1 libflickrnet2.1.5-cil libfuse2 libgimp2.0
  libgl1-mesa-dev libgl1-mesa-dri libgl1-mesa-glx libglade2.0-cil
  libglib2.0-cil libgnome-keyring1.0-cil libgnome-window-settings1
  libgnomecanvas2-0 libgnomecanvas2-common libgpod-common libgs8 libgtk2.0-cil
  libgtkhtml3.14-19 libgtkhtml3.16-cil libgtksourceview2.0-cil libgweather1
  libisccc40 libisccfg40 libjack0 liblwres40 libmbca0
  libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-corlib1.0-cil
  libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-security2.0-cil
  libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil
  libmono-system-runtime2.0-cil libmono-system-web1.0-cil
  libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil
  libmono-winforms2.0-cil libmono1.0-cil libmono2.0-cil libmtp8
  libndesk-dbus1.0-cil libnm-glib0 libpango1.0-0 libpangomm-1.4-1
  libqt4-assistant libqt4-dbus libqt4-designer libqt4-help libqt4-network
  libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg
  libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4
  libx11-6 libx11-dev libxcb-render0 libxcb1 libxcb1-dev linux-generic
  linux-headers-generic linux-image-generic linux-restricted-modules-generic
  lynx mesa-common-dev mono-2.0-devel mono-common mono-gac mono-gmcs mono-jit
  mono-runtime monodevelop monodoc-base monodoc-browser mount nautilus
  nautilus-data network-manager network-manager-gnome ntfs-3g nvidia-common
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-gnome
  openoffice.org-gtk openoffice.org-help-en-gb openoffice.org-help-en-us
  openoffice.org-impress openoffice.org-l10n-en-gb openoffice.org-l10n-en-za
  openoffice.org-math openoffice.org-style-human openoffice.org-writer parted
  pcmciautils poppler-utils pulseaudio pulseaudio-esound-compat
  pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 python
  python-beagle python-cairo python-compizconfig python-gconf python-glade2
  python-gnome2 python-gnome2-desktop python-gnomecanvas python-gobject
  python-gtk2 python-gtksourceview2 python-minimal python-numeric
  python-pyorbit python-qt4 python-qt4-dbus python-uno qt4-qtconfig rhythmbox
  rss-glx seahorse-plugins shared-mime-info system-config-printer-common
  system-config-printer-kde tomboy totem totem-common totem-gstreamer
  totem-mozilla totem-plugins tracker tracker-search-tool tracker-utils
  ubuntu-desktop udev update-manager update-manager-core util-linux vino vlc
  vlc-nox xserver-xorg xserver-xorg-core xserver-xorg-input-evdev
  xserver-xorg-input-kbd xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-geode
  xserver-xorg-video-i128 xserver-xorg-video-i740 xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nv xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa
  xserver-xorg-video-vmware xserver-xorg-video-voodoo xulrunner-1.9
  xulrunner-1.9-gnome-support
0 upgraded, 0 newly installed, 0 to remove and 276 not upgraded.

```exit:
```
root@ubuntu:/# exit
exit
ubuntu@ubuntu:/mnt$ 

```

---

### Post by meierfra. on 2009-04-25
> The following packages have been kept back:


That's your problem. For some reason apt-get refuses to  install all  whose new packages. 

Follow the instructions from my previous post again, but instead of "apt-get upgrade" use

```
apt-get dist-upgrade
```

I'm not sure that this will make a difference, but it's worth a try.

---

### Post by telestrial on 2009-04-25
There was about 180 packages that needed upgraded...so...I'm doing that now. I'll keep you posted!

---

### Post by figjam on 2009-04-25
Having the same issue here.

However, I have uninstalled and reinstalled the kernels to no avail.

I also use the -rt kernel, but grub did not get updated with the new kernel.

All previous install attempts have been made with synaptic.

-G

---

### Post by meierfra. on 2009-04-25
**figjam** Could you start a new thread with your problem? Follow the direction from post 4 and post the RESULTS.txt in your new thread. Thanks.

---

### Post by telestrial on 2009-04-26
Hey. It all worked out! I'm running right from my HD now. Thank you very much for your help.


Would you mind telling me what you did with that chroot business ? How it works ?

---

### Post by meierfra. on 2009-04-26
> It all worked out!

That's great.

> Would you mind telling me what you did with that chroot business ? How it works ? 


"chroot"  is a way to log into your Ubuntu OS.  After "chroot /mnt" all the commands are executed by the programs installed on the Ubuntu partition, and not the programs on the LiveCD.

```
apt-get update
```

downloads information on all  available package in the repros.

```
apt-get dist-upgrade
```

upgrades all your installed packages to the newest version. For example since  you did not have the newest kernel, this downloaded and installed the newest kernel.


```
sudo cp {/,}etc/resolv.conf
sudo mount --bind {/,}proc
sudo mount --bind {/,}sys
sudo mount --bind {/,}dev
```

These commands   gave   the  Ubuntu OS in the chroot  access to  the  information about the hardware stored in the virtual file system of the LiveCD.  For example the first commands is needed  to   have a working Internet connection in the chroot.

---

### Post by figjam on 2009-04-26
> **figjam said:**
> Having the same issue here.

However, I have uninstalled and reinstalled the kernels to no avail.

I also use the -rt kernel, but grub did not get updated with the new kernel.

All previous install attempts have been made with synaptic.

-G

All sorted.
What worked for me in getting the new kernel into the boot menu:

```
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.old
sudo update-grub
```

Simply copying it did not help.

If you are happy it worked after a reboot, delete /boot/grub/menu.lst.old

-G

---

### Post by breakerr on 2009-05-22
Hello guys.......I'm having the same issue....after installing some update called NTUPDATE or so I got [B]ERROR 24: Attempt to access block outside partition  PRESS ANY KEY TO CONTINUE....

(_Needed to quote that days prior to this I tried to convert my EXT3 to EXT4 and that some of this BOOTINFOSCRIPT RESULT might have spanish parts because I loaded the live session in that language :s sorry_ )

[/B]  [COLOR="Red"]**I do not want to remake or touch the MBR because I have Windows7 and my Win-XP as primary boot option( each Operating System is in its own drive) I don't want to alter the boot sequence, but I cant access or enter my ubuntu 9.04 jaunty**.[/COLOR]

So I post here my RESULTS after I runned BOOTINFOSCRIPT: 


============================= **Boot Info Summary:** ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Lilo is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: tipo de sistema de ficheros 'ext4' desconocido

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 40.0 GB, 40020664320 bytes
255 cabezas, 63 sectores/pista, 4865 cilindros, 78165360 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0x9ae25047

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    74,862,899    74,862,837  83 Linux
/dev/sda2          74,862,900    78,156,224     3,293,325   5 Extended
/dev/sda5          74,862,963    78,156,224     3,293,262  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 40.0 GB, 40020664320 bytes
255 cabezas, 63 sectores/pista, 4865 cilindros, 78165360 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0xd372d372

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    78,161,919    78,159,872   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disco /dev/sdc: 250.0 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros, 488397168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0xef0cef0c

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   268,414,019   268,413,957   7 HPFS/NTFS
/dev/sdc2         268,414,020   488,392,064   219,978,045   f W95 Ext d (LBA)
/dev/sdc5         268,414,083   488,392,064   219,977,982   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="2c9d8468-93ee-4852-a6f1-bce629a83517" TYPE="ext4" 
/dev/sda5: UUID="dfbfe6ad-946c-4592-bbf8-9c621cf306e8" TYPE="swap" 
/dev/sdb1: UUID="1090DD9E90DD8A9C" TYPE="ntfs" 
/dev/sdc1: UUID="E8F421C8F4219A38" TYPE="ntfs" 
/dev/sdc5: UUID="2E44552D4454F8D3" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sdc1/boot.ini: ================================

[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo/sdc1: dispositivo ocupado
umount: /tmp/BootInfo/sdc1: dispositivo ocupado

HELP PLZ!!!!
Thanks in advance and waiting for help to avoid reinstalling jaunty.

---

