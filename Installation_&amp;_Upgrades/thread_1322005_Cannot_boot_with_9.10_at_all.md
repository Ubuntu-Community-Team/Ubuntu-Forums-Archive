---
title: "Cannot boot with 9.10 at all"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by ed-koala on 2009-11-10
I'm having serious trouble getting 9.10 to boot after upgrading from 9.04.  No matter what I do, it falls to busybox shell prompt (ie <initramfs> or something like that)

I am currently booting from the live CD ... here is what gparted shows about my hard drives:

/dev/mapper/nvidia_eajcdfjc (931.52 GiB)
	unallocated	unallocated

/dev/sda
	/dev/sda1	extended	465.76 GiB
	    /dev/sda5	ext3		 46.67 GiB
	    /dev/sda7	ext3		372.52 GiB
	    /dev/sda6	linux-swap	 46.57 GiB

/dev/sdb
	/dev/sdb1	ext3		465.76 GiB

/dev/sdc
	/dev/sdc1	fat32		931.51 GiB

The sda5, sda7, and sdb1 drives all show a yellow ! in a triangle, so something is up there but I don't know what.

The /dev/mapper stuff is new, wasn't in 9.04 at all, so I've no idea what is going on with it (obviously, its the raid setup of my 2 identical hard drives, but what's it doing there as unallocated)?

In 9.04, everything is on sda, the sdb drive is simply storage space, and the mybook drive does NOT have windows, it is also storage, just in windows format.  The ONLY OS on the system should be 9.10 at this time.

Changing the root=UUID blah blah to root=/dev/sda (or sda1) as suggested elsewhere has no effect.  It still won't boot up.

Trying to boot to another kernal ... no effect, still same problem.

What can I edit/fix/do to make this PC boot?

---

### Post by SlugSlug on 2009-11-10
> **ed-koala said:**
> I'm having serious trouble getting 9.10 to boot after upgrading from 9.04.  No matter what I do, it falls to busybox shell prompt (ie <initramfs> or something like that)


what does it say when it drops you to this

---

### Post by JugglinPhil on 2009-11-10
So does your system not start at all or is it only your graphical interface that does not start?

 If you've got a terminal that asks for your username then login and run 'startx', that should start the GUI. If that doesn't work it might already be running and you're only on the wrong terminal, try ctrl+alt+7 to switch to tty7 which is the graphical one.

If that's not your problem you might consider backing everything that's on your computer up to some external drive (copy n paste from the livecd) and reinstall, choosing 'Use all available space for Ubuntu' (or something along those lines), you shouldn't have all that partition mess then.

---

### Post by ed-koala on 2009-11-10
I get no messages, just a prompt ... when I hit enter, I see the <initramsf> tag (like its the directory).  I did see something similar to the screen in this post tho - [http://ubuntuforums.org/showthread.php?t=1319976]("http://ubuntuforums.org/showthread.php?t=1319976")

I just want to be able to start my PC

---

### Post by SlugSlug on 2009-11-10
do you not have any text above the prompt?

---

### Post by ed-koala on 2009-11-10
I get absolutely no messages, just a black screen with a flashing cursor, and only after hitting enter do i see the <initramfs> before the prompt, nothing else shows up.

No, the PC isn't booting into ubuntu at all, the drop out to prompt is very fast, so obviously the  OS or something isn't being found.

Any ideas what to do?  9.04 worked fine, and this was a simple upgrade, no changes to my partitioning, nothing strange about my setup at all, very basic packages.

I tried doing a fresh install also, another time, and couldn't even get grub to work from that.  At least now I can get a grub menu, but nothing else.

---

### Post by SlugSlug on 2009-11-10
try go through the tty's see if you can see any error (ctrl + alt + F7) (ctrl + alt + F8) etc..

---

### Post by ed-koala on 2009-11-10
Tried the different tty's ... all I get is a flashing cursor top left of screen, no messages, nothing.

Noticed on boot I'm getting the white ubuntu logo for about 10 sec before it drops to the cursor.

Any ideas?  I'll never be able to upgrade unless I figure out what's wrong here.  And I can't help but wonder about that /dev/mapper partition ... where did it come from on an upgrade with no partitioning????  Perhaps deleting it?

---

### Post by SlugSlug on 2009-11-10
noot sure, I would go deleting it..

you could try boot live mount / and check out /var/log/messages 

but for all the mesin about may be easer to back up and reinstall..

---

### Post by ed-koala on 2009-11-10
This is my 3rd try at getting 9.10 on this PC ... the last upgrade, same thing.  A fresh install from the live CD won't even load grub, gives an error 17.  I'm out of ideas ... I'd like to know just what the system is trying, and failing, to do.

Got any ideas on how to do a fresh install that won't kill grub?  My important stuff is on the storage drives, and I won't format those.

---

### Post by SlugSlug on 2009-11-10
humm you could check out BIOS and make sure your Primary Master drive is set as default boot I had a similar prob once due to one of my other drives set as first in the hard drive boot sequence, 

but that being said I have gone back to 9.04 due to bugs...

---

### Post by dhavalbbhatt on 2009-11-10
Try using the alternate CD to install Ubuntu, as against desktop installation CD.

Try that and post the results.

---

### Post by ed-koala on 2009-11-10
getting amd64 alt CD now, will burn that, try a fresh install, and post results :)

---

### Post by ed-koala on 2009-11-10
Ok, took awhile with d/l and burning, but here are the results:

First fresh install from Alt CD - Selecting "activete raid" and using entire disk for install results in the install hanging and unable to get past installing grub (or lilo, neither work).  The only way to get install to complete is to continue without boot loader, and then of course the system won't boot - Grub error 2.

Second attempt:

Selected no to activate raid, used entire first 500gb HD.  All goes well this time, and grub loads/saves and install completes.  Upon booting the PC, grub gives disk not found error, the ubuntu logo appears (for 10-15 sec), then I get this message ...

Gave up waiting for root device.  Common problems:
   - boot args (cat /proc/cmdline)
     - check rootdelay= (did the system wait long enough?)
     - check root= (did the system wait for the right device?)
   - missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/Raptor-root does not exist. Dropping to shell!

So, still cannot boot up.  What do I do now?

---

### Post by ed-koala on 2009-11-10
Some new info ... pasting results of boot script here:

============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       lvm2pv
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'lvm2pv'

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0fbe8c40

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,270,049   976,269,987  8e Linux LVM
/dev/sda2         976,270,050   976,768,064       498,015   5 Extended
/dev/sda5         976,270,113   976,768,064       497,952  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sdb1     ?   471,859,656 2,619,343,759 2,147,484,104  c8 Unknown
/dev/sdb2     ?             0   536,215,551   536,215,552   4 FAT16 <32M
/dev/sdb3     ?   505,414,088 2,652,898,191 2,147,484,104  c8 Unknown
/dev/sdb4     ?             0   536,215,551   536,215,552   4 FAT16 <32M

/dev/sdb1 ends after the last sector of /dev/sdb
/dev/sdb1 overlaps with /dev/sdb2
/dev/sdb1 overlaps with /dev/sdb3
/dev/sdb1 overlaps with /dev/sdb4
/dev/sdb2 overlaps with /dev/sdb3
/dev/sdb3 ends after the last sector of /dev/sdb
/dev/sdb3 overlaps with /dev/sdb4

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe8900690

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="yHOvrZ-sqLf-kq9z-cwXU-e6gi-67nj-m0mXXi" TYPE="lvm2pv" 
/dev/sda5: UUID="d652423f-470a-45be-a3af-e766644ef2ba" TYPE="ext2" 
/dev/sdc1: LABEL="My Book" UUID="A910-D18E" TYPE="vfat" 

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
/dev/sr1 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc1 on /media/My Book type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


============================= sda5/grub/grub.cfg: =============================

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
insmod lvm
insmod ext2
set root=(Raptor-root)
search --no-floppy --fs-uuid --set ea8f3037-ed35-4400-9667-e8b73efa4b7f
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
	search --no-floppy --fs-uuid --set d652423f-470a-45be-a3af-e766644ef2ba
	linux	/vmlinuz-2.6.31-14-generic root=/dev/mapper/Raptor-root ro   quiet splash
	initrd	/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set d652423f-470a-45be-a3af-e766644ef2ba
	linux	/vmlinuz-2.6.31-14-generic root=/dev/mapper/Raptor-root ro single 
	initrd	/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/memtest86+.bin console=ttyS0,115200n8
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

=================== sda5: Location of files loaded by Grub: ===================


 500.0GB: grub/grub.cfg
 499.8GB: initrd.img-2.6.31-14-generic
 499.8GB: vmlinuz-2.6.31-14-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  eb 63 90 d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |.c....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 03 02  |...It.8,t.......|
00000040  ff 00 00 20 01 00 00 00  00 02 fa 90 90 f6 c2 80  |... ............|
00000050  75 02 b2 80 ea 59 7c 00  00 31 00 80 01 00 00 00  |u....Y|..1......|
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
000001b0  cd 10 ac 3c 00 75 f4 c3  40 8c be 0f 00 00 80 01  |...<.u..@.......|
000001c0  01 00 8e fe ff ff 3f 00  00 00 a3 b2 30 3a 00 fe  |......?.....0:..|
000001d0  ff ff 05 fe ff ff e2 b2  30 3a 5f 99 07 00 00 00  |........0:_.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1


Unknown BootLoader  on sdb2


Unknown BootLoader  on sdb3


Unknown BootLoader  on sdb4



=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg sdh 
=============================== StdErr Messages: ===============================

hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb4: No such file or directory
hexdump: /dev/sdb4: No such file or directory

---

### Post by dhavalbbhatt on 2009-11-10
All right, I can't read through your post - not in it's entirety anyways - so let me ask you - how many Ubuntu/Linux partitions do you have? And if you have multiple, then do you have a GRUB conflict - meaning the older versions of Ubuntu were on GRUB 1.5 or GRUB 0.97. The GRUB in Karmic is GRUB 1.97 beta.

---

### Post by ed-koala on 2009-11-10
No older versions. Clean installs, no matter what I do I cannot get a boot up, tho depending on how I install I get different types of problems.

I've tried some other installations since this posting, so perhaps I should start a new thread, but I'm at a loss how to proceed now.  I unplugged my windows formatted external drive in case that was doing something with grub.

Currently I last tried a clean install from the standard install CD (which is verified good).  Raid setup - 2 500gb HDs, I let ubuntu use the entire partition, ext4 format.  Bootup gives Grub error 2, which is 2 : "Selected disk doesn't exist"

This error is returned if the device part of a device- or full filename refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system

Ok, fine, so how do I fix it?  What file do I edit?

---

### Post by Joebubba360 on 2009-11-10
Same problem.

After trying to load 9.10 on two different brands of laptops (Dell 630 and a Lenovo T41) using the wubi loader (linux on windows) on a second partition. Both machines ended up with the Ubuntu partition being unbootable, dropping to the grub busybox command line. We tried an upgrade from 9.04 to 9.10 first, then a clean install. Both times, the system would not boot. After looking at the system with a live CD, there was no grub loader installed on either system. Thinking that this must be a bad CD, we downloaded fresh images using torrents instead of .iso's from the site. Same results. Tried fresh installs on both machines again. Same results. Tried downloading the alternate live cd and installing...same issues...some worse.

After reading through countless threads discussing boot issues with the grub2 loader, (as well as countless other parallel problems) looking for a solution, it became obvious that there are serious internal system level issues yet to be resolved before 9.10 is ready for prime time. Some of the  'solutions' offered by the most honorable experts on the forum involved major surgery to various configuration files, reloading the grub2 loader manually using a live cd, etc. Their expertise is most commendable, and I have the utmost regard for them all. However, let me point out one tiny little flaw in that approach...(other than none of them worked, or if they did, only until the following reboot)...

The assumption of all such 'fixes' is based on the concept that a repair of a broken system software element is needed..._this is an incorrect assumption in this case_. The code is bad. It didn't work correctly to begin with. The code needs to be rewritten so that it works correctly FIRST. Then, if and when errors happen, its possible to correct a problem that is fixable. Trying to apply such 'fixes' to bad system code is unpredictable and unreliable at best. The developers need to go back and fix the code, then release a 9.10a install disk. 

I've gone back to 9.04.

---

### Post by ed-koala on 2009-11-10
We don't seem to have much choice other than to stick to 9.04.  I'm hoping someone can explain what is going on behind the scenes, as it were, when the system goes from grub to logo to busybody.  Knowing exactly what line of code is going wonky would be nice.

---

### Post by dhavalbbhatt on 2009-11-10
> **ed-koala said:**
> We don't seem to have much choice other than to stick to 9.04.  I'm hoping someone can explain what is going on behind the scenes, as it were, when the system goes from grub to logo to busybody.  Knowing exactly what line of code is going wonky would be nice.

Do you have raid active as part of your BIOS? Try to disable that and see if that works. I know I am throwing out solutions, but it seems like you guys have given up on Karmic. It's working great for me, so I hate for you guys to give up.

---

### Post by atoztoa on 2009-11-11
For initramfs> prompt, try changing the mapping in /etc/fstab from UUID to /dev/sda... (you will need to mount the partition separately after booting from Live CD.

I came across lots of problems during my install of Karmic... read it fully and you will get some insight...

[http://www.atoztoa.com/2009/11/booting-ubuntu-910-part-1-downfall.html](http://www.atoztoa.com/2009/11/booting-ubuntu-910-part-1-downfall.html)

_ATOzTOA
[www.atoztoa.com](www.atoztoa.com)

---

### Post by ed-koala on 2009-11-11
I don't see anything about raid in my Bios, but it obviously is set up as 9.10 "sees" it ... tho it can't handle it.  I'm definately NOT going to open my case and start fooling with hardware, that shouldn't be necessary.

I'm truly afraid to install or upgrade again.  Its hours of work recovering every time it fails, and it has failed every time despite my best efforts.

My problem seems to be "seeing" the installation.  When I reinstalled 9.04, the partitioner told me no other operating systems were installed, even though I had just got done installing 9.10 ... so where did it go?

Any ideas how I can install, or try to install, 9.10 so as not to have to spend hours reinstalling 9.04 when it goes splat?

Developers REALLY need to make this issue a priority. It'll kill Ubuntu for new users ... I feel comfy with Linux and its driving me mad.

---

### Post by SlugSlug on 2009-11-11
I did mention this before, but did you look into your hard drive boot priority in bios?

---

### Post by ed-koala on 2009-11-11
Yes, hard drive boot priority is set correctly in bios.

---

### Post by ed-koala on 2009-11-11
Ok, did some checking, and did a grub2 check.

NO bios settings show up saying RAID.
Boot order is CD, 1st HD

I installed Grub2 to TEST it ... it worked after chenging root to uuid as the grub2 instuctional page says.  So, I suppose I'm ready to replace brub with grub2 ... I'll do that, so I now know Grub2 is installed and working.

Question - Will it make any difference? I might try a side by side install to see what happens, that way I won't lose 9.04 or its settings, correct?

---

### Post by ed-koala on 2009-11-11
More info, and some more strangeness ...

Decided to try a side by side install with 9.04, as to minimize recovery if/when things went bad ... but, there's a serious problem.

(.10 installer says there are no other operating systems on my PC.  Clearly, the installer is faulty, since I'm booting into 9.04 now, it's there but the installer can't see it.  It wants to install to my windows fat32 formatted data drive (it doesn't have windows, just the fat32 format in case I want to take my data to a windows PC).

What the hell is going on with 9.10 installer????  Unplugging my fat32 drive simply results in the installer wanting to use the entire raid array for 9.10, it still can't "see" 9.04.

Why?  I'm giving up for awhile.  9.10 simply will not load / boot no matter what I do, and it seems it doesn't install with 9.04. The OS simply "disappears".  If anyone knows how to fix this, send me a message.  Once 9.04 gets too old, barring a significant change to ubuntu, I'll be forced back to windows.

Wish I could talk to whomever came up with the 9.10 installer, they really screwed up this time.

---

### Post by parlaan on 2009-11-11
Just so you know, I had the exact same thing..  Went to the intramfs boot.  This was after an upgrade.  I tried mounting my drives manually and found no files.

I was wondering.  Do you have 2 hard drives ?  I do and they are about the same size.

I did download the CD for a clean install, and do have the option of changing my drives to raid drives.  I suspected that the upgrade thought I had a raid, and when it tried rebooting, it looked for them and there wasn't any there.

Anyway, with a clean install, the auto installer saw my raid, and I was able to partition it, and install on it.

I'm not sure if is working right yet, because when I installed the NV proprietary drivers, it wouldn't let me write to the xorg.conf..


I'll play with it again tomorrow.  

I guess my point being, Since 9.04 didn't have an option to install raid (Desktop version).  And now 9.10 does, There may be a problem there, if it sees 2 drives, it thinks they should be raid, whether they are or not.

---

### Post by ed-koala on 2009-11-12
I honestly wish I knew what is going on.  BIOS has absolutely NO RAID settings, I checked every entry, every option, and the word RAID appears nowhere.  Using the alt CD and not enabling RAID doesn't help, still won't boot.

This can't be an uncommon problem.  When, if ever, can we expect a fix, and how will we know when it gets fixed?

---

### Post by arobson on 2009-11-12
I had a similar problem after upgrading to 9.10 - after grub loaded I would get the white logo for a while then straight to this:

(initramfs)

What worked for me was to go into the /boot/grub/menu.lst file from a live rescue cd (which I had prior experience changing after grub had failed to "see" my hard drive before) and make sure all the root instances pointed to the right place, i.e.

root          (hd0,0)

instead of:

root           dc198596-ce49-444c-b66b-c86d17d3e93a

And under the kernel line:

kernel        /boot/vmlinuz-2.6.28-16-generic root=/dev/sda1 ro quiet splash

instead of:

kernel        /boot/vmlinuz-2.6.28-16-generic root=dc198596-ce49-444c-b66b-c86d17d3e93a ro quiet splash

Take a look at your menu.lst file and see what it looks like.

---

### Post by ed-koala on 2009-11-12
I may try that, you'd think the upgrade option would work better, but it doesn't.  I'm very frustrated with 9.10, and *IF* I even decide to try, it'll be the LAST time until this issue is fixed ... don't know how I'll ever know if it gets fixed tho.

---

### Post by ed-koala on 2009-11-12
Ok, went back and tried the upgrade route again.  Fell to <initramfs> prompt as expected.  Booted to live cd to edit /boot/grub/menu.lst ... there is no such file.

Now what?

---

### Post by atoztoa on 2009-11-12
> **ed-koala said:**
> Ok, went back and tried the upgrade route again.  Fell to <initramfs> prompt as expected.  Booted to live cd to edit /boot/grub/menu.lst ... there is no such file.

Now what?

You will have to mount the partition where you installed Ubuntu.

If you have separate partition (/dev/sda5) for /boot, then 

```
sudo mount /dev/sda5 /mnt/something
sudo vi /mnt/something/grub/menu.lst
```Else mount the root partition (example /dev/sda1)...

```
sudo mount /dev/sda1 /mnt/something
sudo vi /mnt/something/boot/grub/menu.lst
```*Read this post if you get time... [http://www.atoztoa.com/2009/11/booting-ubuntu-910-part-1-downfall.html]("http://www.atoztoa.com/2009/11/booting-ubuntu-910-part-1-downfall.html")*

_ATOzTOA
[www.atoztoa.com]("http://www.atoztoa.com")

---

### Post by matthewboh on 2009-11-12
Most recent update to update to Firefox with the xulrunner just did the exact same thing to my PC - I want to try some of these and follow this thread

---

### Post by ed-koala on 2009-11-12
sudo mount /dev/sda1 /mnt/something ... mount point /mnt/something does not exist

Now what?

---

### Post by Sylverius on 2009-11-12
It's telling you the target mount directory doesn't exist.  You'll have to create it:

sudo mkdir /mnt/something

Jim

---

### Post by arobson on 2009-11-12
You have to make the directory that you are going to mount your drive to:

```
sudo mkdir /mnt/something
```

Then you can do:

```
sudo mount /dev/sda* /mnt/something
```

'something' can be whatever you want, naturally - its just a folder you are using to store the drive. What you put for '/dev/sda*' will depend on what the partition containing your /boot folder is called. In my case, my /boot folder was in my / partition and was called sda1, thus I had:

```
sudo mount /dev/sda1 /mnt/something
```

Once you have mounted /boot you want to first make a backup of menu.lst:

```
sudo cp /mnt/something/boot/grub/menu.lst /mnt/something/boot/grub/menu.lst.backup
```

Then go and edit the menu.lst file with vim, nano, etc.

---

### Post by parlaan on 2009-11-12
What I found, was that 9.10 only saw my "Fakeraid".  I was able to boot, with limitations, if I turned my fakeraid on in Bios.  It would never give me an option to install 9.10 on say one of my drives.  I never saw the /dev/sd's.

I tried turning off the Fakeraid in bios and disabling one of the hard drives, and it still only saw fake raid.

---

### Post by ed-koala on 2009-11-12
Ok, I'll make the directory, then mount it, then edit menu.lst

What exactly am I going to put in menu.lst that will make my PC boot?

Changing BIOS isn't an option, there is NO RAID anywhere, I checked every entry, every option.  There is nothing to turn on or off.

---

### Post by ed-koala on 2009-11-12
Ok, problem.  Trying to mount /dev/sda1 gives this:

```
mount: special device /dev/sda1 does not exist
```

Gparted shows /dev/mapper/nvidia_eajcdfjc (unallocated)
              /dev/sda1   ext3    boot  (has a yellow ! in a triangle)
              /dev/sda2   extended
              /dev/sda5   swap

Now what do I do?

---

### Post by parlaan on 2009-11-12
> **ed-koala said:**
> Ok, problem.  Trying to mount /dev/sda1 gives this:

```
mount: special device /dev/sda1 does not exist
```

Gparted shows /dev/mapper/nvidia_eajcdfjc (unallocated)
              /dev/sda1   ext3    boot  (has a yellow ! in a triangle)
              /dev/sda2   extended
              /dev/sda5   swap

Now what do I do?

/dev/mapper/nvidia_eajcdfjc  is Raid.  So, it is what I experienced.  9.10 installer is trying to install on a Raid, when you don't want it to.

It won't work unless you turn it on in your Bios.  You said you don't have the option in your Bios.

You might check your bios setup -- goto Drives and goto each Sata Drive individually.  You may find a raid option there.  I'm guessing you possibly have a Dell XPS system?

I don't know how to get the install to recognize your Sata drive as Sata, instead of raid.  But that is the problem as I see it.

Any Help ?

---

### Post by ed-koala on 2009-11-12
I've been through my BIOS several times, every entry, every option ... no RAID mentioned anywhere, so it must be a physical connection between the drives or some other hardware configuration.  I'm assuming pulling one hard drive would work, though it's an extreme solution for something that should work out of the box.  I do not want to pull a drive.

Its hard to believe 9.10 got released with this bug ... RAID isn't exactly uncommon.  I've reinstalled 9.04 now, since no one has come up with any explanation of what's going on much less a fix.

I still hope someone can come up with an answer for me.  9.04 works fine on a regular install.  Too bad 9.10 doesn't, on ANY type of install.

If anyone has any ideas, I'm all ears.  I'd love to get a developer in front of my PC and have them try to install 9.10 so they can see just how badly they screwed up this time.

All that said, I'm wondering why that in gparted under 9.04 my sda1 is ok, but after upgrading to 9.10 gparted shows a ! in a triangle for sda1.  Something went wrong, obviously, but I have no clue what.

---

### Post by atoztoa on 2009-11-12
If there is anything about UUID in menu.lst... paste it here...

You can try LILO....

_ATOzTOA
[www.atoztoa.com]("http://www.atoztoa.com")

---

### Post by jakswa on 2009-11-13
"'Fakeraids' are supported out-of-the-box on the Ubuntu 9.10 Desktop CD, and will be detected and activated by dmraid on boot. Ubiquity will offer to install on the RAID array, and not on the RAID members."
[https://bugs.launchpad.net/ubuntu-release-notes/+bug/462631](https://bugs.launchpad.net/ubuntu-release-notes/+bug/462631)

By 'supported out-of-the-box', I think they mean to say "we will bork your system all to hell *trying* to support fakeraid."

---

### Post by ed-koala on 2009-11-13
Ok, I just want to be clear ... I read that link about fakeraid and the nodmraid option.

So, perhaps trying to install by choosing F6 and using that would work?  After 10 tries, you might understand how much I hate going through hosing my PC AGAIN and having to reinstall 9.04 and all my software.

At this point I want to KNOW it'll work, not guess ... and why won't upgrade work?  All the HD stuff is already set up, all it needs is the new packages, yet it destroys my sda1 ... partitioner shows it with a yellow ! triangle.  How do I find out what happened to my boot partition after the upgrade, and what can I do about it?

Another issue yet to get an answer ... RAID and BIOS ... there is NO RAID in my BIOS, period.  I've looked, no option exists to change it or enable/disable it.  Is it a hardware connection between drives?  At this point I'll open the case and fiddle ***IF*** it'll work.  But I'm not cracking my PC open until I know what is going on with RAID.

I don't mean to insult anyone, because I don't know what everyone's expertise level is that has responded, but I truely wish a developer or someone who created this installer/partitioner would look at this thread and weigh in.

Give me some options ... how can I upgrade to 9.10 and get my PC to boot? Surely I'm not the only person with RAID that isn't in the BIOS?

I'm worried this may be the last version I'll EVER be able to use, since this issue will probably appear in the next version, and the next, etc

---

### Post by ed-koala on 2009-11-13
Finally!!!  Ok, hopefully everyone who needs this will find it.

AMD64 home built system with 8gb RAM and 2 Samsung 500gb HDs in serial RAID config.

Download and burn the alternate install CD for AMD64

Upon booting disk, select F6, arrow down to nodmraid, hit enter to put an x by it, then hit escape to get back to the install menu

Choose install Ubuntu

When you get to the point it asks if you want to activate RAID, select **NO**

I used guided partition - use entire disk option
[INDENT]It automatically set up / as ext4 and swap for me[/INDENT]

Everything should proceed smoothly and automatically from here, with only normal things like system time or user name to fool with (if not already done).  If you get any strange screen like asking what to do next, or where to install grub, your setup isn't going like mine, sorry this might not help you.

Reboot system, removing the install disk

You should now boot up to the login screen (if you are like me). Congrats!

Something so very simple, made so very damn hard for some reason.

---

