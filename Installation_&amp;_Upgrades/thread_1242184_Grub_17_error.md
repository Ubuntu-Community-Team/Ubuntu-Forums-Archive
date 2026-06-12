---
title: "Grub 17 error"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by eewoz on 2009-08-16
I am trying to install Ubuntu on my Windows XP machine with the set-up where Windows and Ubuntu are both on the machine with their own partitions.  

The install went OK but when I turn the computer on Grub gives ERROR 17 and everything stops.  I am able to use my computer with the Ubuntu install CD and run in the "try Ubuntu without changing your computer setup" mode.  I have an internal harddrive and an external USB drive.  I noticed that the USB drive seemed to be accessed during the instalation.  

I Googled GRUB 17 and got a lot of hits, but I could not follow most of them.  One that I could follow said to go into the Bios setup and make sure that your hardrives are set to AUTO, but I could not see that option in my Bios settings.

Any suggestions would be appreciated.

Thanks you!

---

### Post by confused57 on 2009-08-16
For now you might want to reinstall XP's IPL(Initial Program Loader) to the mbr, this will at least enable being
able to use your pc normally.

After doing this, you might try reinstalling Ubuntu with the external USB drive disconnected during the installation.

I've seen grub error 18 sometimes incorrectly identified as grub error 17. Here's info on grub error 18:
[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)

Edit:  Forgot to add link for reinstalling XP's IPL:
[http://members.iinet.net.au/~herman546/p18.html](http://members.iinet.net.au/~herman546/p18.html)

---

### Post by presence1960 on 2009-08-16
before you do anything , boot from the Ubuntu Live Cd and choose "try ubuntu without any changes", when the desktop loads come back here and download to the desktop the Boot Info Script 0.32 from my signature line. Once that is on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on the desktop which contains info about your setup & boot process. paste the entire contents of that file here, then highlight the pasted text and click the # sign on the toolbar to place code tags around the text. This info will show us exactly what you have - no guessing, no maybes.

here is GRUB error 17 from the GRUB manual: 
17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

---

### Post by eewoz on 2009-08-17
presence1960,

Thank you for responding.  I believe I followed your instructions properly but I do not believe the RESULTS.txt file was created.  The screen from the terminal that I ran the script from is:

  ```
 ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
/home/ubuntu/Desktop/boot_info_script032.sh: line 3: syntax error near unexpected token `newline'
/home/ubuntu/Desktop/boot_info_script032.sh: line 3: `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">'
ubuntu@ubuntu:~$ 
```Also when I select Places/Desktop or any of the Places selections the "hour glass" comes up for a while but then nothing is displayed.  When I try to save the link Boot Info Script 0.32 that you placed in your response by using Save Link As I am able to browse the various directories so I know that I successfully  download the info_script.

What do you recommend next?

---

### Post by presence1960 on 2009-08-17
> **eewoz said:**
> presence1960,

Thank you for responding.  I believe I followed your instructions properly but I do not believe the RESULTS.txt file was created.  The screen from the terminal that I ran the script from is:

  ```
 ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
/home/ubuntu/Desktop/boot_info_script032.sh: line 3: syntax error near unexpected token `newline'
/home/ubuntu/Desktop/boot_info_script032.sh: line 3: `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">'
ubuntu@ubuntu:~$ 
```Also when I select Places/Desktop or any of the Places selections the "hour glass" comes up for a while but then nothing is displayed.  When I try to save the link Boot Info Script 0.32 that you placed in your response by using Save Link As I am able to browse the various directories so I know that I successfully  download the info_script.

What do you recommend next?

Click on the link and then you will be brought to a page where you can download the boot info script. save link as will not work. Once you download the boot info script put it on desktop and run that command again from terminal.

---

### Post by eewoz on 2009-08-17
> **presence1960 said:**
> Click on the link and then you will be brought to a page where you can download the boot info script. save link as will not work. Once you download the boot info script put it on desktop and run that command again from terminal.

OK.  Sorry about that.  Here is what I got...


```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbf18bf18

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,156,224    78,156,162   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="8E4453D64453C01F" TYPE="ntfs" 

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


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

```

---

### Post by presence1960 on 2009-08-17
It looks like you installed Ubuntu to your external drive. You had your external unplugged when you ran the boot info script. You installed GRUB to MBR of your internal drive which overwrote the windows bootloader. So now when you boot GRUB takes over and looks for menu.lst which is on your external drive. if your external is unplugged you will get a GRUB error because it can't find menu.lst.

You have 2 choices: you can leave Ubuntu on the external drive. if you do that you will need to restore Windows bootloader to MBR of internal drive and restore GRUB to MBR of external drive. Then set the external in BIOS to boot before the internal. This way if you boot without external drive plugged in windows bootloader will take over, if you boot with the external GRUB will take over.

Or you can reinstall Ubuntu to your internal disk...your choice. If you need help post back, either option is not too difficult.

---

### Post by eewoz on 2009-08-18
> **presence1960 said:**
> It looks like you installed Ubuntu to your external drive. You had your external unplugged when you ran the boot info script. You installed GRUB to MBR of your internal drive which overwrote the windows bootloader. So now when you boot GRUB takes over and looks for menu.lst which is on your external drive. if your external is unplugged you will get a GRUB error because it can't find menu.lst.

You have 2 choices: you can leave Ubuntu on the external drive. if you do that you will need to restore Windows bootloader to MBR of internal drive and restore GRUB to MBR of external drive. Then set the external in BIOS to boot before the internal. This way if you boot without external drive plugged in windows bootloader will take over, if you boot with the external GRUB will take over.

Or you can reinstall Ubuntu to your internal disk...your choice. If you need help post back, either option is not too difficult.

This is starting to make sense.  I think I want to reinstall Ubuntu to my internal disk.  How should I best go about that?  It seems like I somehow have to uninstall Ubuntu first.

---

### Post by presence1960 on 2009-08-18
If you want to install Ubuntu to internal hard disk, this is what I would do:
1. you need to back up your files. With the external disk plugged in boot from the Live CD and choose "try Ubuntu without any changes", when the destop loads go System > Administration > Partition Editor. I am assuming here there are no files on the external that you need to keep. Format the external drive and create partition(s), then from the Live CD copy all the files over from the windows disk you wish to save in case of unexpected data loss. After copying files over from the live cd unmount the external by right clicking it's icon on desktop and choosing unmount, when umnmounted unplug the external drive.

2. Hopefully you defragged XP prior to installing Ubuntu. if you did not you really need to do that before trying to install because you are going to shrink XPs partition to make room for Ubuntu. Unfortunately you overwrote the windows bootloader with GRUB, so this will entail an extra step. You will need to boot the windows install CD  and do [this]("http://ubuntuforums.org/showthread.php?t=1014708") to restore the windows bootloader to MBR of internal disk. Once complete reboot without the windows CD and make sure it boots into windows. Then defrag XP at least once, maybe twice for good measure. If you defragged XP just go to #3.

3. Now you have files backed up and XP defragged you are ready to install Ubuntu. Boot the Ubuntu Live CD (external drive still unplugged), when you get to the window with the install options choose Guided resize. The next window will have a screenshot with your Internal disk and it's partition(s). Grab the right side of the XP partition and drag it to the left until you have created the Ubuntu partition with the amount of space you want it to have. I would recommend no less than 15 or 20 Gb so you have some space for storage & updates. Continue with the rest of the process and the installer will do the rest. Any questions post back here.

---

### Post by eewoz on 2009-08-18
> **presence1960 said:**
> If you want to install Ubuntu to internal hard disk, this is what I would do:
1. you need to back up your files. With the external disk plugged in boot from the Live CD and choose "try Ubuntu without any changes", when the destop loads go System > Administration > Partition Editor. I am assuming here there are no files on the external that you need to keep. Format the external drive and create partition(s), then from the Live CD copy all the files over from the windows disk you wish to save in case of unexpected data loss. After copying files over from the live cd unmount the external by right clicking it's icon on desktop and choosing unmount, when umnmounted unplug the external drive.

2. Hopefully you defragged XP prior to installing Ubuntu. if you did not you really need to do that before trying to install because you are going to shrink XPs partition to make room for Ubuntu. Unfortunately you overwrote the windows bootloader with GRUB, so this will entail an extra step. You will need to boot the windows install CD  and do [this]("http://ubuntuforums.org/showthread.php?t=1014708") to restore the windows bootloader to MBR of internal disk. Once complete reboot without the windows CD and make sure it boots into windows. Then defrag XP at least once, maybe twice for good measure. If you defragged XP just go to #3.

3. Now you have files backed up and XP defragged you are ready to install Ubuntu. Boot the Ubuntu Live CD (external drive still unplugged), when you get to the window with the install options choose Guided resize. The next window will have a screenshot with your Internal disk and it's partition(s). Grab the right side of the XP partition and drag it to the left until you have created the Ubuntu partition with the amount of space you want it to have. I would recommend no less than 15 or 20 Gb so you have some space for storage & updates. Continue with the rest of the process and the installer will do the rest. Any questions post back here.

Boy did I luck out (I think).  I tried doing step 2 first.  But my Windows install CD would not allow me to boot up into Windows.  One of the messages that came up said that it could not find any FAT32 files on the drive.  Uh Oh.  Fortunately I have been regularly backing up my computer with a program called Acronis, but I have been backing them up onto the USB drive that we think Ubuntu got installed on.  When I saw the USB drive spinning during the install process I remember thinking that it probably wasn't such a good idea to be doing the install with my backup hardrive plugged into the system.  But it was too late at that point.

I took my USB drive in to work and plugged it in to my computer there and fortunately it looks like all of my backup files are still in tact.  So tomorrow I will see if I can make the Acronis software do a restore.  Hopefully it will completely restore the hardrive including Windows.  When I bought the software it was my understanding that that is what it would do.  I'll find out tomorrrow.

Thank you for your help.  I will let you know what happens.

---

### Post by presence1960 on 2009-08-18
If Acronis restores your windows image successfully you may be able to boot right into windows. If it still does not boot into windows after restoring the windows image you should then be able to boot off the windows CD and restore the windows bootloader to MBR as outlined in step # 2. 

If your Ubuntu install is intact you can just install GRUB to MBR of the external disk. But lets wait & see what happens with Windows first. Post back and let us know what happens

---

### Post by travmon69 on 2009-08-18
latest supergrubdisk  live cd  always  save  me  on the fly for   when i mess  up mbr   or  grub.   [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)  good  luck   an  have fun!

---

### Post by presence1960 on 2009-08-18
> **travmon69 said:**
> latest supergrubdisk  live cd  always  save  me  on the fly for   when i mess  up mbr   or  grub.   [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)  good  luck   an  have fun!

That is an option, but i prefer to do so from terminal or install CDs. I have a copy of Super GRUB Disk but have not used it since my beginning days of Ubuntu.

That is the beauty of Linux: in most instances there are usually more than one method to accomplish the same task

---

### Post by eewoz on 2009-08-19
> **presence1960 said:**
> If Acronis restores your windows image successfully you may be able to boot right into windows. If it still does not boot into windows after restoring the windows image you should then be able to boot off the windows CD and restore the windows bootloader to MBR as outlined in step # 2. 

If your Ubuntu install is intact you can just install GRUB to MBR of the external disk. But lets wait & see what happens with Windows first. Post back and let us know what happens

It looks like Acronis did its job!  Windows is up and running.  It even restored the windows bootloader into MBR.  

There is a decent chance that the Ubuntu install is still intact.  How can I get GRUB into the MBR of the external disk?

---

### Post by presence1960 on 2009-08-19
> **eewoz said:**
> It looks like Acronis did its job!  Windows is up and running.  It even restored the windows bootloader into MBR.  

There is a decent chance that the Ubuntu install is still intact.  How can I get GRUB into the MBR of the external disk?

Excellent. First I need you to boot the Ubuntu Live Cd with your external plugged in and choose "try Ubuntu without any changes", when the desktop loads open a terminal and run this command ```
sudo fdisk -l
``` That is a lowercase L at the end. post the output back here and I will give you the commands to put GRUB on MBR of the external disk.

---

### Post by presence1960 on 2009-08-19
or if you're brave, you should be after all this, plus I am sure you will have learned a lot after this settles in, try this without my help:
```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,4)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd1,4)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd1)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

In #6 use setup (hd1)
Then one more step, reboot and go into BIOS and set the external drive to boot before the internal drive. This will make it so when you boot without the external windows will boot and when you boot with the external GRUB will take over and you can boot into Ubuntu.

---

### Post by eewoz on 2009-08-23
> **presence1960 said:**
> Excellent. First I need you to boot the Ubuntu Live Cd with your external plugged in and choose "try Ubuntu without any changes", when the desktop loads open a terminal and run this command ```
sudo fdisk -l
``` That is a lowercase L at the end. post the output back here and I will give you the commands to put GRUB on MBR of the external disk.

Here is the results of sudo fdisk -l

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbf18bf18

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f0e969b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38587   309950046    7  HPFS/NTFS
/dev/sdb2           38588       38913     2618595    5  Extended
/dev/sdb5           38588       38891     2441848+  83  Linux
/dev/sdb6           38892       38913      176683+  82  Linux swap / Solaris


```I tried what you suggested in your "if you feel brave" reply and got error 17 again, so I must have done something wrong. 

In the mean time I am going to try to learn about hd0 and sda and sda1 etc.

Thank you for all of your help.

---

### Post by presence1960 on 2009-08-23
> **eewoz said:**
> Here is the results of sudo fdisk -l

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbf18bf18

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f0e969b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38587   309950046    7  HPFS/NTFS
/dev/sdb2           38588       38913     2618595    5  Extended
/dev/sdb5           38588       38891     2441848+  83  Linux
/dev/sdb6           38892       38913      176683+  82  Linux swap / Solaris


```I tried what you suggested in your "if you feel brave" reply and got error 17 again, so I must have done something wrong. 

In the mean time I am going to try to learn about hd0 and sda and sda1 etc.

Thank you for all of your help.

Boot off the Ubuntu live CD with your external plugged in. Choose "try ubuntu without any changes". When the desktop loads open a terminal and do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,4)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd1,4)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd1)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

In # 6 use setup (hd1) to put GRUB on MBR of sdb. just so you understand what we are doing here sda = (hd0), sdb = (hd1), if you had an sdc it would be (hd2) and so on.

---

### Post by presence1960 on 2009-08-23
> **eewoz said:**
> Here is the results of sudo fdisk -l

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbf18bf18

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f0e969b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38587   309950046    7  HPFS/NTFS
/dev/sdb2           38588       38913     2618595    5  Extended
/dev/sdb5           38588       38891     2441848+  83  Linux
/dev/sdb6           38892       38913      176683+  82  Linux swap / Solaris


```I tried what you suggested in your "if you feel brave" reply and got error 17 again, so I must have done something wrong. 

In the mean time I am going to try to learn about hd0 and sda and sda1 etc.

Thank you for all of your help.

is your external set to boot first in your hard disk boot order? if so then those commands should be root (hd0,4) & setup (hd0).

---

### Post by eewoz on 2009-08-24
> **presence1960 said:**
> is your external set to boot first in your hard disk boot order? if so then those commands should be root (hd0,4) & setup (hd0).

I'm lost.  I am still getting ERROR 17.   Here is my latest from Boot Info Script


```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb5 and 
                       looks at sector 622341434 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbf18bf18

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,156,224    78,156,162   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8f0e969b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   619,900,154   619,900,092   7 HPFS/NTFS
/dev/sdb2         619,900,155   625,137,344     5,237,190   5 Extended
/dev/sdb5         619,900,218   624,783,914     4,883,697  83 Linux
/dev/sdb6         624,783,978   625,137,344       353,367  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="8E4453D64453C01F" TYPE="ntfs" 
/dev/sdb1: UUID="55D123D9E79ABF54" TYPE="ntfs" 
/dev/sdb5: UUID="f032dddf-89ab-4e5f-81b1-50b01c8d0fba" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="e8994609-be74-4f93-a33c-bdbde8e63912" TYPE="swap" 

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


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

=========================== sdb5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=f032dddf-89ab-4e5f-81b1-50b01c8d0fba ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f032dddf-89ab-4e5f-81b1-50b01c8d0fba

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        f032dddf-89ab-4e5f-81b1-50b01c8d0fba
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f032dddf-89ab-4e5f-81b1-50b01c8d0fba ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        f032dddf-89ab-4e5f-81b1-50b01c8d0fba
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f032dddf-89ab-4e5f-81b1-50b01c8d0fba ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        f032dddf-89ab-4e5f-81b1-50b01c8d0fba
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=f032dddf-89ab-4e5f-81b1-50b01c8d0fba /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=e8994609-be74-4f93-a33c-bdbde8e63912 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 318.6GB: boot/grub/menu.lst
 318.6GB: boot/grub/stage2
 318.8GB: boot/initrd.img-2.6.28-11-generic
 318.8GB: boot/vmlinuz-2.6.28-11-generic
 318.8GB: initrd.img
 318.8GB: vmlinuz
ubuntu@ubuntu:~/Desktop$ 


```

It looks to me like I have Grub on both hard drives and they both go looking to partition 5 of the second hard drive for menu.lst. 

 fdisk -l says 

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbf18bf18

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f0e969b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38587   309950046    7  HPFS/NTFS
/dev/sdb2           38588       38913     2618595    5  Extended
/dev/sdb5           38588       38891     2441848+  83  Linux
/dev/sdb6           38892       38913      176683+  82  Linux swap / Solaris

```

It looks like sda is my internal drive and sdb is my external drive.  I am pretty sure that I have my bios set to boot from the external drive first so wouldn't that make my external drive be sda?

I tried several combinations of drives with root and setup in grub but I will leave things a lone until I get another reading from you.

---

### Post by presence1960 on 2009-08-24
Ok, take a deep breath, this can be frustrating. First bit of info I need is for you to boot and go into BIOS. I need for you to give me the boot order of your devices in BIOS. Then we shall proceed.

---

### Post by eewoz on 2009-08-25
> **presence1960 said:**
> Ok, take a deep breath, this can be frustrating. First bit of info I need is for you to boot and go into BIOS. I need for you to give me the boot order of your devices in BIOS. Then we shall proceed.

OK Presence, here is what I found.
1st device is DVD reader
2nd device is external USB hard drive
3rd device is internal hard drive

As you may recall, windows is on the internal drive and Ubuntu is on the external drive.

Thanks.

---

### Post by RabbitWho on 2009-08-25
I don't know anything about computers but when this happened to me (grub 17) I put the recovery disk for windows into the computer, went through the directions, opened the terminal (command prompt) and typed in: 

fixmbr
[pressed enter and then]
fixboot 
[and pressed enter again]
and then it was fine. 

No idea if this would help in your situation, but it only takes a few minutes anyway. 

Don't worry there will be a way to get it back anyway. 

If you don't have a recovery disk i'm pretty sure windows lets you download them free? Anyone know anything more about this or if it would work in this situation?

---

### Post by eewoz on 2009-08-25
> **RabbitWho said:**
> I don't know anything about computers but when this happened to me (grub 17) I put the recovery disk for windows into the computer, went through the directions, opened the terminal (command prompt) and typed in: 

fixmbr
[pressed enter and then]
fixboot 
[and pressed enter again]
and then it was fine. 

No idea if this would help in your situation, but it only takes a few minutes anyway. 

Don't worry there will be a way to get it back anyway. 

If you don't have a recovery disk i'm pretty sure windows lets you download them free? Anyone know anything more about this or if it would work in this situation?

Interesting.  Was GRUB working for you and then it stopped working and this procedure fixed it or did GRUB never work until you went through the procedure?

---

### Post by dsimages on 2009-08-25
it seems as if you need to remove grub from the internal hd first. you can do this by using ms-sys in a terminal of the live cd. Google ms-sys for download and usage instructions. ms-sys will restore the mbr of the internal hd.

Im assuming that your external hard drive is 320gb. if that is the case you will be using hd1 in all of the codes that he has given you. (im not exactly sure though, im having the same issues you are and am following this thread).

I would repair the mbr of the internal while you wait for a response from 'presence' though.

---

### Post by RabbitWho on 2009-08-25
> **eewoz said:**
> Interesting.  Was GRUB working for you and then it stopped working and this procedure fixed it or did GRUB never work until you went through the procedure?

Everything was working fine till i deleted a partition. Happened two different times, once with grub error 17 the other time with grub error 22, the procedure I just talked about sorted out 17 and I just re-installed Ubuntu for 22 (the windows fix didn't work that time)

I think it's worth a shot in any case 'cause like i said it only takes a few minutes. windows also have an automatic fix through the gui (on the vista disk anyway) but that seems to be useless. And there's the option to restore your whole pc. Maybe you could just do that and start again? 
There is also a recovery that says it won't damage your files, and that has a box you can tick to recover "boot" 
I've never used the XP disk though.

---

### Post by Bartender on 2009-08-26
It looks like presence has a plan, and he's *much* better than me at the command line and making sense of long text files.

So I don't want to step on his toes.  But one thing that jumps out at me is your boot priority in BIOS.  I don't see how you're ever going to get this resolved when the BIOS is sending the PC to the external before the internal drive.

Well, let me think about this...you could fix things as long as you know exactly what you're doing.  For example, if you want to fix the Windows MBR you've got to have the external unplugged.

We worked on a similar situation a few days ago

[http://ubuntuforums.org/showthread.php?t=1245199](http://ubuntuforums.org/showthread.php?t=1245199)

Might be helpful to you...

---

### Post by eewoz on 2009-08-26
All of you seem to be agreeing that I should clean up my windows MBR.  I successfully did this using my Acronis backup.  I repeated some of the steps that Presence had me do earlier including reinstalling/setting up grub.  I will now give it a test.  I will report back with my results.

---

### Post by eewoz on 2009-08-26
I still don't have it yet...I still got ERROR 17 but at least I did not mess up windows.  I am able to properly control the boot order by going into the bios.  When I select the external drive as the first drive after the DCD drive GRUB starts up but stops with ERROR 17.  When I select the internal drive as the first drive after the DVD drive windows successfully boots up.  A puzzling thing to me though is when I run Ubuntu off of the CD with the external drive selected as the first hard drive fdisk -l says that the internal drive is sda and the external drive is sdb.  My external drive has a windows partition plus the Ubuntu partition.  The Windows partition is the first partition.  Perhaps that has something to do with all of my misery.

---

### Post by presence1960 on 2009-08-26
> **eewoz said:**
> I still don't have it yet...I still got ERROR 17 but at least I did not mess up windows.  I am able to properly control the boot order by going into the bios.  When I select the external drive as the first drive after the DCD drive GRUB starts up but stops with ERROR 17.  When I select the internal drive as the first drive after the DVD drive windows successfully boots up.  A puzzling thing to me though is when I run Ubuntu off of the CD with the external drive selected as the first hard drive fdisk -l says that the internal drive is sda and the external drive is sdb.  My external drive has a windows partition plus the Ubuntu partition.  The Windows partition is the first partition.  Perhaps that has something to do with all of my misery.

It may be that your USB boot is giving you the problem. Everything else seems to be configured correctly. I hate to do this but run the Boot Info Script one more time with your USB plugged in.

---

### Post by eewoz on 2009-08-27
> **presence1960 said:**
> It may be that your USB boot is giving you the problem. Everything else seems to be configured correctly. I hate to do this but run the Boot Info Script one more time with your USB plugged in.

Boot Info Script says:

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb5 and 
                       looks at sector 622341434 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbf18bf18

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,156,224    78,156,162   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8f0e969b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   619,900,154   619,900,092   7 HPFS/NTFS
/dev/sdb2         619,900,155   625,137,344     5,237,190   5 Extended
/dev/sdb5         619,900,218   624,783,914     4,883,697  83 Linux
/dev/sdb6         624,783,978   625,137,344       353,367  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="8E4453D64453C01F" TYPE="ntfs" 
/dev/sdb1: UUID="55D123D9E79ABF54" TYPE="ntfs" 
/dev/sdb5: UUID="f032dddf-89ab-4e5f-81b1-50b01c8d0fba" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="e8994609-be74-4f93-a33c-bdbde8e63912" TYPE="swap" 

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


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

=========================== sdb5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=f032dddf-89ab-4e5f-81b1-50b01c8d0fba ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f032dddf-89ab-4e5f-81b1-50b01c8d0fba

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        f032dddf-89ab-4e5f-81b1-50b01c8d0fba
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f032dddf-89ab-4e5f-81b1-50b01c8d0fba ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        f032dddf-89ab-4e5f-81b1-50b01c8d0fba
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f032dddf-89ab-4e5f-81b1-50b01c8d0fba ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        f032dddf-89ab-4e5f-81b1-50b01c8d0fba
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=f032dddf-89ab-4e5f-81b1-50b01c8d0fba /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=e8994609-be74-4f93-a33c-bdbde8e63912 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 318.6GB: boot/grub/menu.lst
 318.6GB: boot/grub/stage2
 318.8GB: boot/initrd.img-2.6.28-11-generic
 318.8GB: boot/vmlinuz-2.6.28-11-generic
 318.8GB: initrd.img
 318.8GB: vmlinuz


```

---

### Post by presence1960 on 2009-08-27
does Ubuntu boot with the external plugged in? When do you get error 17?

If you get it trying to boot windows change the windows entry in menu.lst to

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
rootnoverify    (hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


```

maybe try switching the port the external USB is plugged into? Everything looks good sda has Windows on MBR and the external has GRUB. Grub is pointing to the right partition for menu.lst. There is something amiss with your ability to boot from USB.

---

### Post by eewoz on 2009-08-27
> **presence1960 said:**
> does Ubuntu boot with the external plugged in? When do you get error 17?

If you get it trying to boot windows change the windows entry in menu.lst to

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
rootnoverify    (hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


```maybe try switching the port the external USB is plugged into? Everything looks good sda has Windows on MBR and the external has GRUB. Grub is pointing to the right partition for menu.lst. There is something amiss with your ability to boot from USB.

Grub tries to start up when the external is plugged in.  That is when I get the error 17.  Windows boots up fine.

I got my hands on a second external drive.  I thought I would try installing Ubuntu on that drive.  I got as far as where they ask you where you want to install it.  I went to the advanced section and there was a message saying "This comp[uter has no operating system on it."  Is that normal?  It was not completely obvious to me how to make the installer install only on the external hard drive so I quit.  It is not real obvious to me how to tell it to install on only the external drive and not on the internal drive, so I am going to investigate a little bit and see if I can find some clear-cut instructions.

---

### Post by presence1960 on 2009-08-27
> **eewoz said:**
> Grub tries to start up when the external is plugged in.  That is when I get the error 17.  Windows boots up fine.

I got my hands on a second external drive.  I thought I would try installing Ubuntu on that drive.  I got as far as where they ask you where you want to install it.  I went to the advanced section and there was a message saying "This comp[uter has no operating system on it."  Is that normal?  It was not completely obvious to me how to make the installer install only on the external hard drive so I quit.  It is not real obvious to me how to tell it to install on only the external drive and not on the internal drive, so I am going to investigate a little bit and see if I can find some clear-cut instructions.

Everything looks good on your boot info script. Windows boots with the external unplugged. At this juncture I would seem to think your USB drive is the problem or you have a problem with your BIOS/motherboard booting from USB.

---

### Post by eewoz on 2009-08-28
> **presence1960 said:**
> Everything looks good on your boot info script. Windows boots with the external unplugged. At this juncture I would seem to think your USB drive is the problem or you have a problem with your BIOS/motherboard booting from USB.

I made some progress???  I have progressed from getting error 17 to getting error 18!  I upgraded my BIOS to the latest version and I now get error 18 rather than error 17.  Maybe my computer is just too old for new tricks.

---

### Post by presence1960 on 2009-08-28
> **eewoz said:**
> I made some progress???  I have progressed from getting error 17 to getting error 18!  I upgraded my BIOS to the latest version and I now get error 18 rather than error 17.  Maybe my computer is just too old for new tricks.

if you have an old computer it probably isn't capable of booting from USB. Refer to your manufacturer's documentation. if you don't have it go to their web site and retrieve it for your model machine.

At this point though I would partition your internal hard disk (10-15 GB for Ubuntu) and install Ubuntu on there and use the external for storage.

---

### Post by eewoz on 2009-08-29
> **presence1960 said:**
> if you have an old computer it probably isn't capable of booting from USB. Refer to your manufacturer's documentation. if you don't have it go to their web site and retrieve it for your model machine.

At this point though I would partition your internal hard disk (10-15 GB for Ubuntu) and install Ubuntu on there and use the external for storage.

I finally have success!  I was able to load Ubuntu on to one of my external hard drives.  I had to set up a small partition at the beginning of the drive to hold Grub.  Evidently if that first partition is too large the it causes problems with the bios.  What a battle! But the world now has one more Ubuntu user.

Thank you for all of your help.

---

