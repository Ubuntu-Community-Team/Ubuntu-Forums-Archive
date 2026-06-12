---
title: "hiding partitions in Grub 2"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by dpg77 on 2009-11-09
anyone help on how to hide a partition in grub 2.

cannot find anywhere on how to set this up.
have a test system that has.
Win XP
Vista 
and had ubuntu 9.04 with grub 1

in the grub menu.lst 

had 

[B]This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows XP Professional
unhide        (hd0,1)
hide        (hd0,2)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista
unhide        (hd0,2)
hide        (hd0,1)
rootnoverify    (hd0,2)
savedefault
makeactive
chainloader    +1



[/B]This was so win xp didn't see vista and stuff up and vista didn't see win xp 
also so straight boot to both os not using linux boot loader then the stupid vista boot loader.

I cannot find any info on how to setup this in the new grub.cfg

or were to set this up.

---

### Post by phillw on 2009-11-09
All things Grub2 live at these areas ..

 [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)  and [http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743) and [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Regards,

Phill.

---

### Post by dpg77 on 2009-11-09
none of these post help all about change background pictures etc.
have not found any useful info on how to get it working. yet.
no man pages on grub 2.

Please help someone out there must have this working already.

---

### Post by Eddie Wilson on 2009-11-09
I'm also having problems hiding a backup drive from the grub 2 menu. I looked at all the info I can find but still can't come up with an answer on how to hide a partition or drive from the probing.

---

### Post by drs305 on 2009-11-09
@ dpg77
I am not familiar with hiding the drives so I don't think the following would apply to you.

@ Eddie Wilson,

If all you want to do is exclude a particular partition from showing up in the menu, one solution might be buried in  [Grub 2 Title Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602"). This post shows how you can change what is displayed *in the menu* by using scripting to hide or alter these items. Look at the 30_os-prober section.

It would take a bit of work to come up with the exact script entries, but it can be done. If I have time, I will try to experiment with it, but everyone else is encouraged to take up the challenge and present the script entry which would hide a specific partition.

Another option would be to change /usr/bin/os-prober to prevent it from looking at a particular partition.

---

### Post by Eddie Wilson on 2009-11-09
Thanks, I'll see what I can do.

---

### Post by Eddie Wilson on 2009-11-09
I dug into it some more and really couldn't find any info on not including a drive. I can change about everything else I need to but I'm stuck on this one. If anyone has any ideas then just jump right in.

Can't wait till we get a decent Startup-Manager.

---

### Post by dpg77 on 2009-11-10
Found the answer but will more than likely have problems when i update the kernel but at least i got it going now.

from my grub.cfg
which i manually editted.

Triple boot here i come.


BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    parttool (hd0,2) hidden-
    parttool (hd0,3) hidden+
    parttool (hd0,2) boot+
    search --no-floppy --fs-uuid --set ecb80573b8053d98
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    parttool (hd0,3) hidden-
    parttool (hd0,2) hidden+
    parttool (hd0,3) boot+
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 66900a65900a3bd5
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

---

### Post by Eddie Wilson on 2009-11-10
If I'm correct in my thinking the menu entries will still show up in your grub menu but I believe that's what you wanted. Now what I want to do is to prevent a backup hard drive from being detected and put into the menu list. The backup drive is not bootable so it shouldn't even be listed. Here we go again.

---

### Post by presence1960 on 2009-11-10
> **Eddie Wilson said:**
> If I'm correct in my thinking the menu entries will still show up in your grub menu but I believe that's what you wanted. Now what I want to do is to prevent a backup hard drive from being detected and put into the menu list. The backup drive is not bootable so it shouldn't even be listed. Here we go again.
Hmmmmm, I have 4 hard disks: IDE 160 GB, 250 GB SATA, 500 GB SATA and 80 GB external USB.

The 160 GB IDE has 9.10, 9.04, Masonux & XP on it. The 250 GB is data (not mounted as /home) and the 500 GB is backups & PING images. No disks/partitions other than the OSs on the 160 GB show up in the GRUB menu.

Something must have gone awry when you installed GRUB.

---

### Post by Eddie Wilson on 2009-11-10
That's what I'm thinking. I'm not sure what it could be tho. Anyway I'm going to install Grub2 1.97 final tonight and then see if it takes care of the problem. I had to reinstall grub after a grandson problem also so that may have disturbed something.

---

### Post by oldfred on 2009-11-10
dgp77 - you can move the entries from grub.cfg to /etc/grub.d/40_custom. If you turn off the executable flag on osprober then when you run update-grub2 only your manual entries will be added. 
Just remember to turn it on again if you ever want it to probe for other new operating systems automatically.

edit - the correct way to turn osprober off is in /etc/default/grub
GRUB_DISABLE_OS_PROBER=true

---

### Post by SilFox on 2012-03-30
After long time of struggling with various boot loaders and their configurations, mainly because there are almost NO informations about GRUB 2 and hidding partitions when you have TWO or more hard disks, finally today I managed to configure GRUB 2 to work as I wish. So, to maybe save someone's time, I'll write my example here.

I got two 250GB SATA HDDs, sda and sdb.
SDA is partitioned on this way:
sda1 - primary - 25GB - NTFS - [with XP64bit]
sda2- primary - 100GB - NTFS - [ Steam is here ;-) ]
sda3 - extended to/on logical partitions:
sda5 - SWAP - 4.2GB
sda6 - Ubuntu Natty (last usable Ubuntu linux) - 12GB - EXT3
sda7 - Empty, awaiting Xubuntu 12.04LTS - 12GB - EXT3
sda8 - Big Linux Partition, (NOT /home), For various Linux files, backups, ..

Installation was going on this order:
(Hard Disk 1, sda, connected at motherboard's IDE 1 connector).
XP was installed first, then was Ubuntu Natty, with GRUB 2 placed on MBR .
(Second disk, SDB was disconnected from motherboard IDE 2 connector.)
DVD-rom is connected at motherboard's IDE 4 connector.

After that, I disconnected SDA from motherboard, and connected SDB to IDE 2 connector/slot.
Reason for this is exactly the same I started to search and learn "How to hide/unhide partitions with GRUB 2", and that is:
I don't want XP see Win 7 boot and cfg files (and root partition) and vice-versa.

Then I installed Windows 7 x64, allowing that it takes entire disk.

Allowing Windows 7 to take entire EMPTY hard disk, produce that win 7 will create special "System reserved" partition.

If you have a pre-configured, or better to say pre-partitioned HDD, let's say one 50GB partition for OS Win 7, and rest (in this case) 200GB for files (Steam ;-) ;
windows 7 will not create that "System reserved" partition (100MB) {this is just an info from my experience}.

So, after Win 7 installation there was one "System reserved" 100MB partition, and rest is one C:/ partition 250GB (of course it is not 250, it's less, but this is only for purpose of this writting).
After  defragmentation (defragmenting NTFS partition before resizing is important), I shrinked it to 35GB that is C:\, and rest was formated as NTFS, which becomes E:\ (cca a little more than 200GB) {note: D:\ is DVD-rom, if for any reason you want, you can change that drive letters later in windows}
If you are curious why I do partitioning on that way:
I always do it that way, because then I can make backups of only OS partitions, so large program files/games will stay on E:, and backup with compression ratio 50% will result with acceptable backup size of 5 - 10GB, and that backup can be stored on that big NTFS partition; including Linux partition backups.

Next, I connected both hard disk, checked if BIOS is configured to boot from SDA (bios will not say SDA or SDB, so you have to learn what are names of disks in boot order)
Booting from SDA will display GRUB2 menu with Ubuntu and XP.
Do NOT choose XP! Windows 7 partitions will not be hidden from it!
Choose Ubuntu.

After booting I'm going to configure grub2 files as I need.
Note: I'm logged as root, so I will not use sudo command.
First, in terminal:
```
root@MSI:~# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-13-generic
Found initrd image: /boot/initrd.img-2.6.38-13-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found Windows NT/2000/XP on /dev/sda1
Found Windows 7 (loader) on /dev/sdb1
done
root@MSI:~#
```

Note that now Windows 7 OS is just added to GRUB 2 boot menu, NOTHING is hidden yet.
Also, the /etc/grub.d/20_memtest86+ is set to be non-executable, so that is the reason why there is no *memtest* in grub2 menu entry.

Then, edit file /etc/grub.d/40_custom with text editor.
In my example, it is this:
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "XP 64 (with hidden W7)" {
insmod ntfs
set root=(hd0,1)
parttool (hd0,1) hidden-
parttool (hd1,1) hidden+
parttool (hd1,2) hidden+
chainloader +1
parttool ${root} boot+
boot
}
menuentry "Win 7 (with hidden XP 64)" {
insmod ntfs
set root=(hd1,1)
parttool (hd1,1) hidden-
parttool (hd1,2) hidden-
parttool (hd0,1) hidden+
chainloader +1
parttool ${root} boot+
boot
}
# END #
```

Save file and then run "update-grub" again.

You will see EXACTLY the same output as it was before:
```
root@MSI:~# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-13-generic
Found initrd image: /boot/initrd.img-2.6.38-13-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found Windows NT/2000/XP on /dev/sda1
Found Windows 7 (loader) on /dev/sdb1
done
root@MSI:~#
```

In other words, there you will NOT see your new added menu entryes.
BUT, if you reboot now your computer, there WILL BE new menu entryes, just as I named them:

Ubuntu, with Linux 2.6.38-13-generic
Ubuntu, with Linux 2.6.38-13-generic (recovery mode)
Windows NT/2000/XP on /dev/sda1
Windows 7 (loader) on /dev/sdb1
XP 64 (with hidden W7)
Win 7 (with hidden XP 64)

SO, do not choose any of listed entryes:
*Windows NT/2000/XP on /dev/sda1* or *Windows 7 (loader) on /dev/sdb1*
cause, they will boot choosen system without any hideden partitions; instead, choose
*XP 64 (with hidden W7)* or* Win 7 (with hidden XP 64)*

Note: *"XP 64 (with hidden W7)*" **or*** "Win 7 (with hidden XP 64)"* are only the OS menu entry names that **I** set for them, you can set names in that file "40_custom" as you wish.

Having grub 2 configuration like this, when I boot to XP, I can't see Windows 7 "system reserved" partition, nor Windows 7 C:\ partition, BUT I CAN see Windows 7 E:\ partition where are valuable files created, downloaded or stored when I was in Windows 7;
When booted ino Win 7, it can't see XP's C:\ partition, but it can see E:\ partition.
Of course those "E:\" partitions, if for some reason needed, can also be configured to be hidden.

As you can see from my mentioning Steam, only reason why I still have windows is for gaming.

I hope this will help someone.

BTW, here is grub.cfg file:
```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root fa90a1fd-6c68-402f-75cf-04fdd5995493
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root fa90a1fd-6c68-402f-75cf-04fdd5995493
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root fa90a1fd-6c68-402f-75cf-04fdd5995493
	linux	/boot/vmlinuz-2.6.38-13-generic root=UUID=fa90a1fd-6c68-402f-75cf-04fdd5995493 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-13-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root fa90a1fd-6c68-402f-75cf-04fdd5995493
	echo	'Loading Linux 2.6.38-13-generic ...'
	linux	/boot/vmlinuz-2.6.38-13-generic root=UUID=fa90a1fd-6c68-402f-75cf-04fdd5995493 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-13-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2entryies
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root fa90a1fd-6c68-402f-75cf-04fdd5995493
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=fa90a1fd-6c68-402f-75cf-04fdd5995493 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root fa90a1fd-6c68-402f-75cf-04fdd5995493
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=fa90a1fd-6c68-402f-75cf-04fdd5995493 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 641088131087E9FE
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 5C029AB7029A961C
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "XP 64 (with hidden W7)" {
insmod ntfs
set root=(hd0,1)
parttool (hd0,1) hidden-
parttool (hd1,1) hidden+
parttool (hd1,2) hidden+
chainloader +1
parttool ${root} boot+
boot
}
menuentry "Win 7 (with hidden XP 64)" {
insmod ntfs
set root=(hd1,1)
parttool (hd1,1) hidden-
parttool (hd1,2) hidden-
parttool (hd0,1) hidden+
chainloader +1
parttool ${root} boot+
boot
}
# END #
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
```0

---

### Post by oldos2er on 2012-03-30
Closed, necromancy.

---

