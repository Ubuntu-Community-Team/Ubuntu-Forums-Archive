---
title: "no option to boot to linux"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by einstejn on 2009-03-14
I just installed kubuntu on a 2nd hdd, but when I start my pc theres no option to boot to it. any ideas to get this to work? this is my first linux install, so go easy on me.

---

### Post by meierfra. on 2009-03-14
Probably you just have to change the boot order in the bios.

---

### Post by dongiuseppe2684 on 2009-03-15
Do you even get the GRUB menu when you boot?  Also install partition editor to see if anything is detecting your second hard disk.  But yes also make sure you BIOS settings are correct.

---

### Post by einstejn on 2009-03-15
I installed partition magic and it shows the second hdd and it shows linux on it. What kind of bios settings do i need to make? right now I have hard drive set as first boot option. and I don't see grub start at all just goes straight to windows. I have three hdd's installed if that makes a difference.

---

### Post by munishvit on 2009-03-15
> **einstejn said:**
> I installed partition magic and it shows the second hdd and it shows linux on it. What kind of bios settings do i need to make? right now I have hard drive set as first boot option. and I don't see grub start at all just goes straight to windows. I have three hdd's installed if that makes a difference.

You please post your hard-disk partition structure

---

### Post by einstejn on 2009-03-15
Is this what you want?

[http://i80.photobucket.com/albums/j193/DieHardD/screen.jpg]("http://i80.photobucket.com/albums/j193/DieHardD/screen.jpg")

---

### Post by munishvit on 2009-03-15
I don't know much about booting when it comes to multiple hard-disks. But, I guess this may help you:
1. Boot using Kubuntu Live Disk
2. Open Terminal and type
> 	sudo grub	//specifying boot directory
	grub> root (hd1,0)
	grub> setup (hd1)	//installs GRUB at MBR
	quit
3. Change name of your menu.lst file (must be in Linux partition of Disk-2  with /boot/grub/menu.lst) to menu.lst.backup
4. There you create a new file named menu.lst and write:
   (But, if your hard-disk is 'hd', then use [COLOR="Red"]'hd' instead of 'sd'[/COLOR], and  write proper files names of [COLOR="Red"]vmlinuz* and initrd*[/COLOR] by looking in your /boot directory)
> 	default saved
	timeout 5
	fallback 0
	title	Kubuntu @ /dev/sdb0
		map (hd0) (hd1)
		map (hd1) (hd0)
		root (hd1,0)
		kernel (hd1,0)/vmlinuz-2.6.24-23-generic root=/dev/sdb0 ro quiet
		initrd (hd1,0)/initrd.img-2.6.24-23-generic
		quiet
		savedefault 0
	title	Windows @ /dev/sdc0
		map (hd0) (hd2)
		map (hd2) (hd0)
		rootnoverify (hd2,0)
		chainloader +1
		makeactive
		savedefault fallback

---

### Post by meierfra. on 2009-03-15
> right now I have hard drive set as first boot option

Have a closer look at your bios: Some bios have  a separate setting where you can choose the  boot order of the individual hard drives.

But **if you cannot change the boot order in the bios**, then I suggest to get SupperGrub

[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

Follow the direction from this page:

[http://www.supergrubdisk.org/wiki/Howto_Fix_Grub]("http://www.supergrubdisk.org/wiki/Howto_Fix_Grub")

Try the "Windows Solution" first. If that does not work, try the  "Quick Solution" and then the  "Not So Quick Solution" 


munishvit's directions will only work if you can set your bios to boot from the Kubuntu drive.  But  in that case you might not have to reinstall grub anyway. So I wouldn't   use the LiveCD to reinstall grub at this stage. (But you might have to do it later)

Do not edit the "Kubuntu" part of menu.lst. It is extremely unlikely that there is anything wrong with that part of menu.lst
You probably will have to edit the Windows item.  But I wouldn't worry about that until you are able to boot into Kubuntu.

---

### Post by einstejn on 2009-03-15
I tried the windows option which didn't work and there are know instructions for the other two options.

---

### Post by meierfra. on 2009-03-15
For the other two options you have to create a  regular SuperGrub CD.  Click on Download CDROM in the upper right corner of the main supergrub page: [ http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

---

### Post by einstejn on 2009-03-16
Can't seem to get it to work. If I were to install it on the same hdd as my windows xp would that take care of the problem? Or would a different distrobution of linux work better?

---

### Post by meierfra. on 2009-03-16
> If I were to install it on the same hdd as my windows xp would that take care of the problem? 

It might, but my guess would be not.

But it should be possible to manually install grub correctly.  I need some information.

1)  Boot from the regular Super Grub disk. Go to

"Choose language and no help" -> "English support Grub disk" -> "Support" -> "Show Hard Disks' partition Layouts".

Look for   the line with "Ubuntu" in the description. Something like


4  (hd2,4) extfs  10GB   Ubuntu .......

Of course the numbers will be different. Please post the "(hd2,4)" part.


2) Boot from your Ubuntu Live CD and  download the Boot Info Script to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by einstejn on 2009-03-16
I made a supergrub cd but I can not boot from it for some reaseon, I used imgburn

---

### Post by meierfra. on 2009-03-16
Well, just run the "boot info script" and post the "RESULTS.txt". 
(The output from SuperGrub just would  have made things a little easier)

---

### Post by einstejn on 2009-03-16
I keep getting "no such file or directory" ?

---

### Post by einstejn on 2009-03-16
There we go

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       625135615 sectors, but according to the info from 
                       fdisk, it has 625151362 sectors.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3dfe48c6

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   625,153,409   625,151,362   7 HPFS/NTFS

/dev/sda1 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x62866286

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,375,999   488,375,937   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb9edd2f1

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   470,495,654   470,495,592  83 Linux
/dev/sdc2         470,495,655   490,223,474    19,727,820   f W95 Ext d (LBA)
/dev/sdc5         470,495,718   490,223,474    19,727,757  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="58D4EC2CD4EC0E56" TYPE="ntfs" 
/dev/sdb1: UUID="220C93DA0C93A6F7" TYPE="ntfs" 
/dev/sdc1: UUID="3ce6d414-e3cc-4fb6-95fd-5404be4eca31" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: UUID="60a17780-e301-4252-b3b0-13b28cd7b147" TYPE="swap" 
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


================================ sdb1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=6
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /NOEXECUTE=OPTIN /FASTDETECT

=========================== sdc1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=3ce6d414-e3cc-4fb6-95fd-5404be4eca31 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3ce6d414-e3cc-4fb6-95fd-5404be4eca31

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		3ce6d414-e3cc-4fb6-95fd-5404be4eca31
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3ce6d414-e3cc-4fb6-95fd-5404be4eca31 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		3ce6d414-e3cc-4fb6-95fd-5404be4eca31
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3ce6d414-e3cc-4fb6-95fd-5404be4eca31 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		3ce6d414-e3cc-4fb6-95fd-5404be4eca31
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=3ce6d414-e3cc-4fb6-95fd-5404be4eca31 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=60a17780-e301-4252-b3b0-13b28cd7b147 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  67.0GB: boot/grub/menu.lst
  67.0GB: boot/grub/stage2
  67.0GB: boot/initrd.img-2.6.27-7-generic
  67.1GB: boot/vmlinuz-2.6.27-7-generic
  67.0GB: initrd.img
  67.1GB: vmlinuz

---

### Post by meierfra. on 2009-03-16
Since I don't know wether the Ubuntu drive is second or third in the boot order, you will have to try two different options to reinstall grub:

So boot from the LiveCD, open a terminal  and type


```
sudo grub 
```

and at the grub prompt:

```

device (hd0) /dev/sdb
device (hd1) /dev/sdc
root (hd1,0)
setup (hd0)
quit

```


Reboot.  

**Only if the Grub Menu does not appear: **

boot  from the LiveCD and open a terminal. Type

```
sudo grub 
```

and at the grub prompt:

```

device (hd0) /dev/sdb
device (hd2) /dev/sdc
root (hd2,0)
setup (hd0)
quit

```

Reboot.


**If the Grub Menu Appeared:**

Boot into Ubuntu. Once you successfully booted into Ubuntu, you need to edit "menu.lst" to be able to boot into Windows from the Grub menu:

Open the file "menu.lst" via

```
gksudo gedit /boot/grub/menu.lst
```

Change 

title Windows Vista/Longhorn (loader)
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

to

title Windows Vista/Longhorn (loader)
root (hd0,0)
chainloader +1

Save the file. Reboot and see whether you can  boot into Vista.

---

### Post by einstejn on 2009-03-17
Alright the first option came up with error 17 and the second option worked, I can now boot to kubuntu. Now as for booting to windows xp, I typed "gksudo gedit /boot/grub/menu.lst" in the terminal and it says: the program 'gksudo' is currently not installed. you can install it by typing: sudo apt-get install gksu. so I did and now when I type "sudo apt-get install gksu" it says: (gksudo:6757): Gtk-WARNING **: libbonoboui-2.so.0: cannot open shared object file: No such file or directory

---

### Post by meierfra. on 2009-03-17
Sorry, I forgot that you have kubuntu and not ubuntu.

Use

```
kdesu kate /boot/grub/menu.lst
```

---

### Post by einstejn on 2009-03-17
hmm, I got command not found

---

### Post by meierfra. on 2009-03-17
Strange. 

Try

```
sudo nano /boot/grub/menu.lst
```

This will open the file inside the terminal . Look at the bottom of the screen for instructions how to save the file ("^" means the "Ctrl" key).

---

### Post by einstejn on 2009-03-17
That didn't seem to work theres only an option to boot to kubuntu

---

### Post by meierfra. on 2009-03-17
Post the output of 

```
cat /boot/grub/menu.lst
ls -l /boot/grub
```

---

### Post by einstejn on 2009-03-17
dan@linux:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=3ce6d414-e3cc-4fb6-95fd-5404be4eca31 ro          

## default grub root device
## e.g. groot=(hd0,0)      
# groot=3ce6d414-e3cc-4fb6-95fd-5404be4eca31

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

title           Ubuntu 8.10, kernel 2.6.27-11-generic
uuid            3ce6d414-e3cc-4fb6-95fd-5404be4eca31 
kernel          /boot/vmlinuz-2.6.27-11-generic root=UUID=3ce6d414-e3cc-4fb6-95fd-5404be4eca31 ro quiet splash                                                  
initrd          /boot/initrd.img-2.6.27-11-generic                              
quiet                                                                           

title           Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid            3ce6d414-e3cc-4fb6-95fd-5404be4eca31
kernel          /boot/vmlinuz-2.6.27-11-generic root=UUID=3ce6d414-e3cc-4fb6-95fd-5404be4eca31 ro  single
initrd          /boot/initrd.img-2.6.27-11-generic

title           Ubuntu 8.10, kernel 2.6.27-7-generic
uuid            3ce6d414-e3cc-4fb6-95fd-5404be4eca31
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=3ce6d414-e3cc-4fb6-95fd-5404be4eca31 ro quiet splash
initrd          /boot/initrd.img-2.6.27-7-generic
quiet

title           Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid            3ce6d414-e3cc-4fb6-95fd-5404be4eca31
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=3ce6d414-e3cc-4fb6-95fd-5404be4eca31 ro  single
initrd          /boot/initrd.img-2.6.27-7-generic

title           Ubuntu 8.10, memtest86+
uuid            3ce6d414-e3cc-4fb6-95fd-5404be4eca31
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Windows XP map (hd0,0) (hd0,2) map (hd0,2) (hd0,0) rootnoverify (hd0,2) makeactive chainloader +1
dan@linux:~$ ls -l /boot/grub

---

### Post by meierfra. on 2009-03-17
> title Windows XP map (hd0,0) (hd0,2) map (hd0,2) (hd0,0) rootnoverify (hd0,2) makeactive chainloader +1

There did that come from?

It needs to be

title Windows Vista   # or any other title of your liking
root (hd0,0)
chainloader +1

Nothing else. Just those three lines.
Also make sure that it does not end up on just one line. It needs  to be on three lines. (if it is on one line, it will not show up in the Grub menu).

---

### Post by einstejn on 2009-03-17
oh, I searched google for a fix, thats where that string of code came from, didn't work though. couldn't get yours to work either.

---

### Post by einstejn on 2009-03-17
I tried it again and it worked, Yahhhooooo!!!
one thing though, it shows 2 kubuntus and 2 kubuntu safe modes in the grub boot loader.
I really appreciate the help on gettin this stuff going you surely know what your doing, thanks!

---

### Post by meierfra. on 2009-03-17
```
tried it again and it worked, Yahhhooooo!!!
```

Great.

> one thing though, it shows 2 kubuntus and 2 kubuntu safe modes in the grub boot loader.

Those corresponds to two different kernel. I recommend to keep both kernels on the Grub menu. If something goes wrong with one of them (for example during kernel updates) you still have the other to boot. But I suggest to change

# howmany=all

in menu.lst to

# howmany=2

Then you  will never have more than two kernels on your Grub menu.

Have a look at drs305's HowTo:
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

---

### Post by einstejn on 2009-03-18
Again, thanks for the help, I really appreciate it!

---

### Post by meierfra. on 2009-03-18
> Again, thanks for the help, I really appreciate it!

You are welcome. Have fun with Windows and Kubuntu.

---

