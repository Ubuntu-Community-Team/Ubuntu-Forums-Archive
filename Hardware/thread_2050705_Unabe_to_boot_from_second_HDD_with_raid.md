---
title: "Unabe to boot from second HDD with raid"
date: 2012-08-31
forum: Hardware
---

### Post by pki on 2012-08-31
Hi there.

Ubuntu 11.10. As i remember upgraded from earlier versions. 

A setup with 4 HDD's on serial ATA. sda & sdc raid 1 with a 60GB / partition. The remaining place of sda & sdc as a second raid 1. The other discs sdb & sdd as raid 1. The big space as lvm as /var.

The fird HDD is failing now (after 900 days), i removed the drive and tried to boot, no success. The system is stopping after BIOS, not resposible, no response to keyboard, num lock. No message from GRUB on screen, only the last BIOS line about "Verifiyng DMI pool data ...."

Selecting to boot from any of the three remaining discs gives the same hanging result. When i attach the faulty sda i can boot(selecting resue mode with degraded array), sda is already removed from the raid array. 

```
$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md4 : active raid1 sdd1[1]
      976759936 blocks [2/1] [_U]
      
md1 : active raid1 sdc2[1]
      8787456 blocks [2/1] [_U]
      
md2 : active raid1 sdc1[1]
      58596992 blocks [2/1] [_U]
      
md3 : active raid1 sdc3[1]
      909375296 blocks [2/1] [_U]

```


I tried update-grub to all discs, i also tried update-initramfs, no success, no change.



I also run bootinfoscript, here the result:
```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (mduuid/bf58706f7e97fc033cbfe349357e3f33)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (mduuid/bf58706f7e97fc033cbfe349357e3f33)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (mduuid/bf58706f7e97fc033cbfe349357e3f33)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (mduuid/bf58706f7e97fc033cbfe349357e3f33)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sda2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdc2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdc3: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdd1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

vg1-bigraid': __________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: nieznany typ systemu plików ''

md3: ___________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 

md2: ___________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

md1: ___________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

md4: ___________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000203804160 bytes
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 121601, w sumie sektorów: 1953523055
Jednostka = sektorów, czyli 1 * 512 = 512 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   117,194,174   117,194,112  fd Linux raid autodetect
/dev/sda2         117,194,175   134,769,284    17,575,110  fd Linux raid autodetect
/dev/sda3         134,769,285 1,953,520,064 1,818,750,780  fd Linux raid autodetect


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000203804160 bytes
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 121601, w sumie sektorów: 1953523055
Jednostka = sektorów, czyli 1 * 512 = 512 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002  fd Linux raid autodetect


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 121601, w sumie sektorów: 1953525168
Jednostka = sektorów, czyli 1 * 512 = 512 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63   117,194,174   117,194,112  fd Linux raid autodetect
/dev/sdc2         117,194,175   134,769,284    17,575,110  fd Linux raid autodetect
/dev/sdc3         134,769,285 1,953,520,064 1,818,750,780  fd Linux raid autodetect


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 121601, w sumie sektorów: 1953525168
Jednostka = sektorów, czyli 1 * 512 = 512 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                  63 1,953,520,064 1,953,520,002  fd Linux raid autodetect


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/vg1-bigraid f5e64a47-ac4e-4a3b-ad25-1983478ff000   reiserfs   
/dev/md1         656473c5-08b1-48af-8d11-9a1323e68578   swap       
/dev/md2         0ff1799e-d176-4f49-982c-2f7fe0f44d01   ext4       
/dev/md3         kR8TCj-mILr-t5zd-hNgD-PCKG-18Ix-xZ1KlM LVM2_member 
/dev/md4         txahnR-5Tc2-rXPC-5hc3-Xouq-8Xje-GKP7gP LVM2_member 
/dev/sda1        bf58706f-7e97-fc03-3cbf-e349357e3f33   linux_raid_member 
/dev/sda2        bc12c087-6c3d-26a8-5203-90b7396d847a   linux_raid_member 
/dev/sda3        2719bfb4-e763-35e9-273a-5f886224090c   linux_raid_member 
/dev/sdb1        2fe8ca55-3d20-bd68-464d-63993527a259   linux_raid_member 
/dev/sdc1        bf58706f-7e97-fc03-3cbf-e349357e3f33   linux_raid_member 
/dev/sdc2        bc12c087-6c3d-26a8-5203-90b7396d847a   linux_raid_member 
/dev/sdc3        2719bfb4-e763-35e9-273a-5f886224090c   linux_raid_member 
/dev/sdd1        2fe8ca55-3d20-bd68-464d-63993527a259   linux_raid_member 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
vg1-bigraid

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/vg1-bigraid /var                     reiserfs   (rw,noatime,notail)
/dev/md2         /                        ext4       (rw,errors=remount-ro)


=========================== md2/boot/grub/grub.cfg: ============================

--------------------------------------------------------------------------------
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

insmod raid
insmod mdraid09
insmod part_msdos
insmod part_msdos
insmod ext2
set root='(mduuid/bf58706f7e97fc033cbfe349357e3f33)'
search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod raid
  insmod mdraid09
  insmod part_msdos
  insmod part_msdos
  insmod ext2
  set root='(mduuid/bf58706f7e97fc033cbfe349357e3f33)'
  search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
  set locale_dir=($root)/boot/grub/locale
  set lang=pl_PL
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 3.0.0-16-server' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod raid
	insmod mdraid09
	insmod part_msdos
	insmod part_msdos
	insmod ext2
	set root='(mduuid/bf58706f7e97fc033cbfe349357e3f33)'
	search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
	linux	/boot/vmlinuz-3.0.0-16-server root=UUID=0ff1799e-d176-4f49-982c-2f7fe0f44d01 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-16-server
}
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 3.0.0-16-server (tryb ratunkowy)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod raid
	insmod mdraid09
	insmod part_msdos
	insmod part_msdos
	insmod ext2
	set root='(mduuid/bf58706f7e97fc033cbfe349357e3f33)'
	search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
	echo	'Wczytywanie systemu Linux 3.0.0-16-server...'
	linux	/boot/vmlinuz-3.0.0-16-server root=UUID=0ff1799e-d176-4f49-982c-2f7fe0f44d01 ro recovery nomodeset 
	echo	'Wczytywanie pocz&#261;tkowego dysku RAM...'
	initrd	/boot/initrd.img-3.0.0-16-server
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 2.6.38-13-server' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod raid
	insmod mdraid09
	insmod part_msdos
	insmod part_msdos
	insmod ext2
	set root='(mduuid/bf58706f7e97fc033cbfe349357e3f33)'
	search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
	linux	/boot/vmlinuz-2.6.38-13-server root=UUID=0ff1799e-d176-4f49-982c-2f7fe0f44d01 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-13-server
}
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 2.6.38-13-server (tryb ratunkowy)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod raid
	insmod mdraid09
	insmod part_msdos
	insmod part_msdos
	insmod ext2
	set root='(mduuid/bf58706f7e97fc033cbfe349357e3f33)'
	search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
	echo	'Wczytywanie systemu Linux 2.6.38-13-server...'
	linux	/boot/vmlinuz-2.6.38-13-server root=UUID=0ff1799e-d176-4f49-982c-2f7fe0f44d01 ro recovery nomodeset 
	echo	'Wczytywanie pocz&#261;tkowego dysku RAM...'
	initrd	/boot/initrd.img-2.6.38-13-server
}
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 2.6.32-38-server' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod raid
	insmod mdraid09
	insmod part_msdos
	insmod part_msdos
	insmod ext2
	set root='(mduuid/bf58706f7e97fc033cbfe349357e3f33)'
	search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
	linux	/boot/vmlinuz-2.6.32-38-server root=UUID=0ff1799e-d176-4f49-982c-2f7fe0f44d01 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-38-server
}
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 2.6.32-38-server (tryb ratunkowy)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod raid
	insmod mdraid09
	insmod part_msdos
	insmod part_msdos
	insmod ext2
	set root='(mduuid/bf58706f7e97fc033cbfe349357e3f33)'
	search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
	echo	'Wczytywanie systemu Linux 2.6.32-38-server...'
	linux	/boot/vmlinuz-2.6.32-38-server root=UUID=0ff1799e-d176-4f49-982c-2f7fe0f44d01 ro recovery nomodeset 
	echo	'Wczytywanie pocz&#261;tkowego dysku RAM...'
	initrd	/boot/initrd.img-2.6.32-38-server
}
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 2.6.31-22-server' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod raid
	insmod mdraid09
	insmod part_msdos
	insmod part_msdos
	insmod ext2
	set root='(mduuid/bf58706f7e97fc033cbfe349357e3f33)'
	search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
	linux	/boot/vmlinuz-2.6.31-22-server root=UUID=0ff1799e-d176-4f49-982c-2f7fe0f44d01 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.31-22-server
}
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 2.6.31-22-server (tryb ratunkowy)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod raid
	insmod mdraid09
	insmod part_msdos
	insmod part_msdos
	insmod ext2
	set root='(mduuid/bf58706f7e97fc033cbfe349357e3f33)'
	search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
	echo	'Wczytywanie systemu Linux 2.6.31-22-server...'
	linux	/boot/vmlinuz-2.6.31-22-server root=UUID=0ff1799e-d176-4f49-982c-2f7fe0f44d01 ro recovery nomodeset 
	echo	'Wczytywanie pocz&#261;tkowego dysku RAM...'
	initrd	/boot/initrd.img-2.6.31-22-server
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod raid
	insmod mdraid09
	insmod part_msdos
	insmod part_msdos
	insmod ext2
	set root='(mduuid/bf58706f7e97fc033cbfe349357e3f33)'
	search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod raid
	insmod mdraid09
	insmod part_msdos
	insmod part_msdos
	insmod ext2
	set root='(mduuid/bf58706f7e97fc033cbfe349357e3f33)'
	search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, za pomoc&#261; systemu Linux 3.0.0-16-server (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
	linux /boot/vmlinuz-3.0.0-16-server root=UUID=0ff1799e-d176-4f49-982c-2f7fe0f44d01 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-16-server
}
menuentry "Ubuntu, za pomoc&#261; systemu Linux 3.0.0-16-server (tryb ratunkowy) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
	linux /boot/vmlinuz-3.0.0-16-server root=UUID=0ff1799e-d176-4f49-982c-2f7fe0f44d01 ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-16-server
}
menuentry "Ubuntu, za pomoc&#261; systemu Linux 2.6.38-13-server (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
	linux /boot/vmlinuz-2.6.38-13-server root=UUID=0ff1799e-d176-4f49-982c-2f7fe0f44d01 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-13-server
}
menuentry "Ubuntu, za pomoc&#261; systemu Linux 2.6.38-13-server (tryb ratunkowy) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
	linux /boot/vmlinuz-2.6.38-13-server root=UUID=0ff1799e-d176-4f49-982c-2f7fe0f44d01 ro recovery nomodeset
	initrd /boot/initrd.img-2.6.38-13-server
}
menuentry "Ubuntu, za pomoc&#261; systemu Linux 2.6.32-38-server (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
	linux /boot/vmlinuz-2.6.32-38-server root=UUID=0ff1799e-d176-4f49-982c-2f7fe0f44d01 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.32-38-server
}
menuentry "Ubuntu, za pomoc&#261; systemu Linux 2.6.32-38-server (tryb ratunkowy) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
	linux /boot/vmlinuz-2.6.32-38-server root=UUID=0ff1799e-d176-4f49-982c-2f7fe0f44d01 ro recovery nomodeset
	initrd /boot/initrd.img-2.6.32-38-server
}
menuentry "Ubuntu, za pomoc&#261; systemu Linux 2.6.31-22-server (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
	linux /boot/vmlinuz-2.6.31-22-server root=UUID=0ff1799e-d176-4f49-982c-2f7fe0f44d01 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.31-22-server
}
menuentry "Ubuntu, za pomoc&#261; systemu Linux 2.6.31-22-server (tryb ratunkowy) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
	linux /boot/vmlinuz-2.6.31-22-server root=UUID=0ff1799e-d176-4f49-982c-2f7fe0f44d01 ro recovery nomodeset
	initrd /boot/initrd.img-2.6.31-22-server
}
menuentry "Ubuntu, za pomoc&#261; systemu Linux 3.0.0-16-server (on /dev/sdc1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
	linux /boot/vmlinuz-3.0.0-16-server root=UUID=0ff1799e-d176-4f49-982c-2f7fe0f44d01 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-16-server
}
menuentry "Ubuntu, za pomoc&#261; systemu Linux 3.0.0-16-server (tryb ratunkowy) (on /dev/sdc1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
	linux /boot/vmlinuz-3.0.0-16-server root=UUID=0ff1799e-d176-4f49-982c-2f7fe0f44d01 ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-16-server
}
menuentry "Ubuntu, za pomoc&#261; systemu Linux 2.6.38-13-server (on /dev/sdc1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
	linux /boot/vmlinuz-2.6.38-13-server root=UUID=0ff1799e-d176-4f49-982c-2f7fe0f44d01 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-13-server
}
menuentry "Ubuntu, za pomoc&#261; systemu Linux 2.6.38-13-server (tryb ratunkowy) (on /dev/sdc1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
	linux /boot/vmlinuz-2.6.38-13-server root=UUID=0ff1799e-d176-4f49-982c-2f7fe0f44d01 ro recovery nomodeset
	initrd /boot/initrd.img-2.6.38-13-server
}
menuentry "Ubuntu, za pomoc&#261; systemu Linux 2.6.32-38-server (on /dev/sdc1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
	linux /boot/vmlinuz-2.6.32-38-server root=UUID=0ff1799e-d176-4f49-982c-2f7fe0f44d01 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.32-38-server
}
menuentry "Ubuntu, za pomoc&#261; systemu Linux 2.6.32-38-server (tryb ratunkowy) (on /dev/sdc1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
	linux /boot/vmlinuz-2.6.32-38-server root=UUID=0ff1799e-d176-4f49-982c-2f7fe0f44d01 ro recovery nomodeset
	initrd /boot/initrd.img-2.6.32-38-server
}
menuentry "Ubuntu, za pomoc&#261; systemu Linux 2.6.31-22-server (on /dev/sdc1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
	linux /boot/vmlinuz-2.6.31-22-server root=UUID=0ff1799e-d176-4f49-982c-2f7fe0f44d01 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.31-22-server
}
menuentry "Ubuntu, za pomoc&#261; systemu Linux 2.6.31-22-server (tryb ratunkowy) (on /dev/sdc1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set=root 0ff1799e-d176-4f49-982c-2f7fe0f44d01
	linux /boot/vmlinuz-2.6.31-22-server root=UUID=0ff1799e-d176-4f49-982c-2f7fe0f44d01 ro recovery nomodeset
	initrd /boot/initrd.img-2.6.31-22-server
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

================================ md2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# / was on /dev/md2 during installation
UUID=0ff1799e-d176-4f49-982c-2f7fe0f44d01 /               ext4    errors=remount-ro 0       1

# /var was on /dev/md3 during installation
#UUID=84f3b94e-47fe-4fda-a0d4-d3063991d555 /home/piotr/test            reiserfs defaults        0       2

# swap was on /dev/md1 during installation
UUID=656473c5-08b1-48af-8d11-9a1323e68578 none            swap    sw              0       0
UUID=f5e64a47-ac4e-4a3b-ad25-1983478ff000 /var reiserfs defaults,noatime,notail

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


--------------------------------------------------------------------------------

==================== md2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  25.017742157 = 26.862596096   boot/grub/core.img                             1
  25.015731812 = 26.860437504   boot/grub/grub.cfg                             1
  15.421875000 = 16.559112192   boot/initrd.img-2.6.31-22-server               2
  15.408908844 = 16.545189888   boot/initrd.img-2.6.32-38-server               2
  15.474037170 = 16.615120896   boot/initrd.img-2.6.38-13-server               2
   4.121025085 = 4.424916992    boot/initrd.img-3.0.0-16-server                2
   6.073307037 = 6.521163776    boot/vmlinuz-2.6.31-22-server                  1
  12.097587585 = 12.989685760   boot/vmlinuz-2.6.32-38-server                  1
   0.992568970 = 1.065762816    boot/vmlinuz-2.6.38-13-server                  1
  14.844261169 = 15.938904064   boot/vmlinuz-3.0.0-16-server                   1
   4.121025085 = 4.424916992    initrd.img                                     2
  15.474037170 = 16.615120896   initrd.img.old                                 2
  14.844261169 = 15.938904064   vmlinuz                                        1
   0.992568970 = 1.065762816    vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on vg1-bigraid'



=============================== StdErr Messages: ===============================

xz: (stdin): Skompresowane dane s&#261; uszkodzone
xz: (stdin): Skompresowane dane s&#261; uszkodzone
xz: (stdin): Skompresowane dane s&#261; uszkodzone
xz: (stdin): Skompresowane dane s&#261; uszkodzone
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg1-bigraid': Nie ma takiego pliku ani katalogu
hexdump: /dev/mapper/vg1-bigraid': Nie ma takiego pliku ani katalogu
mdadm: /dev/md2 is already in use.
mdadm: /dev/md1 is already in use.
mdadm: /dev/md3 is already in use.
mdadm: /dev/md4 is already in use.



```


What can i do?

---

