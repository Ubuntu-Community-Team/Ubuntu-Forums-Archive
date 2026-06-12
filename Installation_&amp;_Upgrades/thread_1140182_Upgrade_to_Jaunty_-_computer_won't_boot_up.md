---
title: "Upgrade to Jaunty - computer won't boot up"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by toastermm on 2009-04-27
I have a HPtx1000 (AMD X64), worked fantastic with Intrepid out of the box.  No problems.  I recently upgraded to Jaunty.

Well, the more correct action is that I clicked on "upgrade" and went through all the upgrading, rebooted... and... 

I get this text screen:

> 
Loading, please wait...
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/aa9024b5-abef-4c9a-9ff7-3e7765b78ac5 does not exist. Dropping to a shell!


BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)


And that's it.  Just sits there.  I am absolutely clueless what to do.  (I'm not very good with the command prompt).

I know that I can reinstall ubuntu with a disk- but I have some important work documents on the drive that I would like to have back.


Any ideas?

ps- I believe I have typed everything on the screen correctly.  I obviously can not cut and paste it since I can not use that computer.

---

### Post by Niniel on 2009-04-27
I had a similar experience when I upgraded my HP Pavilion laptop (Mobile P4 2.4 GHz). I my case, the system was unable to mount my /home partition which is on an SD card which in turn is in a Transcend USB adapter. 
I then booted using the old kernel and that worked fine.
And strangely, a couple of reboots later, when I forgot to switch kernels one time, it worked ok, with the new kernel too, so now I got rid of the old one and am only using the new one.
Maybe your system won't repair itself like that, but I figured it's worth a shot. 

Good luck.

---

### Post by toastermm on 2009-04-27
> I then booted using the old kernel and that worked fine.


how is that done?  I would not mind at all just using Intrepid.

---

### Post by toastermm on 2009-04-27
it won't even recognize sudo...

> 
(initramfs) sudo apt-get dist-upgrade
/bin/sh: sudo: not found
(initramfs) apt-get dist-upgrade
/bin/sh: apt-get: not found


I'm begining to think that the upgrade didn't finish before the reboot.  Somehow some important files got destroyed.  Uh oh.

---

### Post by brunogirin on 2009-04-27
When booting, while you see the counter that goes "booting in 2s... 1s... 0", press Esc to get to the GRUB menu and select the old kernel. See if this works.

---

### Post by toastermm on 2009-04-27
> **brunogirin said:**
> When booting, while you see the counter that goes "booting in 2s... 1s... 0", press Esc to get to the GRUB menu and select the old kernel. See if this works.

The short answer is no, this did not work.  Every other kernel I tried did actually bring me to a login screen- but the keyboard and mouse did not work, so I could not login.

I went into safe mode and tried to "fix broken packages" - and it did something, but I still can not boot up.

Have I lost my files?

---

### Post by Niniel on 2009-04-27
Not necessarily.
Just to save your files, you could burn yourself a live CD and see if you can access your hd that way, and then copy your home directory onto a USB stick. After that, if you don't want to continue to try fixing your current system anymore, you could install from scratch and then copy your files back afterwards.

---

### Post by toastermm on 2009-04-27
> **Niniel said:**
> Not necessarily.
Just to save your files, you could burn yourself a live CD and see if you can access your hd that way, and then copy your home directory onto a USB stick. After that, if you don't want to continue to try fixing your current system anymore, you could install from scratch and then copy your files back afterwards.

Sounds like a plan, I will let you know later today if it worked.

---

### Post by pablomolnar on 2009-04-27
> **toastermm said:**
> The short answer is no, this did not work.  Every other kernel I tried did actually bring me to a login screen- but the keyboard and mouse did not work, so I could not login.

I went into safe mode and tried to "fix broken packages" - and it did something, but I still can not boot up.

Have I lost my files?

I'm sure you haven't lost any files.
Try to boot in recovery mode with an old kernel and tell us if you can see your data with the shell

---

### Post by toastermm on 2009-04-27
> I'm sure you haven't lost any files.
Try to boot in recovery mode with an old kernel and tell us if you can see your data with the shell

Everytime I try booting with an old kernel, it actually does go to a login screen!  Which rocks...

Sadly, at the same time my mouse and keyboard do not work.  So I can not login.

---

### Post by pablomolnar on 2009-04-27
> **toastermm said:**
> Everytime I try booting with an old kernel, it actually does go to a login screen!  Which rocks...

Sadly, at the same time my mouse and keyboard do not work.  So I can not login.

Please try to select the **recovery option** in the grub menu (press ESC at boot time).
Then choose the option of log in as root and check if you can access your documents in the home folder of the normal user.

Wich version of kernels appears in the grub menu and wich one are you trying to boot the system?

---

### Post by toastermm on 2009-04-27
> Please try to select the recovery option in the grub menu (press ESC at boot time).
Then choose the option of log in as root and check if you can access your documents in the home folder of the normal user.


Ok- so I went in as a root user in a command prompt and was able to see the files- I still exist on that computer somewhere.

As to how to use a USB drive through a command prompt, I'm not entirely sure. (To transfer files off).

> Wich version of kernels appears in the grub menu and wich one are you trying to boot the system? 

Here is the list:

Ubuntu 9.04, kernel 2.6.27-11-server
Ubuntu 9.04, kernel 2.6.27-11-server (recovery mode)
Ubuntu 9.04, kernel 2.6.27-11-generic
Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
Ubuntu 9.04, kernel 2.6.24-22-server
Ubuntu 9.04, kernel 2.6.24-22-server (recovery mode)
Ubuntu 9.04, kernel 2.6.24-17-server
Ubuntu 9.04, kernel 2.6.24-17-server (recovery mode)
Ubuntu 9.04, kernel 2.6.24-17-rt
Ubuntu 9.04, kernel 2.6.24-17-rt (recovery mode)
Ubuntu 9.04, kernel 2.6.24-17-openvz
Ubuntu 9.04, kernel 2.6.24-17-openvz (recovery mode)


... I used the second one down from the top to enter recovery mode and see my files.

---

### Post by TreyKerux on 2009-04-27
I have a similar issue, except when I try and old kernel it just bring up a black screen with the white mouse cursor twirling.  (havent tried recovery mode of old kernel yet, will do that when I get home)
Booting from a live cd shows all my data is there, only problem I dont have another drive big enough to back up all my data. :-/

---

### Post by abn91c on 2009-04-27
```
exit
``` at the prompt

---

### Post by toastermm on 2009-04-27
> **abn91c said:**
> ```
exit
``` at the prompt
If I type "exit" at the prompt, here's what I get:

> 
(initramfs) exit
Loading, please wait...
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/aa9024b5-abef-4c9a-9ff7-3e7765b78ac5 does not exist. Dropping to a shell!


BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) 


was I supposed to get something else?

---

### Post by pablomolnar on 2009-04-27
> **toastermm said:**
> If I type "exit" at the prompt, here's what I get:



was I supposed to get something else?

There is a [know issue]("http://www.ubuntu.com/getubuntu/releasenotes/904#Boot%20failures%20on%20systems%20with%20Intel%20D945%20motherboards") with Intel D945 based motherboards. If you wait several minutes at the prompt and type exit and the boot continue right then that's your case but I think that you have another issue.

Please provide the result of these (all with root user):

```

fdisk -l
cat /etc/fstab
cat /boot/grub/menu.lst
blkid
ls /var/cache/apt/archives/linux-image*

```Also do you have connectivity at shell?
Try 
```

ping www.google.com

```To perform a backup to a usb drive you have to mount the usb device first. Try to determinate the device name and do something like this
```

mkdir /mnt/usb
mount /dev/sda1 /mnt/usb

```

---

### Post by abn91c on 2009-04-27
sometimes you have to type exit  couple if times

---

### Post by hzrunner on 2009-04-27
Hi Brunogirin. The same thing works for me for one of the kernels, but I have to do it now every time. Any idea how to change the file that selects the kernel?

---

### Post by toastermm on 2009-04-28
> **pablomolnar said:**
> There is a [know issue]("http://www.ubuntu.com/getubuntu/releasenotes/904#Boot%20failures%20on%20systems%20with%20Intel%20D945%20motherboards") with Intel D945 based motherboards. If you wait several minutes at the prompt and type exit and the boot continue right then that's your case but I think that you have another issue.

Please provide the result of these (all with root user):

```

fdisk -l
cat /etc/fstab
cat /boot/grub/menu.lst
blkid
ls /var/cache/apt/archives/linux-image*

```Also do you have connectivity at shell?
Try 
```

ping www.google.com

```To perform a backup to a usb drive you have to mount the usb device first. Try to determinate the device name and do something like this
```

mkdir /mnt/usb
mount /dev/sda1 /mnt/usb

```

Thanks for the reply!  Here is my output:

```

root@user:~# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa54f52ad

    Device Boot     Start     End     Blocks    ID  System
/dev/sda1    *         1     18662  149902483+  83  Linux
/dev/sda2          18663     19457    6385837+   5  Extended
/dev/sda5          18663     19457    6385806   82  Linux swap / Solaris

```

```

root@owner:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>  <dump>  <pass>
proc            /proc           proc    defaults   0       0
# /dev/sda1
UUID=aa9024b5-abef-4c9a-9ff7-3e7765b78ac5 /  ext3  relatime,error
s=remount-ro 0       1
# /dev/sda5
UUID=1a999c7f-3eb6-4f4a-9990-fb0561b3ffb4 none  swap  sw
  0       0
/dev/scd0     /media/cdrom0   udf,iso9660 user,noauto,exec,utf8  0  0
none  /proc/bus/usb   usbfs devgid=124,devmode=664  0  0

```

```

root@owner:~# cat /boot/grub/menu.lst
#menu.lst - See: grub(8), info grub, update-grub(8)
#           grub-install(8), grub-floppy(8),
#           grub-md5-crypt, /usr/share/doc/grub
#           and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM.  Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: if you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout    3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

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
# kopt=root=UUID=aa9024b5-abef-4c9a-9ff7-3e7765b78ac5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=fals

## should update grup lock alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

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
# altoptions=(revocery mode) single

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

## shouuld update-grub adust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title         Ubuntu 9.04, kernel 2.6.27-11-server
root          (hd0,0)
kernel        /boot/vmlinuz-2.6.27-11-server root=UUID=aa9024b5-abef-4c9a-9ff7-3e7765b78ac5 ro quiet splash
initrd        /boot/initrd.img-2.6.27-11-server
quiet

title         Ubuntu 9.04, kernel 2.6.27-11-server (recovery mode)
root          (hd0,0)
kernel        /boot/vmlinuz-2.6.27-11-server root=UUID=aa9024b5-abef-4c9a-9ff7-3e7765b78ac5 ro single
initrd        /boot/initrd.img-2.6.27-11-server

title         Ubuntu 9.04, kernel 2.6.27-11-generic
root          (hd0,0)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=aa9024b5-abef-4c9a-9ff7-3e7765b78ac5 ro quiet splash
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title         Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
root          (hd0,0)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=aa9024b5-abef-4c9a-9ff7-3e7765b78ac5 ro single
initrd        /boot/initrd.img-2.6.27-11-generic

title         Ubuntu 9.04, kernel 2.6.27-22-server
root          (hd0,0)
kernel        /boot/vmlinuz-2.6.27-22-server root=UUID=aa9024b5-abef-4c9a-9ff7-3e7765b78ac5 ro quiet splash
initrd        /boot/initrd.img-2.6.27-22-server
quiet

title         Ubuntu 9.04, kernel 2.6.27-22-server (recovery mode)
root          (hd0,0)
kernel        /boot/vmlinuz-2.6.27-22-server root=UUID=aa9024b5-abef-4c9a-9ff7-3e7765b78ac5 ro single
initrd        /boot/initrd.img-2.6.27-22-server

title         Ubuntu 9.04, kernel 2.6.24-17-server
root          (hd0,0)
kernel        /boot/vmlinuz-2.6.24-17-server root=UUID=aa9024b5-abef-4c9a-9ff7-3e7765b78ac5 ro quiet splash
initrd        /boot/initrd.img-2.6.24-17-server
quiet

title         Ubuntu 9.04, kernel 2.6.24-17-server (recovery mode)
root          (hd0,0)
kernel        /boot/vmlinuz-2.6.24-17-server root=UUID=aa9024b5-abef-4c9a-9ff7-3e7765b78ac5 ro single
initrd        /boot/initrd.img-2.6.24-17-server

title         Ubuntu 9.04, kernel 2.6.24-17-rt
root          (hd0,0)
kernel        /boot/vmlinuz-2.6.24-17-rt root=UUID=aa9024b5-abef-4c9a-9ff7-3e7765b78ac5 ro quiet splash
initrd        /boot/initrd.img-2.6.24-17-rt
quiet

title         Ubuntu 9.04, kernel 2.6.24-17-rt (recovery mode)
root          (hd0,0)
kernel        /boot/vmlinuz-2.6.24-17-rt root=UUID=aa9024b5-abef-4c9a-9ff7-3e7765b78ac5 ro single
initrd        /boot/initrd.img-2.6.24-17-rt

title         Ubuntu 9.04, kernel 2.6.24-17-openvz
root          (hd0,0)
kernel        /boot/vmlinuz-2.6.24-17-openvz root=UUID=aa9024b5-abef-4c9a-9ff7-3e7765b78ac5 ro quiet splash
initrd        /boot/initrd.img-2.6.24-17-openvz 
quiet

title         Ubuntu 9.04, kernel 2.6.24-17-openvz (recovery mode)
root          (hd0,0)
kernel        /boot/vmlinuz-2.6.24-17-openvz root=UUID=aa9024b5-abef-4c9a-9ff7-3e7765b78ac5 ro single
initrd        /boot/initrd.img-2.6.24-17-openvz

title         Ubuntu 9.04, kernel 2.6.24-17-generic
root          (hd0,0)
kernel        /boot/vmlinuz-2.6.24-17-generic root=UUID=aa9024b5-abef-4c9a-9ff7-3e7765b78ac5 ro quiet splash
initrd        /boot/initrd.img-2.6.24-17-generic
quiet

title         Ubuntu 9.04, kernel 2.6.24-17-generic (recovery mode)
root          (hd0,0)
kernel        /boot/vmlinuz-2.6.24-17-generic root=UUID=aa9024b5-abef-4c9a-9ff7-3e7765b78ac5 ro single
initrd        /boot/initrd.img-2.6.24-17-generic

title         Ubuntu 9.04, memtest86+
root          (hd0,0)
kernel        /boot/memtest86+.bin
quiet


```

```

root@owner:~# blkid
/dev/sda1: UUID="aa9024b5-abef-4c9a-9ff7-3e7765b78ac5" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="1a999c7f-3eb6-4f4a-9990-fb0561b3ffb4"

```

```

root@owner:~# ls /var/cache/apt/archives/linux-image*
/var/cache/apt/archives/linux-image-2.6.27-11-generic_2.6.27-11.31_amd64.deb
/var/cache/apt/archives/linux-image-2.6.27-11-server_2.6.27-11.31_amd64.deb

```

```

root@owner:~# ping www.google.com
ping: unknown host www.google.com

```
No connectivity!

Hrm, I will try the USB dump soon.

---

### Post by pablomolnar on 2009-04-28
Apparently the UUID is correct, the problem must be something else.
Maybe the upgrade proccess didnt finish before the reebot. Jaunty boots with kernel 2.6.28.11 and this kernel version is missing in grub menu and archives.

Normally these would help you
```

sudo aptitude update
sudo aptitude -f install
sudo dpkg --configure -a
sudo aptitude dist-upgrade

```

But if you don't have internet you can't performt these commands.

Try to choose another kernel in recovery mode to test internet connectivity.
If no one of the others kernels has put the result of this as root:
```

 lshw -C network
ifconfig -a
cat /etc/network/interfaces

```

---

### Post by toastermm on 2009-04-28
> **pablomolnar said:**
> Apparently the UUID is correct, the problem must be something else.
Maybe the upgrade proccess didnt finish before the reebot. Jaunty boots with kernel 2.6.28.11 and this kernel version is missing in grub menu and archives.

Normally these would help you
```

sudo aptitude update
sudo aptitude -f install
sudo dpkg --configure -a
sudo aptitude dist-upgrade

```

But if you don't have internet you can't performt these commands.

Try to choose another kernel in recovery mode to test internet connectivity.
If no one of the others kernels has put the result of this as root:
```

 lshw -C network
ifconfig -a
cat /etc/network/interfaces

```

Ok, thanks again, here's the output:

```

root@owner:~# lshw -C network
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33Mhz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb

```


```

root@owner:~# ifconfig -a
eth0       Link encap:Ethernet  HWaddr 00:1b:24:74:fc:7e
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carriers:0
           collisions:0 txqueuelen:1000
           RX bytes:0 (0.0B)  TX bytes:0 (0.0B)
           Interrupt:23 Base address:0xa000

eth0:avahi  Link encap:Ethernet  HWaddr 00:1b:24:74:fc:7e
           inet addr:169.254.8.38  Bcast:169.254.255.255  Mask:255.255.0.0
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           Interrupt:23 Base address:0xa000

lo         Link encap:Local Loopback
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:120 errors:0 dropped:0 overruns:0 frame:0
           TX packets:120 errors:0 dropped:0 overruns:0 carriers:0
           collisions:0 txqueuelen:0
           RX bytes:9504 (9.5B)  TX bytes:9504 (9.5B)


```

```

root@owner:~# cat /etc/network/interfaces
auto lo
iface lo inet loopback



iface ith0 inet dhcp
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0

```

If it is any help, I connect to my school wireless network through a user ID/passwork (VPN network).  I can also take the laptop to a non-vpn wireless (friends house) and connect there if that would help.

Also, I used to be able to connect with a ethernet cord without a vpn or password at school, but once linux got my wireless card working, it would never accept the ethernet cord for some reason.

I also made a Intrepid (v. 8.10) live CD, but for some reason it can not boot from that at all.

---

### Post by pablomolnar on 2009-04-28
Try this configuration in file /etc/network/interfaces

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```Connect direct thru a modem/router without VPN, proxy, firewall, etc

Then
```

/etc/init.d/networking restart

sudo aptitude update
sudo aptitude -f install
sudo dpkg --configure -a
sudo aptitude dist-upgrade

```None kernel has connectivity?

---

### Post by toastermm on 2009-04-29
> **pablomolnar said:**
> Try this configuration in file /etc/network/interfaces

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```Connect direct thru a modem/router without VPN, proxy, firewall, etc

Then
```

/etc/init.d/networking restart

sudo aptitude update
sudo aptitude -f install
sudo dpkg --configure -a
sudo aptitude dist-upgrade

```None kernel has connectivity?


Thank you again for the reply.

1- I edited the file to say exactly what is above.

I have connectivity, it is updating now.

Thank you.  I will let you know soon if it works.

---

### Post by toastermm on 2009-04-29
It worked, sort of.  I had connectivity, and it went through a whole lot of updates with those commands, and I am now able to bring up Jaunty. After I brought up Jaunty- I lost connectivity and use of my mouse, although my keyboard works.

So I dropped back to the bash prompt and redid what you suggested to test connectivity.

I checked /etc/network/interfaces, and here is what it is:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

Which is what it was when it was working.

Now when I run /etc/init.d/networking restart,
I get the following:
```

root@hobbes:/# /etc/init.d/networking restart
 *Reconfiguring network interfaces...
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp

SIOCSIFADDR: No such device
eth0: Error while getting interface flags: No such device
eth0: Error while getting interface flags: No such device
Failed to bring up eth0.

```

This is true for all kernels, recovery mode or not.

---

### Post by pablomolnar on 2009-04-29
Summarizing:

Working
 - Jaunty with Gnome (desktop environment)
 - Keyboard

Not working
 - Internet
 - Mouse

I'm right?

Display once again the result of this in Jaunty as root
```

lshw -C network
ifconfig -a
cat /etc/network/interfaces

```

Regarding the mouse issue maybe the quick fix is trying a generic usb mouse instead of the notebook integrated mouse .

---

### Post by toastermm on 2009-04-29
> **pablomolnar said:**
> Summarizing:

Working
 - Jaunty with Gnome (desktop environment)
 - Keyboard

Not working
 - Internet
 - Mouse

I'm right?

Regarding the mouse issue maybe the quick fix is trying a generic usb mouse instead of the notebook integrated mouse .

Correct.  I have tried a USB mouse- still doesn't work (plugging it in after boot up, and again before booting up).

```

root@owner:/# lshw -C network
  *-network UNCLAIMED
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Coporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33Mhz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

```

```

root@owner:/# ifconfig -a
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          Tx packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0B)  TX bytes:0 (0.0 B)

```

```

root@owner:/# cat /etc/network/interfaces
auto lo
iface lo inet loopback


auto eth0
iface eth0 inet dhcp

```

---

### Post by pablomolnar on 2009-04-29
Try this:
```

cd /lib/modules/`(uname -r)`/kernel/drivers/net/wireless/b43/
modprobe b43.ko
depmod -a
 /etc/init.d/networking restart
dhclient

```

Test internet.
If it doesn't work reboot Jaunty and check again internet.

---

### Post by toastermm on 2009-04-30
> **pablomolnar said:**
> Try this:
```

cd /lib/modules/`(uname -r)`/kernel/drivers/net/wireless/b43/
modprobe b43.ko
depmod -a
 /etc/init.d/networking restart
dhclient

```

Test internet.
If it doesn't work reboot Jaunty and check again internet.

Alright-

```

root@owner:/# cd /lib/modules//kernel/drivers/net/wireless/b43/
root@owner:/lib/modules//kernel/drivers/net/wireless/b43# modprobe b43.ko
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/dkms, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/fuse, it will be ignored in a future release.
FATAL: Module b43.ko not found.

```
Hmm... not found? so I did:

```

root@owner:/lib/modules//kernel/drivers/net/wireless/b43# ls
b43.ko

```
So it is there. Wierd.

```

root@owner:/lib/modules//kernel/drivers/net/wireless/b43# depmod -a
root@owner:/lib/modules//kernel/drivers/net/wireless/b43#

```
... No output. (But it was busy for a bit)

```

root@owner:/lib/modules//kernel/drivers/net/wireless/b43#  /etc/init.d/networking restart
 *Reconfiguring network interfaces...
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp

SIOCSIFADDR: No such device
eth0: Error while getting interface flags: No such device
eth0: Error while getting interface flags: No such device
Failed to bring up eth0.

```
Same error.

```

root@owner:/lib/modules//kernel/drivers/net/wireless/b43# dhclient
Internet Systems Consortium DNCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://ww.isc.org/sw/dhcp/

No broadcast interfaces found - exiting

```

```

root@owner:/# ping www.google.com
ping: unknown host www.google.com

```

Now rebooting Jaunty...

no connectivity still...

---

### Post by toastermm on 2009-04-30
So, just out of curiousity, I tried a wired connection.  The wired internet connection works in bash prompt, but not jaunty.  So I'm updated with the following commands again:
```

sudo aptitude update
sudo aptitude -f install
sudo dpkg --configure -a
sudo aptitude dist-upgrade

```

Mouse, sound and internet work in Jaunty.

Problem solved.

Thank you so much!!!!

---

### Post by pablomolnar on 2009-04-30
The output of lshw -c network gets UNCLAIMED, that means you have to install the driver of the network card.

Post the results for:
locate b43.ko
uname -r

---

### Post by pablomolnar on 2009-04-30
> **toastermm said:**
> So, just out of curiousity, I tried a wired connection.  The wired internet connection works in bash prompt, but not jaunty.  So I'm updated with the following commands again:
```

sudo aptitude update
sudo aptitude -f install
sudo dpkg --configure -a
sudo aptitude dist-upgrade

```Mouse, sound and internet work in Jaunty.

Problem solved.

Thank you so much!!!!

Perferct! Dismiss the last comment.
Glad to see you could finally solve the problem
=P

---

