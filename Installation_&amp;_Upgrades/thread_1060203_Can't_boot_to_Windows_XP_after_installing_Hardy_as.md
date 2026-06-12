---
title: "Can't boot to Windows XP after installing Hardy as dual-boot"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by Bearly Able on 2009-02-04
Hi,

I'm pretty new to Ubuntu, although I have a laptop with Hardy Heron (pre-installed).  I installed Hardy on my desktop PC yesterday as a dual-boot with Windows XP.  The PC has been running XP and we added a second hard-drive for Ubuntu.  Ubuntu runs fine, but I'm unable to boot into Windows.  The option is there on the boot menu, but selecting it gets me 
[INDENT]TRAP 00000006 EXCEPTION[/INDENT]
followed by several lines of code (which I can quote, if needed).  I can find no way out of this apart from the reset button.

Sadly, I do need to use Windows occasionally (hence the dual-boot), so I would be very grateful for any assistance.

Thanks

Lesley

---

### Post by Jesper-L on 2009-02-04
Assuming you have the windows cd, it could be worth a shot to boot from it, into repair console and try typing: fixmbr

(Maybe its fixboot now, been a while since fiddling with that. Try both :) )

---

### Post by caljohnsmith on 2009-02-04
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

---

### Post by Jesper-L on 2009-02-04
I think that maybe youre in better hands than mine now, lesley ;)

Good luck.

---

### Post by Bearly Able on 2009-02-04
Thanks for the detailed instructions, which I've followed and now have this:

```

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfbc4fbc4

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    71,682,029    71,681,967   7 HPFS/NTFS
/dev/sda2          71,682,030   312,576,704   240,894,675   f W95 Ext d (LBA)
/dev/sda5          71,682,093   133,259,174    61,577,082   7 HPFS/NTFS
/dev/sda6         133,259,238   199,463,039    66,203,802   7 HPFS/NTFS
/dev/sda7         199,463,103   266,678,999    67,215,897   7 HPFS/NTFS
/dev/sda8         266,679,063   312,576,704    45,897,642   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ec031

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   300,431,564   300,431,502  83 Linux
/dev/sdb2         300,431,565   312,576,704    12,145,140   5 Extended
/dev/sdb5         300,431,628   312,576,704    12,145,077  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="127C3D347C3D13C7" TYPE="ntfs" 
/dev/sda5: UUID="4CBE3566D7F2CDE4" TYPE="ntfs" 
/dev/sda6: UUID="ACABF83B1BD256E9" TYPE="ntfs" 
/dev/sda7: UUID="024FF147EFA0A210" TYPE="ntfs" 
/dev/sda8: UUID="132F8D1E942CCBC1" TYPE="ntfs" 
/dev/sdb1: UUID="5fd01ebc-10f0-404f-9c20-35fb88570be0" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="b675e649-2a01-4e03-b879-552eb1d45a66" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/lesley/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lesley)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=5fd01ebc-10f0-404f-9c20-35fb88570be0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=5fd01ebc-10f0-404f-9c20-35fb88570be0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=5fd01ebc-10f0-404f-9c20-35fb88570be0 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5fd01ebc-10f0-404f-9c20-35fb88570be0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5fd01ebc-10f0-404f-9c20-35fb88570be0 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=5fd01ebc-10f0-404f-9c20-35fb88570be0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=b675e649-2a01-4e03-b879-552eb1d45a66 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 111.4GB: boot/grub/menu.lst
 111.4GB: boot/grub/stage2
 111.4GB: boot/initrd.img-2.6.24-16-generic
 111.5GB: boot/initrd.img-2.6.24-16-generic.bak
 111.4GB: boot/initrd.img-2.6.24-23-generic
 111.4GB: boot/initrd.img-2.6.24-23-generic.bak
 111.5GB: boot/vmlinuz-2.6.24-16-generic
 111.4GB: boot/vmlinuz-2.6.24-23-generic
 111.4GB: initrd.img
 111.4GB: initrd.img.old
 111.4GB: vmlinuz
 111.5GB: vmlinuz.old

```

(Perhaps I should have explained that the original hard drive - the one with Windows - has five partitions.)

Hope all this means something to you!  Thanks for your time.

---

### Post by caljohnsmith on 2009-02-04
Lesley, can you change your BIOS boot order so that the Ubuntu sdb drive boots before the Windows sda drive? If so, I think that will help solve the problem; if you can do that, we can first install Grub to the MBR (Master Boot Record) of your Ubuntu drive to make it bootable, and then we can restore a Windows MBR to your sda Windows drive. Then we can try booting Windows from Grub again (we will have to change its Grub entry of course), and if for some reason we can't get that to work, you will always at least have the option of booting Windows by simply changing the boot order again. And more importantly, that will also help us confirm whether Windows is the problem right now or if it is instead a Grub problem; part of the issue is that your current Windows entry in the Grub menu should work, and yet obviously it doesn't. So does that plan sound OK?

---

### Post by Bearly Able on 2009-02-05
Hi again,

Yes, I can change the BIOS boot order to boot the second hard drive first.  Let me know what to do next.  I'm very grateful for your help.

Lesley

---

### Post by caljohnsmith on 2009-02-05
OK, how about first doing:
```
sudo grub
grub> root (hd1,0)
grub> makeactive
grub> setup (hd1)
grub> quit
```
That should install Grub to the MBR of your Ubuntu drive. Next, to restore your Windows MBR:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Next, we'll need to modify your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change all your Ubuntu entries to use (hd0,0) instead of (hd1,0), similar to:
```
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		[COLOR="Blue"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=5fd01ebc-10f0-404f-9c20-35fb88570be0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet
```
Also change the "# groot=(hd1,0)" line:
```
# groot=[COLOR="Blue"](hd0,0)[/COLOR]
```
Next change your Windows entry to:
```
title       Windows XP
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

```
Then reboot, and you should be able to boot straight into Windows since I assume you haven't changed your BIOS boot order yet (your BIOS should still be booting the Windows drive first); let me know if you can boot into Windows OK. Next set your BIOS to boot the sdb Ubuntu drive, and if all goes well you should get the Grub menu on start up. Let me know if you can boot Windows and Ubuntu from the Grub menu, or if you get any errors. We can work from there. :)

---

### Post by Bearly Able on 2009-02-05
OK - so far so good!  I'm in Windows, and just about to try rebooting to the second hard drive.  Fingers crossed.

---

### Post by Bearly Able on 2009-02-05
Hi again,

I can boot Ubuntu from the Grub menu, but not Windows.  I no longer get the error message, just a black screen with nothing happening.  At least now I can boot Windows from the BIOS, so things have definitely improved.  Many thanks.

Lesley

---

### Post by caljohnsmith on 2009-02-05
Glad to hear you can at least boot Windows from BIOS, but maybe we can still get Windows to boot from Grub. If you want to give it a try, how about opening your menu.lst again and replace the Windows entry with the following entries:
```
title       Windows XP #1
rootnoverify     (hd1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows XP #2
rootnoverify     (hd1)
map        (hd0) (hd1)
chainloader +1

title       Windows XP #3
rootnoverify     (hd1)
map        (hd1) (hd0)
chainloader +1
```
Then reboot, select each Windows entry from the Grub menu, and please let me know exactly what happens when you try each one. We can work from there.

---

### Post by Bearly Able on 2009-02-05
OK.  Options 1 and 3 give me "Starting Up", briefly, then nothing - black screen.  Option 2 gives me "Starting Up disk read error".  Aare we any further forward?

---

### Post by caljohnsmith on 2009-02-05
Unfortunately, your computer setup is one of the rare cases I've seen where Grub just can't seem to boot Windows for some reason. Are you OK with changing your BIOS boot order whenever you want to boot the other OS, or would you like to pursue a better solution? For instance, we could add an option in your Windows boot manager to boot Ubuntu from Windows, and then you could just boot the Windows drive on start up all the time. That usually works just fine for the few rare cases I've seen like yours where Grub can't boot Windows for some reason, so instead we just have Windows boot Grub. Do you want to try that?

---

### Post by Bearly Able on 2009-02-05
I guess it's just the Windows boot loader we'd be using, not Windows itself, to launch Ubuntu.  We're trying to get away from Windows as far as possible, because it's so darned unreliable, and this has me a little hesitant, but your advice has been good this far, so I'll trust your judgment on this and give it a go.  Thank you again.

---

### Post by caljohnsmith on 2009-02-05
If it makes you feel any better, you can ditch Windows at any time, and you should be able to boot Ubuntu with no problems by simply changing your BIOS to boot the Ubuntu drive (like you have done all ready). So anyway, to boot Grub from your XP boot manager, how about first doing the following in Ubuntu:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1,0)
grub> quit
```
Then boot into Windows, download this program called "[bootpart]("http://www.winimage.com/bootpa26.zip")" to your Windows desktop, unzip it, make sure the "bootpart.exe" program is on your desktop, and go to Start > Run > and type "cmd" to get a command window. Then navigate to your desktop directory by doing:
```
cd C:\Documents and Settings\[COLOR="Blue"]<user name>[/COLOR]\Desktop
```
And replace <user name> with your Windows user name. Then run bootpart:
```
bootpart
```
That will show a list of all all your partitions and their corresponding numbers. Note that bootpart numbers the partitions differently than when you are in Ubuntu, so you'll have to check the listing carefully. Select the partition number that is your Ubuntu install, and do:
```
bootpart [COLOR="Blue"]<partition number>[/COLOR] LBA C:\grub.bin "Ubuntu Grub Menu"
```
If bootpart doesn't report any errors, reboot, make sure your BIOS is set to boot the Windows drive, and if all goes well you will see the Windows boot menu with Windows and "Ubuntu Grub Menu" as the two options. Let me know how far you get when you choose "Ubuntu Grub Menu". We can work from there.

---

### Post by Bearly Able on 2009-02-05
OK, I've followed all that.  I can get to the "Ubuntu Grub Menu", but when I try to load Ubuntu I get "Error 17 Unable to mount selected partition", (or something similar - sorry, I should have written it down).

---

### Post by caljohnsmith on 2009-02-05
OK, I think I know what the issue is, so how about trying this: when you boot Ubuntu from your Windows boot menu and get the Grub menu, select the Ubuntu entry you want to boot, press "e" to edit it, select the line that says "root (hd0,0)", press "e" to edit it, change it to "root (hd1,0)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the change is not permanent, so if it works, you'll need to modify your menu.lst to make it permanent. Let me know how that goes.

---

### Post by Bearly Able on 2009-02-05
Hallelujah - success!  I probably should be able to work out how to modify my menu.lst myself, but I'm somewhat nervous of trying.

---

### Post by caljohnsmith on 2009-02-05
Great, glad to hear that worked OK. :) To modify your menu.lst, you can do the same thing we did before, in other words:
```
gksudo gedit /boot/grub/menu.lst
```
And then change all the Ubuntu entries to use (hd1,0), and also change the "#groot..." line to use (hd0,0) too. Save, and you're done. Let me know if you run into any problems, but that should hopefully be the end of your booting problems. Cheers and enjoy Ubuntu.

---

### Post by Bearly Able on 2009-02-05
Yes, that's it - everything's working just fine.:) Many, many thanks for your help and patience.

Lesley

---

