---
title: "Problem during boot"
date: 2011-03-14
forum: Hardware
---

### Post by silverstorm on 2011-03-14
Hi everyone!
I having some problem during boot.
I have dual boot  windows XP on sda(sda1) Ubuntu on sdb(sdb1 is extended for some reason,  sdb2 is nothing, sdb5 /boot, sdb6 /, sdb7 swap)and one sata disc for is  my store(sdc1)
During booting shows up a splash screen.
An error occurred while mounting /media/sdb1
Press S to skip mounting or M for manual recovery.
Then i press S and booting normally.
Any help why is he doing this.

---

### Post by oldfred on 2011-03-14
If sdb1 is an extended partition you cannot mount it. It is just a container for all the logical. So an error message is correct. Is it somehow set up in fstab?

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by silverstorm on 2011-03-15
Thanks for your post. :)
Here is the results.txt

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.cfg /grub/core.img

sdc6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /etc/fstab

sdc7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders, total 58633344 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    58,621,184    58,621,122   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1              16,126   156,248,189   156,232,064   f W95 Ext d (LBA)
/dev/sdc5    *         16,128     2,072,384     2,056,257  83 Linux
/dev/sdc6           2,072,448   145,436,444   143,363,997  83 Linux
/dev/sdc7         145,436,508   156,248,189    10,811,682  82 Linux swap / Solaris
/dev/sdc2                  63        16,064        16,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D48CB4778CB455A8                       ntfs       Storage                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1A541B51541B2F4F                       ntfs       Windows                       
/dev/sdb: PTTYPE="dos" 
/dev/sdc1: PTTYPE="dos" 
/dev/sdc2        507e35d7-ceed-4654-9d37-6a75ff544313   ext3                                     
/dev/sdc5        ae442dba-b635-4467-a987-d1e2b7bb1905   ext3                                     
/dev/sdc6        9e422c94-2909-469a-ac5d-056707bcb3de   ext3                                     
/dev/sdc7        98e4b6a9-05bd-48f7-b084-5c42da661363   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc6        /                        ext3       (rw)
/dev/sdc5        /boot                    ext3       (rw)
/dev/sdc2        /media/sdb2              ext3       (rw)
/dev/sda1        /media/sdc1              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/sdb1              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

============================= sdc5/grub/menu.lst: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 9e422c94-2909-469a-ac5d-056707bcb3de
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set ae442dba-b635-4467-a987-d1e2b7bb1905
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ae442dba-b635-4467-a987-d1e2b7bb1905
    linux    /vmlinuz-2.6.32-29-generic root=UUID=9e422c94-2909-469a-ac5d-056707bcb3de ro   quiet splash
    initrd    /initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ae442dba-b635-4467-a987-d1e2b7bb1905
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /vmlinuz-2.6.32-29-generic root=UUID=9e422c94-2909-469a-ac5d-056707bcb3de ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ae442dba-b635-4467-a987-d1e2b7bb1905
    linux    /vmlinuz-2.6.32-24-generic root=UUID=9e422c94-2909-469a-ac5d-056707bcb3de ro   quiet splash
    initrd    /initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ae442dba-b635-4467-a987-d1e2b7bb1905
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /vmlinuz-2.6.32-24-generic root=UUID=9e422c94-2909-469a-ac5d-056707bcb3de ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ae442dba-b635-4467-a987-d1e2b7bb1905
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ae442dba-b635-4467-a987-d1e2b7bb1905
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1a541b51541b2f4f
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sdc5/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 9e422c94-2909-469a-ac5d-056707bcb3de
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set ae442dba-b635-4467-a987-d1e2b7bb1905
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ae442dba-b635-4467-a987-d1e2b7bb1905
    linux    /vmlinuz-2.6.32-29-generic root=UUID=9e422c94-2909-469a-ac5d-056707bcb3de ro   quiet splash
    initrd    /initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ae442dba-b635-4467-a987-d1e2b7bb1905
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /vmlinuz-2.6.32-29-generic root=UUID=9e422c94-2909-469a-ac5d-056707bcb3de ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ae442dba-b635-4467-a987-d1e2b7bb1905
    linux    /vmlinuz-2.6.32-24-generic root=UUID=9e422c94-2909-469a-ac5d-056707bcb3de ro   quiet splash
    initrd    /initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ae442dba-b635-4467-a987-d1e2b7bb1905
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /vmlinuz-2.6.32-24-generic root=UUID=9e422c94-2909-469a-ac5d-056707bcb3de ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ae442dba-b635-4467-a987-d1e2b7bb1905
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ae442dba-b635-4467-a987-d1e2b7bb1905
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1a541b51541b2f4f
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sdc5: Location of files loaded by Grub: ===================


    .4GB: grub/core.img
    .4GB: grub/grub.cfg
    .4GB: grub/menu.lst
    .0GB: initrd.img-2.6.32-24-generic
    .1GB: initrd.img-2.6.32-29-generic
    .0GB: vmlinuz-2.6.32-24-generic
    .0GB: vmlinuz-2.6.32-29-generic

=============================== sdc6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sdb6 :
UUID=9e422c94-2909-469a-ac5d-056707bcb3de    /    ext3    defaults    0    1
#Entry for /dev/sdb5 :
UUID=ae442dba-b635-4467-a987-d1e2b7bb1905    /boot    ext3    defaults    0    2
#Entry for /dev/sdb2 :
UUID=507e35d7-ceed-4654-9d37-6a75ff544313    /media/sdb2    ext3    defaults    0    0
#Entry for /dev/sdc1 :
UUID=D48CB4778CB455A8    /media/sdc1    ntfs    defaults    0    0
#Entry for /dev/sdb7 :
UUID=98e4b6a9-05bd-48f7-b084-5c42da661363    none    swap    defaults    0    0
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0
/dev/sdb1    /media/sdb1    ntfs    nls=utf8,umask=0222    0    0



=================== sdc6: Location of files loaded by Grub: ===================


   1.1GB: initrd.img
   1.1GB: initrd.img.old
   1.1GB: vmlinuz
   1.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc2

00000000  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
*
00000200


```

---

### Post by oldfred on 2011-03-15
It looks like you have plugged in a new drive that is now sda - 500GB.

This then has confused all the mounts that use sdXY as the style rather than UUID. Also windows still thinks it is rdisk(0) when it is 1.

If you want to keep the 500GB you will have to update boot.ini, and fstab entries.

Are you able to choose boot drive in BIOS? Is this a mixed SATA/PATA or IDE drive configuration?

Either script or grub report same drive when it is not. If you set BIOS to boot sdb, I would expect it to boot sdc5/sdc6 since it uses UUID. But you do have parts of grub legacy & grub2 in that install which may cause issues.

Can you boot?  What is your goal with the new 500GB drive?

---

### Post by silverstorm on 2011-03-15
Yes i am able to choose from bios wich device to boot.
Yes it is mixed. I have 2 pata and 1 sata drive.
Pata drive:
Master Quantum Fireball 30GB - Windows XP
Slave WDC 80GB - Ubuntu 10.04
Sata drive:
Hitachi 500GB The New Device.
I can boot i have set WDC for my boot device.There is the ubuntu boot drive.
Yes Hitachi Hard Disc is the new one.

---

### Post by silverstorm on 2011-03-15
Sorry i have been wrong.
Quantum is my boot device. And i can boot.
If i change it to wdc it write grub rescue?

---

### Post by oldfred on 2011-03-15
I think most times I see the IDE drives before the SATA. Must depend on BIOS or have you seen it change. That sometimes occurs if drives spin up differently and BIOS sees a different order.

I would install grub2 to sdc - the 80 GB drive. Make sure it still is sdc.

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sdc"  then just run:
sudo grub-install /dev/sdc
#If that returns any errors run:
sudo grub-install --recheck /dev/sdc
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

You could install lilo to sdb after the install of grub, but I would test that you can boot ok from sdc before installing lilo since that is the grub that works. Lilo will boot windows. But I do not know if the drive order makes a difference. I think if you select sdb with lilo you will boot windows, but the grub entry will not work.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

Windows really prefers to be the first drive. But that can be difficult to configure with mixed SATA/PATA drives.

---

