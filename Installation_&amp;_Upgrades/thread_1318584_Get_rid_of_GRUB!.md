---
title: "Get rid of GRUB!"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by Dr.Fuzzy on 2009-11-07
Hi,

this is my fdisk -l info:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32c2da86

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb14cb14

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       20073   161236341    7  HPFS/NTFS
/dev/sdb2           20074       30515    83875365    5  Extended
/dev/sdb5           20074       30084    80413326   83  Linux
/dev/sdb6           30085       30515     3461976   82  Linux swap / Solaris

for some reason GRUB is installed in both HDs (sda and sdb) probably causing a 15 second GRUB loading delay at boot. How in the earth I can get rid of GRUB from sda (drive used for storage) without messing the HD?

Please help!

---

### Post by dhavalbbhatt on 2009-11-07
> **Dr.Fuzzy said:**
> Hi,

for some reason GRUB is installed in both HDs (sda and sdb) probably causing a 15 second GRUB loading delay at boot. How in the earth I can get rid of GRUB from sda (drive used for storage) without messing the HD?

Please help!

Are you sure GRUB on two HDDs is causing a 15 second delay? Theoretically, GRUB is only supposed to boot from the HDD which is set as root within GRUB. Please verify that GRUB on 2 HDDs is causing the delay.

---

### Post by Dr.Fuzzy on 2009-11-07
How can I check that? Well this is just a guess cause I can't think of anything else causing this delay! Seriously after bios post hardisk works like crazy and it takes about 15secs for GRUB menu to appear! Anyhow, having GRUB on both sdb and sda is redundant, isn't? Unless it is needed to be on both drives for some reason? If not how can I remove it from sda?

---

### Post by Dr.Fuzzy on 2009-11-07
C'mon!

---

### Post by jheaton5 on 2009-11-07
The fact that grub is installed on both partitions is not causing the delay you are experiencing.

Are you using grub-legacy or grub2?

---

### Post by Dr.Fuzzy on 2009-11-07
I'm running 9.10 so I assume GRUB2.

---

### Post by jheaton5 on 2009-11-07
Let's not assume.  If you upgraded from 9.04 you are probably using grub-legacy.  If you did a fresh install of 9.10 then you are probably using grub2.  How did you get to 9.10?

---

### Post by Dr.Fuzzy on 2009-11-07
Well, I did a fresh install so that makes me GRUB2 then (1.74Beta I think reports on the GRUB menu).

---

### Post by jheaton5 on 2009-11-07
> **Dr.Fuzzy said:**
> Well, I did a fresh install so that makes me GRUB2 then (1.74Beta I think reports on the GRUB menu).

OK, good.
I have a fresh install of 9.10 using grub2.  I'm used to the immediate response of the old grub to menu selections.  There seems to be a couple of delays in grub2, one from BIOS to Grub menu and another from menu selection to boot.  It seems like a long time, but is only a second or two.  If you are really experiencing a delay of 15 seconds, where in the sequence are you experiencing the delay?

---

### Post by Dr.Fuzzy on 2009-11-07
Post BIOS to GRUB ~15 sec. Any ideas why GRUB was installed in sda & sdb in the first place. I only need it in sdb where my 9.10 is located. Help me get rid of it from sda!

---

### Post by jheaton5 on 2009-11-07
> **Dr.Fuzzy said:**
> Post BIOS to GRUB ~15 sec. Any ideas why GRUB was installed in sda & sdb in the first place. I only need it in sdb where my 9.10 is located. Help me get rid of it from sda!

Yes, grub is installed in the partition of the distro you are installing unless you tell it not to.  This option is available in step 7 of the ubuntu installer.  Other distros have different places where you select to install grub or not.  Not only that, but the last distro you install will have the controlling grub.

I'll have to reboot and time the delay on my machine.  I'll get back to you.

---

### Post by jheaton5 on 2009-11-07
Well, mine is 17 seconds.  I didn't realize it took that long.  I have no idea why it takes that long.  Although I can't say that I have been that annoyed by it.  I usually turn on the laptop and walk away to come back and I'm ready to log in.

---

### Post by dhavalbbhatt on 2009-11-07
I hate to think that it is GRUB 2.0 which is causing the delays. I am guessing the new GNOME coupled with a splashscreen associated with GRUB 2.0 in Ubuntu 9.10 is what is causing the delays.

---

### Post by jheaton5 on 2009-11-07
I don't think so.  Yes, the splash and new gnome will affect the speed of the system load, but that would manifest itself after the menu selection and before the login screen.  If I had to guess, and I never guess ;), I would say it is the new grub just takes longer to load.

---

### Post by dhavalbbhatt on 2009-11-07
Well - how about the splashscreen for GRUB 2.0? Doesn't GRUB 2.0 look for a splashscreen at the time of booting up? Maybe that is the reason why it is slow...Also realize that GRUB 2.0 is not really 2.0 it is 1.97 and still in beta - which surprises me because Canonical should have never used a beta version for a release like Karmic. With ext4 already a major upgrade, GRUB 2.0 wasn't required. On top of that, they somehow managed to break partition manager in the desktop installation CD. Most of the posts that I see here are related to the above 2-3 issues. Hope things will change for the better with Lucid, which is a LTS release.

The following post might be helpful though -

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by presence1960 on 2009-11-07
> **Dr.Fuzzy said:**
> Post BIOS to GRUB ~15 sec. Any ideas why GRUB was installed in sda & sdb in the first place. I only need it in sdb where my 9.10 is located. Help me get rid of it from sda!
That GRUB in sda is not hurting or slowing anything down. You can only boot from one MBR at a time and that is controlled in your BIOS in the hard disk boot order. So if you have sdb set as first hard disk boot priority and sda as second, your GRUB on sda will never even be read as sdb is set to boot first. Your MBR on sdb will be read and it will be GRUB in that MBR which points to the OS you select in GRUB menu.

---

### Post by louieb on 2009-11-07
Grub has two parts stage1 - which goes in the MBR of the boot drive. And stage2 thats in your Ubuntu install. Its quite possible for stage1 to be in the MBR of sda and the main GRUB program to be in your Ubuntu install on on another drive.  

> probably causing a 15 second GRUB loading delay at boot.

Most of that time is taken by BIOS doing its post stuff. Not much you can do about that. 

> Also realize that GRUB 2.0 is not really 2.0 it is 1.97 and still in beta

Even after 10 year Grub legacy still called itself a beta (v.097) I'm not betting that we will ever see GRUB 2.0.

---

### Post by oldefoxx on 2009-11-08
Either Grub or the Windows boot process has to be located on the first partition of disk 0.  Both can actually reside there, but the boot process will only point to one of them.  Grub will automatically pick up on the Windows presences and include it as well.  If you want the Windows boot method to be used, you can try to download bootpart (a Windows/DOS program) and use it to add lines to Boot.ini so that it will include ways of getting to Linux or Ubuntu.  Generally, Grub is easier to do.

You can also tell Grub to put itself somewhere else, but BootPart is not going to check every logical partition for the presence of Linux (or Ubuntu).  With bootpart it is best to plan on having Ubuntu in primary partions, even as the first partition on any drive.  Normally, Windows sees the first partition that it recognizes on drive 0 as Drive C:  Ubuntu sees the first partion on drive 0 as either /dev/sda1 or /dev/hda1, regardless of what file system is used there.

But a problem can exist in some PCs that mix SATA and EIDE drives even USB external drives, because the mix may put one interface before another at different points in a process.  What you need to do is make sure that you Grub or Windows boot process is on the Drive that Windows sees as Drive C.  This is crutial, because this is the real disk 0, regardless of what another operating system might think at any given time.  If you have a Grub boot process on any other drive, it can just be deleted, as it won't be used unless you work out how to use bootpart or other efforts to have the disk 0 boot process point to this as a second boot menu.

Since Grub may end up on a non-FAT and not-NTFS partition, it is generally better to modify and/or delete it from within an operating system like Ubuntu, which handles the folders and files of different files systems with more grace.  Under Windows, you normally only see FAT and NTFS partitions.  There is software for Windows that will add a new driver to it for handling EXT2 drives, and that actually works with EXT3 as well, but without the journalling found in EXT3.  Haven't seen anything yet for Windows that will do the same for EXT4 and other file system types.  Working with drivers like this means that partitions, folders and files can be shared across several operation systems, though only one is normally running at a time.

To have multiple operating systems at work at once and to be able to switch between them without rebooting, look for products in the Virtual Machine (VM) category.  They can allow this.  One that I like is Sun's VirtualBox.  The operating systems are then classified as either host or one of several guests or clients.  It's quite remarkable what mixes of this nature can permit you to do,  but it does require more RAM and hard drive space to take the most advantage of it.

I hope all this helps.

---

### Post by abdusamed on 2009-11-08
i too got some prob.. when i start my computer and select ubunt 9.10 to boot.. the conputer waits and loads some crap .. here what it shows 
```

hdd[0] nowulibr
hdd[1] checking 
```

its something shows like that. can't remeber word for word

help :(

---

### Post by Dr.Fuzzy on 2009-11-08
...but the question still remains! How can I get rid of GRUB from sda? Ok, I got it, it may not make a difference at all located on both sdb & sda but again I don't see why.

...the ~15 sec are spend for loading GRUB, I'm not talking about post BIOS messages.

---

### Post by sklyer on 2009-11-08
Forgive me, Dr. Fuzzy, but can I suggest that this is a case of "It ain't broke!" As I read the posts, it seems that this delay is consistent across several systems, so the fact that you have grub on two hard drives is irrelevant. Furthermore, Grub is teeny tiny, so you shouldn't be worried about space issues. And as louieb points out, you might have stage 1 on your windows install (if you have one) and stage 2 on your Ubuntu install. And lastly, you don't really want to mess with Grub -- your computer boots, albeit more slowly than you'd like. Is it really prudent to go messing around in there?

---

### Post by louieb on 2009-11-08
> **Dr.Fuzzy said:**
> ...but the question still remains! How can I get rid of GRUB from sda? 

you don't get rid of grub - you replace it. Break out your Win CD and put the win boot IPL code back in the MBR.

---

### Post by Dr.Fuzzy on 2009-11-08
Gyes, gyes wait a minute, I don't want to replace GRUB with the windows bootloader, never said that! It just doesn't make sense why GRUB was installed on both my physical drives (hda and hdb). Yep OK my system might be working, and sure GRUB doesn't take any space at all and it'aint broken and all that...I agree! Out of curiosity though is it possible to get rid of GRUB out of my sda leaving my system unharmed or not and how!

---

### Post by louieb on 2009-11-08
> **Dr.Fuzzy said:**
> ...It just doesn't make sense why GRUB was installed on both my physical drives (hda and hdb)...
It some cases it makes perfect sense. The boot section of the MBR is only 446 bytes long - Just enough room for some code to pass control to the main boot loader program.  Does not matter if that main program is GRUB, a Windows boot loader or some other.  If the install drive and the boot drive are different  ... repeating myself ... "Its quite possible for stage1 to be in the MBR of sda and the main GRUB program to be in your Ubuntu install on on another drive."

Truth is have not see anything to prove if GRUB stage1 is in the MBR of sda or sdb. Since it boots to GRUB - just  know its in one or the other.   Which drive is 1st in the boot order? 
> Out of curiosity though is it possible to get rid of GRUB out of my sda leaving my system unharmed or not and how!
The short of it yes you can.  2 hard drives = 2 MBR = room for two boot loaders.
Use the windows recovery console for your flavor of windows to restore the MBR to load the Windows boot loader.  Use the grub-setup command to put GRUBs stage1 code in the other.  
Then you can change the boot order in BIOS to switch between GRUB and the windows boot loader.

lol watching the NFL and NASCAR so if I don't make much sense I'm distracted.

---

### Post by presence1960 on 2009-11-08
> **Dr.Fuzzy said:**
> ...but the question still remains! How can I get rid of GRUB from sda? Ok, I got it, it may not make a difference at all located on both sdb & sda but again I don't see why.

...the ~15 sec are spend for loading GRUB, I'm not talking about post BIOS messages.

The only way I know how is to get rid of the info on MBR, but then your partition table will be invalid. I would leave it alone as the GRUB on sda is playing no part in the boot process unless you set sda as first boot in BIOS.

---

### Post by Dr.Fuzzy on 2009-11-08
> **louieb said:**
> If the install drive and the boot drive are different  ... repeating myself ... "Its quite possible for stage1 to be in the MBR of sda and the main GRUB program to be in your Ubuntu install on on another drive."

Truth is have not see anything to prove if GRUB stage1 is in the MBR of sda or sdb. Since it boots to GRUB - just  know its in one or the other.   Which drive is 1st in the boot order? 


Well, sdb contains Ubuntu 9.10 and WinXp, sda is just for storage and backups, I mean no OSs in this drive. Drive sdb is 1st in the boot order, 2nd is cdrom. 

If I get it right you mean on the XP recovery console fdisk /mbr on sdb and sda and then in Ubuntu grub-setup to reconfigure grub on sdb?

---

### Post by presence1960 on 2009-11-08
you can do what you want, but you are making much out of nothing. My Linux and windows OSs are now on sdc as well as GRUB 2. My sda which is a data storage drive has GRUB 0.97 on its MBR. My system boots fine from GRUB 2 ( which by the way takes a little longer than Legacy GRUB ). The Legacy GRUB 0.97 in MBR of sda plays no role in the boot process. Your machine is in the same situation. Your GRUB on sda plays no role in the boot process and is not the cause of the 15 second delay you say you have experienced. My personal opinion is you are being just a tad anal about this.

---

### Post by louieb on 2009-11-08
> Drive sdb is 1st in the boot order, 2nd is cdrom. 

That tells me GRUB is in the MBR of sdb. With both OSes on the same drive that changes what you can do. I just *******umed your windows install was on sda and sda was 1st in the boot order. 

Anyway enough guessing. Lets look Please follow the [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280")  and put the results.txt file in your next post. When you run the script GRUB2 will show up as the **unknown boot loader** - script has not been update yet to reconize GRUB2.

---

### Post by Dr.Fuzzy on 2009-11-09
Very handy script, well done! Here is the RESULTS.TXT .

```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb

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

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x32c2da86

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcb14cb14

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   322,472,744   322,472,682   7 HPFS/NTFS
/dev/sdb2         322,472,745   490,223,474   167,750,730   5 Extended
/dev/sdb5         322,472,808   483,299,459   160,826,652  83 Linux
/dev/sdb6         483,299,523   490,223,474     6,923,952  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="5294216094214835" LABEL="Storage" TYPE="ntfs" 
/dev/sdb1: UUID="8C80AECD80AEBCD8" LABEL="Live" TYPE="ntfs" 
/dev/sdb5: LABEL="KARMIC" UUID="0ff87809-15d3-4215-b049-fe72a7a652ec" TYPE="ext4" 
/dev/sdb6: UUID="f5e500df-341a-4bed-a05f-c159a5d033ef" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/delk/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=delk)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /TUTag=LQ1PNK /Kernel=TUKernel.exe 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional (TuneUp Backup)" /noexecute=optin /fastdetect /TUTag=LQ1PNK-BAK 

=========================== sdb5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,5)
search --no-floppy --fs-uuid --set 0ff87809-15d3-4215-b049-fe72a7a652ec
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 0ff87809-15d3-4215-b049-fe72a7a652ec
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=0ff87809-15d3-4215-b049-fe72a7a652ec ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 0ff87809-15d3-4215-b049-fe72a7a652ec
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=0ff87809-15d3-4215-b049-fe72a7a652ec ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8c80aecd80aebcd8
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=0ff87809-15d3-4215-b049-fe72a7a652ec /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=f5e500df-341a-4bed-a05f-c159a5d033ef none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 165.1GB: boot/grub/grub.cfg
 165.1GB: boot/initrd.img-2.6.31-14-generic
 165.1GB: boot/vmlinuz-2.6.31-14-generic
 165.1GB: initrd.img
 165.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  eb 63 90 d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |.c....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 07 8b  |...It.8,t.......|
00000040  f0 ac 3c 00 74 fc bb 07  00 b4 0e cd 10 eb f2 88  |..<.t...........|
00000050  4e 10 e8 46 00 73 2a fe  46 10 00 80 01 00 00 00  |N..F.s*.F.......|
00000060  00 00 00 00 ff fa eb 07  f6 c2 80 75 02 b2 80 ea  |...........u....|
00000070  74 7c 00 00 31 c0 8e d8  8e d0 bc 00 20 fb a0 64  |t|..1....... ..d|
00000080  7c 3c ff 74 02 88 c2 52  be 88 7d e8 24 01 be 05  ||<.t...R..}.$...|
00000090  7c f6 c2 80 74 48 b4 41  bb aa 55 cd 13 5a 52 72  ||...tH.A..U..ZRr|
000000a0  3d 81 fb 55 aa 75 37 83  e1 01 74 32 31 c0 89 44  |=..U.u7...t21..D|
000000b0  04 40 88 44 ff 89 44 02  c7 04 10 00 66 8b 1e 5c  |.@.D..D.....f..\|
000000c0  7c 66 89 5c 08 66 8b 1e  60 7c 66 89 5c 0c c7 44  ||f.\.f..`|f.\..D|
000000d0  06 00 70 b4 42 cd 13 72  05 bb 00 70 eb 73 b4 08  |..p.B..r...p.s..|
000000e0  cd 13 73 0a f6 c2 80 0f  84 d8 00 e9 82 00 66 0f  |..s...........f.|
000000f0  b6 c6 88 64 ff 40 66 89  44 04 0f b6 d1 c1 e2 02  |...d.@f.D.......|
00000100  88 e8 88 f4 40 89 44 08  0f b6 c2 c0 e8 02 66 89  |....@.D.......f.|
00000110  04 66 a1 60 7c 66 09 c0  75 4e 66 a1 5c 7c 66 31  |.f.`|f..uNf.\|f1|
00000120  d2 66 f7 34 88 d1 31 d2  66 f7 74 04 3b 44 08 7d  |.f.4..1.f.t.;D.}|
00000130  37 fe c1 88 c5 30 c0 c1  e8 02 08 c1 88 d0 5a 88  |7....0........Z.|
00000140  c6 bb 00 70 8e c3 31 db  b8 01 02 cd 13 72 29 8c  |...p..1......r).|
00000150  c3 60 1e b9 00 01 8e db  31 f6 bf 00 80 8e c6 fc  |.`......1.......|
00000160  f3 a5 1f 61 ff 26 5a 7c  be 8e 7d e8 44 00 eb 0e  |...a.&Z|..}.D...|
00000170  be 93 7d e8 3c 00 eb 06  be 9d 7d e8 34 00 be a2  |..}.<.....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  86 da c2 32 00 00 80 01  |...<.u.....2....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 02 4c 38 3a 00 00  |......?....L8:..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown MBR on /dev/sdb

00000000  eb 63 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |.c..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 00 00  00 00 00 80 01 00 00 00  |................|
00000060  00 00 00 00 ff fa eb 07  f6 c2 80 75 02 b2 80 ea  |...........u....|
00000070  74 7c 00 00 31 c0 8e d8  8e d0 bc 00 20 fb a0 64  |t|..1....... ..d|
00000080  7c 3c ff 74 02 88 c2 52  be 88 7d e8 24 01 be 05  ||<.t...R..}.$...|
00000090  7c f6 c2 80 74 48 b4 41  bb aa 55 cd 13 5a 52 72  ||...tH.A..U..ZRr|
000000a0  3d 81 fb 55 aa 75 37 83  e1 01 74 32 31 c0 89 44  |=..U.u7...t21..D|
000000b0  04 40 88 44 ff 89 44 02  c7 04 10 00 66 8b 1e 5c  |.@.D..D.....f..\|
000000c0  7c 66 89 5c 08 66 8b 1e  60 7c 66 89 5c 0c c7 44  ||f.\.f..`|f.\..D|
000000d0  06 00 70 b4 42 cd 13 72  05 bb 00 70 eb 73 b4 08  |..p.B..r...p.s..|
000000e0  cd 13 73 0a f6 c2 80 0f  84 d8 00 e9 82 00 66 0f  |..s...........f.|
000000f0  b6 c6 88 64 ff 40 66 89  44 04 0f b6 d1 c1 e2 02  |...d.@f.D.......|
00000100  88 e8 88 f4 40 89 44 08  0f b6 c2 c0 e8 02 66 89  |....@.D.......f.|
00000110  04 66 a1 60 7c 66 09 c0  75 4e 66 a1 5c 7c 66 31  |.f.`|f..uNf.\|f1|
00000120  d2 66 f7 34 88 d1 31 d2  66 f7 74 04 3b 44 08 7d  |.f.4..1.f.t.;D.}|
00000130  37 fe c1 88 c5 30 c0 c1  e8 02 08 c1 88 d0 5a 88  |7....0........Z.|
00000140  c6 bb 00 70 8e c3 31 db  b8 01 02 cd 13 72 29 8c  |...p..1......r).|
00000150  c3 60 1e b9 00 01 8e db  31 f6 bf 00 80 8e c6 fc  |.`......1.......|
00000160  f3 a5 1f 61 ff 26 5a 7c  be 8e 7d e8 44 00 eb 0e  |...a.&Z|..}.D...|
00000170  be 93 7d e8 3c 00 eb 06  be 9d 7d e8 34 00 be a2  |..}.<.....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  14 cb 14 cb 00 00 80 01  |...<.u..........|
000001c0  01 00 07 fe ff ff 3f 00  00 00 ea 8a 38 13 00 fe  |......?.....8...|
000001d0  ff ff 05 fe ff ff 29 8b  38 13 4a ac ff 09 00 00  |......).8.J.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

/home/delk/Downloads/boot_info_script032.sh: line 1233: cd: sda1: Transport endpoint is not connected
```

---

### Post by oldefoxx on 2009-11-09
I dn't know how mention of a CD-ROM drive crept in here, but CD drives are slow, very slow compared to hard drives.  If the system goes to the CD drive as part of the boot process, that would involve delay as the efforts to check for a bootable disk come into play - check for media present, if so, spin up, read the first track, check for the presence of a boot process, then go on to the next device if not.  Otherwise, boot.

The boot sequence is set in the BIOS, and has nothing to do with which operating system or boot method is employed.  Many PCs leave the CD-ROM boot method enabled and attempted before going to the hard drive, and others either disable it or reverse the order, so that the hard drive is checked and booted from first.  They can always go back into setup and re-enable the CD-ROM boot method when they need to.

Something that I wished Grub or something like it would do, is to scan each partition for a boot process, then determine what would boot up if that boot were employed, then presented this as a comprehensive list to choose from when you get to the point of choosing.  It should also mark which was the last boot choice made, in case you need to get back to where you were on the last logout or power off. It should know enough to mark any apparent boot choices as invalid or corrupted if it finds fault with the method found there.  And maybe it should harbor the ones found good, and offer to restore the ones found bad from among those harbored.

---

### Post by oldefoxx on 2009-11-09
> **Dr.Fuzzy said:**
> ...but the question still remains! How can I get rid of GRUB from sda? Ok, I got it, it may not make a difference at all located on both sdb & sda but again I don't see why.

...the ~15 sec are spend for loading GRUB, I'm not talking about post BIOS messages.

Simple.  Backup sda first, in case you prove yourself wrong.  Use a backup method that works from the CD drive to be on the safe side.  Then just go find /boot on sda and delete it, or rename it, to something like /xboot or /bootx.  Then reboot.  If the reboot works for both systems, you are safe to just go delete /xboot (or /bootx, or whatever you called it).  Then its gone, and no more issues in that regard.

If you can't reboot, then reverse the backup process and put everything back.  Or, if the restore method allows you to just do track 0 and the MBR, try restoring just that first.  If restoring just put you back where you were beforehand. you can repeat the process, but with your focus on sdb this time.  It is extremely uncommon for anyone to create a boot process that requires boot processes on more than one partition, so you should be able to get rid of one of these after you assure yourself of which one to let go by deleting.  To assume otherwise leaves an opening for mistakes to take place.

---

### Post by louieb on 2009-11-09
Just some observations.  
Looks like the MBR in both sda and sdb are setup to pass control to GRUB. Wonder how that happened. Also wonder what would boot if the boot order of the hard drives were flipped. - Just a guess that Windows would not boot - and don't know about Ubuntu. 

The GRUB menu looks like its setup as if sda is the boot drive.  But the windows (boot.ini) is setup for sdb to be the boot drive. Really confused here.   Have not seen a boot.ini entry like the 2nd in yours before. 
```

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /TUTag=LQ1PNK /Kernel=TUKernel.exe 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional (TuneUp Backup)" /noexecute=optin /fastdetect /TUTag=LQ1PNK-BAK 

```I love Clint Eastwood's line in Dirty Harry "You got to know your limitations". Over half of the in statements in grub.conf  are not a part of GRUB Legacy. (the version of GRUB used by Ubuntu prior to Karmic). Things like insmod, search, drivemap, ...   
Going to bail out, try to get up to speed on GRUB2 - maybe by time the Lucid lynx (aka Lounge Lizard) is released...

---

### Post by darrelsanchez23 on 2009-11-09
hello evrybody...

can i ask a manual on how to partition in ubuntu 6.10 because after installation i just selected the whole drive for the whole system and after restart it says error on 15GRUB loading..



tnx

---

### Post by Dr.Fuzzy on 2009-11-10
> **louieb said:**
> Just some observations.  
Looks like the MBR in both sda and sdb are setup to pass control to GRUB. Wonder how that happened. Also wonder what would boot if the boot order of the hard drives were flipped. - Just a guess that Windows would not boot - and don't know about Ubuntu. 

The GRUB menu looks like its setup as if sda is the boot drive.  But the windows (boot.ini) is setup for sdb to be the boot drive. Really confused here.   Have not seen a boot.ini entry like the 2nd in yours before. 
```

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /TUTag=LQ1PNK /Kernel=TUKernel.exe 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional (TuneUp Backup)" /noexecute=optin /fastdetect /TUTag=LQ1PNK-BAK 

```I love Clint Eastwood's line in Dirty Harry "You got to know your limitations". Over half of the in statements in grub.conf  are not a part of GRUB Legacy. (the version of GRUB used by Ubuntu prior to Karmic). Things like insmod, search, drivemap, ...   
Going to bail out, try to get up to speed on GRUB2 - maybe by time the Lucid lynx (aka Lounge Lizard) is released...

Interesting...Weird though cause all I did was a clean install with Karmic cd...Maybe I should give a second try installing it again. Will this overwrite my "bad" grub.conf ? The sda boot entry though will remain intact, any ideas how to clean this? Oh, and this time I might go for the 64-bit version, or no?.

---

### Post by louieb on 2009-11-12
> **Dr.Fuzzy said:**
> ...a second try installing ...Will this overwrite my "bad" grub.conf ?...

Don't think the grub.conf is bad. It works - even if is slower than you would like.  Just a guess that installing over will leave you with the same. 

Ubuntu Karmic is the 1st of the popular Linux distributions to use GRUB2 as its default boot loader. Because its so different from GRUB legacy and  so new - not a lot of knowledgeable people to help - not a lot of  detailed documentation out there yet. I expect that both will change for the better, in the next 6 months.

---

