---
title: "Dual Boot Win7 + Karmic - was working, but not anymore"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by acroporas on 2009-11-10
I installed windows 7.  Then I installed Karmic.  I was able to go back and forth between the two several times, and everything was wonderful.

Then I added a few additional hard drives, and Windows 7 disappeared from the list of OS choices in Grub.  I can still boot into Karmic fine.  But since Win7 is no longer a choice, I can not boot into Windows any-more.

How do I get Win7 added back to the list of choices.

---

### Post by mechro on 2009-11-10
Can you not just scroll down the boot menu?

---

### Post by acroporas on 2009-11-10
Yes, I could, at first that is what I was doing.  But then Windows 7 Disappeared from the list.  I can not arrow down to an option that is not there....

---

### Post by presence1960 on 2009-11-10
try opening a terminal and running ```
sudo update-grub
```

---

### Post by acroporas on 2009-11-10
Nope, that does not appear to have fixed it.

```
william@Pholidochromis:~$ sudo update-grub
[sudo] password for william: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

---

### Post by presence1960 on 2009-11-10
> **acroporas said:**
> Nope, that does not appear to have fixed it.

```
william@Pholidochromis:~$ sudo update-grub
[sudo] password for william: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

OK out comes the trobleshooting artillery. Do this:

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by raymondh on 2009-11-10
Quick question ...

"Then I added a few additional hard drives"  Is this for a RAID set-up and is so, which raid?

---

### Post by acroporas on 2009-11-10
No, no raid's involved.  Just some extra disks attached via sata ports on the MB.

---

### Post by acroporas on 2009-11-10
> **presence1960 said:**
> OK out comes the trobleshooting artillery. Do this:


```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda4 starts at sector 256204620.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e516e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   128,206,847   128,000,000   7 HPFS/NTFS
/dev/sda3         128,214,765   256,204,619   127,989,855   5 Extended
/dev/sda5         128,214,828   256,204,619   127,989,792  83 Linux
/dev/sda4         256,204,620   976,768,064   720,563,445   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0003aef1

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,953,520,064 1,953,520,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005a569

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000cb5ca

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63 1,953,520,064 1,953,520,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="042A96592A964796" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: UUID="FE5E98B15E9863E5" TYPE="ntfs" 
/dev/sda4: LABEL="Documents" UUID="B09E-E509" TYPE="vfat" 
/dev/sda5: UUID="4408d510-b975-4f94-badd-39811ae4b9ad" TYPE="ext4" 
/dev/sdb1: UUID="a11dd74b-02b5-42f1-ac52-ddd824ae12e3" TYPE="ext4" 
/dev/sdd1: LABEL="Television Shows" UUID="634605f8-a30b-4068-85d2-c3e44fc44f78" TYPE="ext4" 
/dev/sdc1: LABEL="Movies" UUID="bd0afda3-5b79-48ef-bf5d-58346899dd86" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
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
/dev/sdb1 on /home/william/Videos/More type ext4 (rw,noexec,nosuid,nodev)
/dev/sdd1 on /home/william/Videos/Television type ext4 (rw,noexec,nosuid,nodev)
/dev/sdc1 on /home/william/Videos/Movies type ext4 (rw,noexec,nosuid,nodev)
/dev/sda4 on /home/william/Documents type vfat (rw,noexec,nosuid,nodev,uid=1000)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/william/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=william)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 4408d510-b975-4f94-badd-39811ae4b9ad
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
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4408d510-b975-4f94-badd-39811ae4b9ad
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=4408d510-b975-4f94-badd-39811ae4b9ad ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4408d510-b975-4f94-badd-39811ae4b9ad
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=4408d510-b975-4f94-badd-39811ae4b9ad ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#

#<file system> 					<mount point>				<type>	<options>			<dump>	<pass>
proc         					/proc        				proc	defaults		        0       0
/dev/scd0     					/media/cdrom0				udf,iso9660 user,noauto,exec,utf8	0       0
UUID=4408d510-b975-4f94-badd-39811ae4b9ad 	/					ext4	errors=remount-ro 		0       1
UUID=a11dd74b-02b5-42f1-ac52-ddd824ae12e3	/home/william/Videos/More		ext4	users,auto			0	0 
UUID=634605f8-a30b-4068-85d2-c3e44fc44f78	/home/william/Videos/Television		ext4	users,auto			0	0 
UUID=bd0afda3-5b79-48ef-bf5d-58346899dd86	/home/william/Videos/Movies		ext4	users,auto			0	0 
UUID=B09E-E509 					/home/william/Documents			vfat	users,rw,uid=1000,auto		0	0

=================== sda5: Location of files loaded by Grub: ===================


  65.6GB: boot/grub/grub.cfg
  65.6GB: boot/initrd.img-2.6.31-14-generic
  65.6GB: boot/vmlinuz-2.6.31-14-generic
  65.6GB: initrd.img
  65.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  eb 63 90 d0 bc 00 7c 8e  c0 8e d8 be 00 7c bf 00  |.c....|......|..|
00000010  06 b9 00 02 fc f3 a4 50  68 1c 06 cb fb b9 04 00  |.......Ph.......|
00000020  bd be 07 80 7e 00 00 7c  0b 0f 85 0e 01 83 c5 10  |....~..|........|
00000030  e2 f1 cd 18 88 56 00 55  c6 46 11 05 c6 46 10 00  |.....V.U.F...F..|
00000040  b4 41 bb aa 55 cd 13 5d  72 0f 81 fb 55 aa 75 09  |.A..U..]r...U.u.|
00000050  f7 c1 01 00 74 03 fe 46  10 66 00 80 01 00 00 00  |....t..F.f......|
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
000001b0  cd 10 ac 3c 00 75 f4 c3  6e 51 0e 00 00 00 80 20  |...<.u..nQ..... |
000001c0  21 00 07 df 13 0c 00 08  00 00 00 20 03 00 00 df  |!.......... ....|
000001d0  14 0c 07 fe ff ff 00 28  03 00 00 20 a1 07 00 fe  |.......(... ....|
000001e0  ff ff 05 fe ff ff ed 66  a4 07 5f f8 a0 07 00 fe  |.......f.._.....|
000001f0  ff ff 0b fe ff ff 4c 5f  45 0f f5 ec f2 2a 55 aa  |......L_E....*U.|
00000200


```

---

### Post by acroporas on 2009-11-11
Bump

---

### Post by darkod on 2009-11-11
I have no great experience with grub2 (karmic would have installed grub2 not grub I guess) but can't you google around for ways to make manual entries?

From the file you posted it looks obvious Win7 boot is on sda1. Just add it as manual entry in grub2 and give it a shot.

---

### Post by oldfred on 2009-11-11
If the os prober is not finding the windows install, it sounds like you have a problem with the windows. You make have to run the fixmbr and other repair commands to fix the windows. I do not know how just adding hard drives could mess up windows. All your boot is on the one drive so boot order can not effect anything.

If you want to try a manual entry, copy this into your /etc/grub.d/40_custom file, double check that I have your UUID correct.

menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 042A96592A964796
    chainloader +1
}

---

### Post by Ghoulchaser on 2009-11-11
Try reversing your new hard drive installs . see if win7 shows back up in grub. It is possible when the new HD was added it is looking at the wrong drive now. My new main board is all SATA now . I had a similar problem on my old MB with IDE and added a second drive that was SATA.  The bios took the SATA as the boot drive .  This is just a possible scenario .  Think i corrected it by using the Vista cd to repair the Windows boot loader. It been a while.  I have another issue after upgrading to 9.10 where Grub lost Unbutu but Vista stays .  I will wait a few more months before trying 9.10 again. I just returned to 9.04.  I have Vista on one drive primary and Unbuntu on a 2nd drive primary.  I was currently using Easy BCD from Windows  worked great until 9.10 showed up , think grub2 is still flaky

---

### Post by acroporas on 2009-11-11
> **Ghoulchaser said:**
> Try reversing your new hard drive installs . see if win7 shows back up in grub. It is possible when the new HD was added it is looking at the wrong drive now. My new main board is all SATA now . I had a similar problem on my old MB with IDE and added a second drive that was SATA.  The bios took the SATA as the boot drive .  This is just a possible scenario .  Think i corrected it by using the Vista cd to repair the Windows boot loader. It been a while.  I have another issue after upgrading to 9.10 where Grub lost Unbutu but Vista stays .  I will wait a few more months before trying 9.10 again. I just returned to 9.04.  I have Vista on one drive primary and Unbuntu on a 2nd drive primary.  I was currently using Easy BCD from Windows  worked great until 9.10 showed up , think grub2 is still flaky

Yesterday, I tried pulling out all of the extra drives, and it still did not work.

---

### Post by cap10xb1s on 2009-11-11
I'm having similar trouble with a new installation of XP on 1 hard drive and a new karmic install on other. XP installation was ok but now I have installed KK on the other drive XP crashes when I select it in Grub. KK boots OK though and can see the windows volume.

I'm a bit of a newbie at all this so would be very grateful if someone could offer some guidance.

Machine is a Dell Dimension 9200 that previously ran XP in a raid configuration.

cap10xb1s

---

### Post by acroporas on 2009-11-11
> **oldfred said:**
> 
If you want to try a manual entry, copy this into your /etc/grub.d/40_custom file, double check that I have your UUID correct.

menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 042A96592A964796
    chainloader +1
}

The above fixed the problem.  After adding that code, I rebooted.  The first time windows 7 still did not show up.  Rebooted again and there it was.  Once Windows 7 was a choice again, windows booted up just fine.

Thanks

---

### Post by Mark Phelps on 2009-11-11
> **cap10xb1s said:**
> I'm having similar trouble with a new installation of XP on 1 hard drive and a new karmic install on other. XP installation was ok but now I have installed KK on the other drive XP crashes when I select it in Grub. KK boots OK though and can see the windows volume.

I'm a bit of a newbie at all this so would be very grateful if someone could offer some guidance.

Machine is a Dell Dimension 9200 that previously ran XP in a raid configuration.

cap10xb1s
This is a completely different problem -- having nothing to do with Windows 7.  You would do better to start your own thread instead of hijacking this one.

---

### Post by acroporas on 2009-11-11
> **cap10xb1s said:**
> I'm having similar trouble with a new installation of XP on 1 hard drive and a new karmic install on other. XP installation was ok but now I have installed KK on the other drive XP crashes when I select it in Grub. KK boots OK though and can see the windows volume.

I'm a bit of a newbie at all this so would be very grateful if someone could offer some guidance.

Machine is a Dell Dimension 9200 that previously ran XP in a raid configuration.

cap10xb1s

I would recommend that you start a new thread with your problems as doing so will probably get your question more attention/help and it does sound like a different problem than mine since my problem was about windows not showing up, and yours is about windows showing up and not working.

---

### Post by Mark Phelps on 2009-11-11
> **acroporas said:**
> The above fixed the problem.  After adding that code, I rebooted.  The first time windows 7 still did not show up.  Rebooted again and there it was.  Once Windows 7 was a choice again, windows booted up just fine.

Thanks

The choice is there now because you added it to a script that it runs.  However, you may want to rename the OS-prober script file, otherwise, if you ever do an update-grub, it will run that script.  Since you have the MS Windows entries you need in the custom script file, you no longer need the OS-prober file.

---

### Post by acroporas on 2009-11-11
> **Mark Phelps said:**
> The choice is there now because you added it to a script that it runs.  However, you may want to rename the OS-prober script file, otherwise, if you ever do an update-grub, it will run that script.  Since you have the MS Windows entries you need in the custom script file, you no longer need the OS-prober file.

um.....you completely lost me.  What do I need to do?  Or perhaps better phrased, how do I do what I need to do?

---

### Post by oldfred on 2009-11-11
If the os-prober finds the windows entry you will get two entries.

You can turn off the prober with a setting in grub:

/etc/default/grub
GRUB_DISABLE_OS_PROBER=true

grug update still will do all the other updates, just not find other operating systems.

---

