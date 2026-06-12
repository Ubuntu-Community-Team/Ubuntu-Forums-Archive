---
title: "Error 15: File not found. Argh!"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by polkadotteapot on 2009-04-11
I went a bit wrong:

Firstly when booting I get a list of linux kernels (none of which boot), then windows versions. I have to go into windows xp, then choose xp or ubuntu like I did before. The partitions are all set and there is data on the ubuntu one so is this booting correctly?

My partitions fo small FAT, ntfs for xp, swap, ext3 for linux.

I wanted the xp/ubuntu choice as before so following the advice on page three of this thread [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591) using this
Code:

sudo gedit /boot/grub/menu.lst

I moved the ubuntu and xp to the top of the list above the kernels and I still get the same boot screen, but now I can't boot into ubuntu. I just get a loop of errors sending be back through the process; Error 15: File not found.

I can get to do something to the list so can anyone tell me what I can do to get it changed to either working back to how it was, or how to get it how I want please?

Thank you, argh!

---

### Post by polkadotteapot on 2009-04-11
By the way, I don't have an optical drive at the moment so I can't do any of the solutions I've found so far using the live cd.

---

### Post by polkadotteapot on 2009-04-11
Just bumping.

---

### Post by meierfra. on 2009-04-11
Try this: at the grub menu at boot up press "c"

Type

```
find /boot/grub/stage2
```

This will return something like "root (hd0,4)".  Whatever it says, use in the next line:

```
root (hd0,4)
```

Next type

```
kernel /vmlinuz root=/dev/sda5 ro
```
(the number needs to be one higher than the number in "root (hd0,4)". So if you used "root (hd0,0)"  above, use "/dev/sda1", if you used  "root (hd0,1)" use "/dev/sda2" and so on.

Type

```
initrd /initrd.img

boot
```

Hopefully this will boot you into Ubuntu. 
If yes, open a terminal in Ubuntu and post the output of

```
cat /boot/grub/menu.lst
```

---

### Post by polkadotteapot on 2009-04-12
Thank you for your reply. Just found that if I go to boot into Windows Xp. then into kubuntu (got it on wubi on my windows partition) and press Esc I can get to the choice of kernels on the ubuntu partition.

'e' brings up similar to what is written above so I didn't change it but it did boot into my ubuntu The wireless is broken now though.

As requested:
lou@ubuntu:~$ cat /boot/grub/menu.lst 
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
timeout 	10 

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
# kopt=root=UUID=027829f4-ce52-4e6c-adc2-594544457175 ro ROOTFLAGS=syncio 

## default grub root device 
## e.g. groot=(hd0,0) 
# groot=()/ubuntu/disks 

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

title		Ubuntu 8.10, kernel 2.6.28sickboy-kuki 
root		()/ubuntu/disks 
kernel		/boot/vmlinuz-2.6.28sickboy-kuki root=UUID=027829f4-ce52-4e6c-adc2-594544457175  ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.28sickboy-kuki 

title		Ubuntu 8.10, kernel 2.6.28sickboy-kuki (recovery mode) 
root		()/ubuntu/disks 
kernel		/boot/vmlinuz-2.6.28sickboy-kuki root=UUID=027829f4-ce52-4e6c-adc2-594544457175  ro ROOTFLAGS=syncio  single 
initrd		/boot/initrd.img-2.6.28sickboy-kuki 

title		Ubuntu 8.10, kernel 2.6.27-11-generic 
root		()/ubuntu/disks 
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=027829f4-ce52-4e6c-adc2-594544457175  ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic 

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) 
root		()/ubuntu/disks 
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=027829f4-ce52-4e6c-adc2-594544457175  ro ROOTFLAGS=syncio  single 
initrd		/boot/initrd.img-2.6.27-11-generic 

title		Ubuntu 8.10, kernel 2.6.27-7-generic 
root		()/ubuntu/disks 
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=027829f4-ce52-4e6c-adc2-594544457175  ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic 

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) 
root		()/ubuntu/disks 
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=027829f4-ce52-4e6c-adc2-594544457175  ro ROOTFLAGS=syncio  single 
initrd		/boot/initrd.img-2.6.27-7-generic 

title		Ubuntu 8.10, memtest86+ 
root		()/ubuntu/disks 
kernel		/boot/memtest86+.bin 

### END DEBIAN AUTOMAGIC KERNELS LIST 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 
root 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda1 
title		Windows NT/2000/XP 
root		(hd0,0) 
savedefault 
chainloader	+1 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda2 
title		Microsoft Windows XP Home Edition 
root		(hd0,1) 
savedefault 
chainloader	+1 


title UNetbootin-partitionmanagerrev146 
   root (hd0,) 
   kernel /ubuntu/disks/boot/ubnkern noapic root=/dev/ram0 init=/linuxrc ramdisk_size=200000 keymap=us liveusb vga=791 quiet toram 
   initrd /ubuntu/disks/boot/ubninit 
   boot 


# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 
root 


title Windows 
root (hd0,1) 
makeactive 
chainloader +1 
boot 


title Windows NT/2000/XP 
root (hd0,0) 
makeactive 
chainloader +1 
boot 


title Microsoft Windows XP Home Edition 
root (hd0,1) 
makeactive 
chainloader +1 
boot 

Also if you're any good with wifi:
lou@ubuntu:~$ sudo lshw -C network 
[sudo] password for lou: 
  *-network               
       description: Ethernet interface 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:23:8b:3f:c1:12 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s 
  *-network UNCLAIMED 
       description: Ethernet controller 
       product: AR242x 802.11abg Wireless PCI Express Adapter 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix bus_master cap_list 
       configuration: latency=0 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: be:4a:af:f6:28:5a 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 
lou@ubuntu:~$ ipconfig 
bash: ipconfig: command not found 
lou@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:23:8b:3f:c1:12  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:154312318 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:219 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:2200 (2.2 KB)  TX bytes:2200 (2.2 KB) 

lou@ubuntu:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

pan0      no wireless extensions. 
lou@ubuntu:~$ sudo lshw -C network 
[sudo] password for lou: 
  *-network               
       description: Ethernet interface 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:23:8b:3f:c1:12 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s 
  *-network UNCLAIMED 
       description: Ethernet controller 
       product: AR242x 802.11abg Wireless PCI Express Adapter 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix bus_master cap_list 
       configuration: latency=0 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: be:4a:af:f6:28:5a 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 
lou@ubuntu:~$ ipconfig 
bash: ipconfig: command not found 
lou@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:23:8b:3f:c1:12  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:154312318 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:219 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:2200 (2.2 KB)  TX bytes:2200 (2.2 KB) 

lou@ubuntu:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

pan0      no wireless extensions. 
lou@ubuntu:~$ sudo lshw -C network 
[sudo] password for lou: 
  *-network               
       description: Ethernet interface 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:23:8b:3f:c1:12 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s 
  *-network UNCLAIMED 
       description: Ethernet controller 
       product: AR242x 802.11abg Wireless PCI Express Adapter 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix bus_master cap_list 
       configuration: latency=0 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: be:4a:af:f6:28:5a 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 
lou@ubuntu:~$ ipconfig 
bash: ipconfig: command not found 
lou@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:23:8b:3f:c1:12  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:154312318 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:219 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:2200 (2.2 KB)  TX bytes:2200 (2.2 KB) 

lou@ubuntu:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

pan0      no wireless extensions. 

I've got the sickboy.kuki kernel installed and all I've done is move ubuntu off wubi to it's own partition. How would that have broken the internet? What have I missed?

Thank you for your help.

---

### Post by polkadotteapot on 2009-04-12
Ack, the internet is fine, I was just being a moose (again) and booting into the wrong kernel. So I could just do with a way of tidying up the grubby mess I've made. Pun entirely intended.

---

### Post by meierfra. on 2009-04-12
Your menu.lst definitely needs some fixing, but i need some more information:

Boot into  Ubuntu and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it.

---

### Post by polkadotteapot on 2009-04-12
As requested:

EDIT: Sorry, pressed the hash button but it still came out like this I'll try again, it may be noscript.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x11a8ba38

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    10,233,404    10,233,342  12 Compaq diagnostics
/dev/sda2    *     10,233,405    62,235,809    52,002,405   7 HPFS/NTFS
/dev/sda3          62,235,810    64,484,909     2,249,100  82 Linux swap / Solaris
/dev/sda4          64,484,910   312,576,704   248,091,795  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x48e23888

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   614,402,047   614,400,000   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="PQSERVICE" UUID="0159-6699" TYPE="vfat" 
/dev/sda2: UUID="4C504C1A504C0CE0" LABEL="ACER" TYPE="ntfs" 
/dev/sda3: UUID="6337a417-ada3-4f6b-92e6-cbbd45d0f97b" TYPE="swap" 
/dev/sda4: UUID="027829f4-ce52-4e6c-adc2-594544457175" TYPE="ext3" 
/dev/sdb1: UUID="A4D81299D81269B6" LABEL="Spare Tyre" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda4 on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sda2 on /media/drv0 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/lou/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lou)
/dev/sdb1 on /media/Spare Tyre type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


==================== sda2/ubuntu/disks/boot/grub/menu.lst: ====================

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
# kopt=root=UUID=4C504C1A504C0CE0 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 8.10, kernel 2.6.28sickboy-kuki
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28sickboy-kuki root=UUID=4C504C1A504C0CE0 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.28sickboy-kuki

title		Ubuntu 8.10, kernel 2.6.28sickboy-kuki (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28sickboy-kuki root=UUID=4C504C1A504C0CE0 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.28sickboy-kuki

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4C504C1A504C0CE0 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4C504C1A504C0CE0 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Ubuntu 8.10, kernel 2.6.28sickboy-kuki (on /dev/sda4)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.28sickboy-kuki root=UUID=027829f4-ce52-4e6c-adc2-594544457175 ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.28sickboy-kuki
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Ubuntu 8.10, kernel 2.6.28sickboy-kuki (recovery mode) (on /dev/sda4)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.28sickboy-kuki root=UUID=027829f4-ce52-4e6c-adc2-594544457175 ro ROOTFLAGS=syncio single 
initrd		/boot/initrd.img-2.6.28sickboy-kuki
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sda4)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=027829f4-ce52-4e6c-adc2-594544457175 ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda4)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=027829f4-ce52-4e6c-adc2-594544457175 ro ROOTFLAGS=syncio single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda4)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=027829f4-ce52-4e6c-adc2-594544457175 ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda4)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=027829f4-ce52-4e6c-adc2-594544457175 ro ROOTFLAGS=syncio single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Ubuntu 8.10, memtest86+ (on /dev/sda4)
root		(hd0,3)
kernel		/boot/memtest86+.bin  
savedefault
boot


======================== sda2/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

================================ sda2/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

C:\ubnldr.mbr="UNetbootin"

c:\wubildr.mbr="Kubuntu"


================================== sda2Wubi: ==================================

Operating System: "Ubuntu 8.10"

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

=================== sda2: Location of files loaded by Grub: ===================


   8.9GB: ubuntu/disks/boot/grub/menu.lst
   9.0GB: ubuntu/disks/boot/initrd.img-2.6.27-7-generic
   8.8GB: ubuntu/disks/boot/initrd.img-2.6.28sickboy-kuki
   8.9GB: ubuntu/disks/boot/vmlinuz-2.6.27-7-generic
   8.6GB: ubuntu/disks/boot/vmlinuz-2.6.28sickboy-kuki

=========================== sda4/boot/grub/menu.lst: ===========================

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
timeout 	10

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
# kopt=root=UUID=027829f4-ce52-4e6c-adc2-594544457175 ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 8.10, kernel 2.6.28sickboy-kuki
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28sickboy-kuki root=UUID=027829f4-ce52-4e6c-adc2-594544457175  ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.28sickboy-kuki

title		Ubuntu 8.10, kernel 2.6.28sickboy-kuki (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28sickboy-kuki root=UUID=027829f4-ce52-4e6c-adc2-594544457175  ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.28sickboy-kuki

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=027829f4-ce52-4e6c-adc2-594544457175  ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=027829f4-ce52-4e6c-adc2-594544457175  ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=027829f4-ce52-4e6c-adc2-594544457175  ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=027829f4-ce52-4e6c-adc2-594544457175  ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
chainloader	+1


title UNetbootin-partitionmanagerrev146
   root (hd0,)
   kernel /ubuntu/disks/boot/ubnkern noapic root=/dev/ram0 init=/linuxrc ramdisk_size=200000 keymap=us liveusb vga=791 quiet toram
   initrd /ubuntu/disks/boot/ubninit
   boot


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title Windows
root (hd0,1)
makeactive
chainloader +1
boot


title Windows NT/2000/XP
root (hd0,0)
makeactive
chainloader +1
boot


title Microsoft Windows XP Home Edition
root (hd0,1)
makeactive
chainloader +1
boot


=============================== sda4/etc/fstab: ===============================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda4
UUID=027829f4-ce52-4e6c-adc2-594544457175     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sda2
UUID=4C504C1A504C0CE0       /media/drv0       ntfs-3g         defaults      0   0


# /dev/sda3
UUID=6337a417-ada3-4f6b-92e6-cbbd45d0f97b      none            swap        sw          0   0


=================== sda4: Location of files loaded by Grub: ===================


 134.9GB: boot/grub/menu.lst
 134.9GB: boot/grub/stage2
 135.0GB: boot/initrd.img-2.6.27-11-generic
 134.9GB: boot/initrd.img-2.6.27-7-generic
 134.9GB: boot/initrd.img-2.6.28sickboy-kuki
 134.9GB: boot/vmlinuz-2.6.27-11-generic
 134.9GB: boot/vmlinuz-2.6.27-7-generic
 134.9GB: boot/vmlinuz-2.6.28sickboy-kuki
 135.0GB: initrd.img
 134.9GB: initrd.img.old
 134.9GB: vmlinuz
 134.9GB: vmlinuz.old
```

---

### Post by meierfra. on 2009-04-12
Boot into Ubuntu and edit the file  /boot/grub/menu.lst as follows:

Change 

# kopt=root=UUID=027829f4-ce52-4e6c-adc2-594544457175 ro ROOTFLAGS=syncio 

to

# kopt=root=UUID=027829f4-ce52-4e6c-adc2-594544457175 ro


and change

# groot=()/ubuntu/disks

 to

# groot=027829f4-ce52-4e6c-adc2-594544457175

Save the file. Then regenerate menu.lst via

```
sudo update-grub
```

You should now be able to boot into Ubuntu directly from the Grub Menu at boot up.

---

