---
title: "Radeon graphics bootup issue ( possibly monitor EDID related )"
date: 2015-03-15
forum: Hardware
---

### Post by neu2buntu on 2015-03-15
Hi guys, I have had this bootup issue since I 1st installed ubuntu 12.04 on my desktop computer, where I get a totally messed up screen right from the very start of boot , this makes accessing the bios almost impossible.
I upgraded to 14.04 and still the issue is the same. I get very random system freeze ups which could be linked I guess. ( see screenshots for pictures during boot )

* Right after logging in my screen works perfectly.

* My monitor is a Samsung S22C150 just using it through the VGA cable.

* I have tried with the proprietary FGLRX drivers as well as the open source ones, still the same results.

* Re- Flashing the bios is the only way that I can access the bios settings without having a glitched out screen.

* My true resolution is 1680x1050


Here is the output of dmseg | grep drm

```
mikobuntu@mikobuntu-MS-7721:~$ dmesg | grep drm
[   16.284905] [drm] Initialized drm 1.1.0 20060810
[   16.339106] [drm] radeon kernel modesetting enabled.
[   16.341855] fb: conflicting fb hw usage radeondrmfb vs EFI VGA - removing generic driver
[   16.343835] [drm] initializing kernel modesetting (ARUBA 0x1002:0x990E 0x1462:0x7721).
[   16.343865] [drm] register mmio base: 0xFEF00000
[   16.343867] [drm] register mmio size: 262144
[   16.343983] [drm] Detected VRAM RAM=768M, BAR=256M
[   16.343984] [drm] RAM width 64bits DDR
[   16.344262] [drm] radeon: 768M of VRAM memory ready
[   16.344263] [drm] radeon: 1024M of GTT memory ready.
[   16.344276] [drm] Loading ARUBA Microcode
[   16.664933] [drm] GART: num cpu pages 262144, num gpu pages 262144
[   16.682846] [drm] PCIE GART of 1024M enabled (table at 0x0000000000276000).
[   16.684124] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   16.684125] [drm] Driver supports precise vblank timestamp query.
[   16.684707] [drm] radeon: irq initialized.
[   16.715219] [drm] ring test on 0 succeeded in 2 usecs
[   16.715230] [drm] ring test on 3 succeeded in 3 usecs
[   16.715239] [drm] ring test on 4 succeeded in 4 usecs
[   16.772812] [drm] ring test on 5 succeeded in 2 usecs
[   16.792854] [drm] UVD initialized successfully.
[   16.794376] [drm] Enabling audio 0 support
[   16.794379] [drm] Enabling audio 1 support
[   16.794381] [drm] Enabling audio 2 support
[   16.794382] [drm] Enabling audio 3 support
[   16.794384] [drm] Enabling audio 4 support
[   16.794385] [drm] Enabling audio 5 support
[   16.794907] [drm] ib test on ring 0 succeeded in 0 usecs
[   16.795429] [drm] ib test on ring 3 succeeded in 0 usecs
[   16.795941] [drm] ib test on ring 4 succeeded in 0 usecs
[   16.816818] [drm] ib test on ring 5 succeeded
[   16.840636] [drm] Radeon Display Connectors
[   16.840639] [drm] Connector 0:
[   16.840641] [drm]   HDMI-A-1
[   16.840642] [drm]   HPD1
[   16.840644] [drm]   DDC: 0x6530 0x6530 0x6534 0x6534 0x6538 0x6538 0x653c 0x653c
[   16.840645] [drm]   Encoders:
[   16.840647] [drm]     DFP1: INTERNAL_UNIPHY2
[   16.840648] [drm] Connector 1:
[   16.840650] [drm]   VGA-1
[   16.840651] [drm]   HPD2
[   16.840653] [drm]   DDC: 0x6540 0x6540 0x6544 0x6544 0x6548 0x6548 0x654c 0x654c
[   16.840654] [drm]   Encoders:
[   16.840655] [drm]     CRT1: INTERNAL_UNIPHY2
[   16.840657] [drm]     CRT1: NUTMEG
[   16.865541] [drm] Internal thermal controller without fan control
[   16.866507] [drm] radeon: dpm initialized
[   16.957994] [drm] fb mappable at 0xC1488000
[   16.957996] [drm] vram apper at 0xC0000000
[   16.957997] [drm] size 8294400
[   16.957998] [drm] fb depth is 24
[   16.957999] [drm]    pitch is 7680
[   16.958074] fbcon: radeondrmfb (fb0) is primary device
[   17.021678] radeon 0000:00:01.0: fb0: radeondrmfb frame buffer device
[   17.021684] [drm] Initialized radeon 2.36.0 20080528 for 0000:00:01.0 on minor 0



```
... And the output of running bootinfoscript

                  Boot Info Script 0.61      [1 April 2012]




```
============================= Boot Info Summary: ===============================


 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    1493797752 of the same hard drive for core.img. core.img is at this 
    location and looks in partition 112 for .


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.
    Operating System:  
    Boot files:        /efi/ubuntu/grubx64.efi /efi/ubuntu/MokManager.efi 
                       /efi/ubuntu/shimx64.efi


sda2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf


sda3: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT




GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       194,559       192,512 EFI System partition
/dev/sda2         194,560 1,921,636,351 1,921,441,792 Data partition (Windows/Linux)
/dev/sda3   1,921,636,352 1,953,523,711    31,887,360 Swap partition (Linux)


"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/sda1        D7C3-7BE6                              vfat       
/dev/sda2        0a72f170-6213-4a0b-828a-35f94ce622a0   ext4       
/dev/sda3        726d8204-cc66-40d5-8d56-922f6ce1092c   swap       


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/sda1        /boot/efi                vfat       (rw)
/dev/sda2        /                        ext4       (rw,errors=remount-ro)




=========================== sda2/boot/grub/grub.cfg: ===========================


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
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi


if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi


export menuentry_id_option


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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}


if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
set root='hd0,gpt2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  0a72f170-6213-4a0b-828a-35f94ce622a0
else
  search --no-floppy --fs-uuid --set=root 0a72f170-6213-4a0b-828a-35f94ce622a0
fi
    font="/usr/share/grub/unicode.pf2"
fi


if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###


### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###


### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-0a72f170-6213-4a0b-828a-35f94ce622a0' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  0a72f170-6213-4a0b-828a-35f94ce622a0
    else
      search --no-floppy --fs-uuid --set=root 0a72f170-6213-4a0b-828a-35f94ce622a0
    fi
    linux    /boot/vmlinuz-3.13.0-48-lowlatency root=UUID=0a72f170-6213-4a0b-828a-35f94ce622a0 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-48-lowlatency
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-0a72f170-6213-4a0b-828a-35f94ce622a0' {
    menuentry 'Ubuntu, with Linux 3.13.0-48-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-48-lowlatency-advanced-0a72f170-6213-4a0b-828a-35f94ce622a0' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  0a72f170-6213-4a0b-828a-35f94ce622a0
        else
          search --no-floppy --fs-uuid --set=root 0a72f170-6213-4a0b-828a-35f94ce622a0
        fi
        echo    'Loading Linux 3.13.0-48-lowlatency ...'
        linux    /boot/vmlinuz-3.13.0-48-lowlatency root=UUID=0a72f170-6213-4a0b-828a-35f94ce622a0 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-48-lowlatency
    }
    menuentry 'Ubuntu, with Linux 3.13.0-48-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-48-lowlatency-recovery-0a72f170-6213-4a0b-828a-35f94ce622a0' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  0a72f170-6213-4a0b-828a-35f94ce622a0
        else
          search --no-floppy --fs-uuid --set=root 0a72f170-6213-4a0b-828a-35f94ce622a0
        fi
        echo    'Loading Linux 3.13.0-48-lowlatency ...'
        linux    /boot/vmlinuz-3.13.0-48-lowlatency root=UUID=0a72f170-6213-4a0b-828a-35f94ce622a0 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-48-lowlatency
    }
    menuentry 'Ubuntu, with Linux 3.13.0-48-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-48-generic-advanced-0a72f170-6213-4a0b-828a-35f94ce622a0' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  0a72f170-6213-4a0b-828a-35f94ce622a0
        else
          search --no-floppy --fs-uuid --set=root 0a72f170-6213-4a0b-828a-35f94ce622a0
        fi
        echo    'Loading Linux 3.13.0-48-generic ...'
        linux    /boot/vmlinuz-3.13.0-48-generic.efi.signed root=UUID=0a72f170-6213-4a0b-828a-35f94ce622a0 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-48-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-48-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-48-generic-recovery-0a72f170-6213-4a0b-828a-35f94ce622a0' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  0a72f170-6213-4a0b-828a-35f94ce622a0
        else
          search --no-floppy --fs-uuid --set=root 0a72f170-6213-4a0b-828a-35f94ce622a0
        fi
        echo    'Loading Linux 3.13.0-48-generic ...'
        linux    /boot/vmlinuz-3.13.0-48-generic.efi.signed root=UUID=0a72f170-6213-4a0b-828a-35f94ce622a0 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-48-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-47-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-47-lowlatency-advanced-0a72f170-6213-4a0b-828a-35f94ce622a0' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  0a72f170-6213-4a0b-828a-35f94ce622a0
        else
          search --no-floppy --fs-uuid --set=root 0a72f170-6213-4a0b-828a-35f94ce622a0
        fi
        echo    'Loading Linux 3.13.0-47-lowlatency ...'
        linux    /boot/vmlinuz-3.13.0-47-lowlatency root=UUID=0a72f170-6213-4a0b-828a-35f94ce622a0 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-47-lowlatency
    }
    menuentry 'Ubuntu, with Linux 3.13.0-47-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-47-lowlatency-recovery-0a72f170-6213-4a0b-828a-35f94ce622a0' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  0a72f170-6213-4a0b-828a-35f94ce622a0
        else
          search --no-floppy --fs-uuid --set=root 0a72f170-6213-4a0b-828a-35f94ce622a0
        fi
        echo    'Loading Linux 3.13.0-47-lowlatency ...'
        linux    /boot/vmlinuz-3.13.0-47-lowlatency root=UUID=0a72f170-6213-4a0b-828a-35f94ce622a0 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-47-lowlatency
    }
    menuentry 'Ubuntu, with Linux 3.13.0-47-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-47-generic-advanced-0a72f170-6213-4a0b-828a-35f94ce622a0' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  0a72f170-6213-4a0b-828a-35f94ce622a0
        else
          search --no-floppy --fs-uuid --set=root 0a72f170-6213-4a0b-828a-35f94ce622a0
        fi
        echo    'Loading Linux 3.13.0-47-generic ...'
        linux    /boot/vmlinuz-3.13.0-47-generic.efi.signed root=UUID=0a72f170-6213-4a0b-828a-35f94ce622a0 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-47-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-47-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-47-generic-recovery-0a72f170-6213-4a0b-828a-35f94ce622a0' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  0a72f170-6213-4a0b-828a-35f94ce622a0
        else
          search --no-floppy --fs-uuid --set=root 0a72f170-6213-4a0b-828a-35f94ce622a0
        fi
        echo    'Loading Linux 3.13.0-47-generic ...'
        linux    /boot/vmlinuz-3.13.0-47-generic.efi.signed root=UUID=0a72f170-6213-4a0b-828a-35f94ce622a0 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-47-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-46-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-46-lowlatency-advanced-0a72f170-6213-4a0b-828a-35f94ce622a0' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  0a72f170-6213-4a0b-828a-35f94ce622a0
        else
          search --no-floppy --fs-uuid --set=root 0a72f170-6213-4a0b-828a-35f94ce622a0
        fi
        echo    'Loading Linux 3.13.0-46-lowlatency ...'
        linux    /boot/vmlinuz-3.13.0-46-lowlatency root=UUID=0a72f170-6213-4a0b-828a-35f94ce622a0 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-46-lowlatency
    }
    menuentry 'Ubuntu, with Linux 3.13.0-46-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-46-lowlatency-recovery-0a72f170-6213-4a0b-828a-35f94ce622a0' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  0a72f170-6213-4a0b-828a-35f94ce622a0
        else
          search --no-floppy --fs-uuid --set=root 0a72f170-6213-4a0b-828a-35f94ce622a0
        fi
        echo    'Loading Linux 3.13.0-46-lowlatency ...'
        linux    /boot/vmlinuz-3.13.0-46-lowlatency root=UUID=0a72f170-6213-4a0b-828a-35f94ce622a0 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-46-lowlatency
    }
    menuentry 'Ubuntu, with Linux 3.13.0-46-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-46-generic-advanced-0a72f170-6213-4a0b-828a-35f94ce622a0' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  0a72f170-6213-4a0b-828a-35f94ce622a0
        else
          search --no-floppy --fs-uuid --set=root 0a72f170-6213-4a0b-828a-35f94ce622a0
        fi
        echo    'Loading Linux 3.13.0-46-generic ...'
        linux    /boot/vmlinuz-3.13.0-46-generic.efi.signed root=UUID=0a72f170-6213-4a0b-828a-35f94ce622a0 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-46-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-46-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-46-generic-recovery-0a72f170-6213-4a0b-828a-35f94ce622a0' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  0a72f170-6213-4a0b-828a-35f94ce622a0
        else
          search --no-floppy --fs-uuid --set=root 0a72f170-6213-4a0b-828a-35f94ce622a0
        fi
        echo    'Loading Linux 3.13.0-46-generic ...'
        linux    /boot/vmlinuz-3.13.0-46-generic.efi.signed root=UUID=0a72f170-6213-4a0b-828a-35f94ce622a0 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-46-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-45-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-45-generic-advanced-0a72f170-6213-4a0b-828a-35f94ce622a0' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  0a72f170-6213-4a0b-828a-35f94ce622a0
        else
          search --no-floppy --fs-uuid --set=root 0a72f170-6213-4a0b-828a-35f94ce622a0
        fi
        echo    'Loading Linux 3.13.0-45-generic ...'
        linux    /boot/vmlinuz-3.13.0-45-generic root=UUID=0a72f170-6213-4a0b-828a-35f94ce622a0 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-45-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-45-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-45-generic-recovery-0a72f170-6213-4a0b-828a-35f94ce622a0' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  0a72f170-6213-4a0b-828a-35f94ce622a0
        else
          search --no-floppy --fs-uuid --set=root 0a72f170-6213-4a0b-828a-35f94ce622a0
        fi
        echo    'Loading Linux 3.13.0-45-generic ...'
        linux    /boot/vmlinuz-3.13.0-45-generic root=UUID=0a72f170-6213-4a0b-828a-35f94ce622a0 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-45-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-44-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-advanced-0a72f170-6213-4a0b-828a-35f94ce622a0' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  0a72f170-6213-4a0b-828a-35f94ce622a0
        else
          search --no-floppy --fs-uuid --set=root 0a72f170-6213-4a0b-828a-35f94ce622a0
        fi
        echo    'Loading Linux 3.13.0-44-generic ...'
        linux    /boot/vmlinuz-3.13.0-44-generic root=UUID=0a72f170-6213-4a0b-828a-35f94ce622a0 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-44-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-44-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-recovery-0a72f170-6213-4a0b-828a-35f94ce622a0' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  0a72f170-6213-4a0b-828a-35f94ce622a0
        else
          search --no-floppy --fs-uuid --set=root 0a72f170-6213-4a0b-828a-35f94ce622a0
        fi
        echo    'Loading Linux 3.13.0-44-generic ...'
        linux    /boot/vmlinuz-3.13.0-44-generic root=UUID=0a72f170-6213-4a0b-828a-35f94ce622a0 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-44-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-38-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-38-generic-advanced-0a72f170-6213-4a0b-828a-35f94ce622a0' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  0a72f170-6213-4a0b-828a-35f94ce622a0
        else
          search --no-floppy --fs-uuid --set=root 0a72f170-6213-4a0b-828a-35f94ce622a0
        fi
        echo    'Loading Linux 3.13.0-38-generic ...'
        linux    /boot/vmlinuz-3.13.0-38-generic root=UUID=0a72f170-6213-4a0b-828a-35f94ce622a0 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-38-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-38-generic-recovery-0a72f170-6213-4a0b-828a-35f94ce622a0' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  0a72f170-6213-4a0b-828a-35f94ce622a0
        else
          search --no-floppy --fs-uuid --set=root 0a72f170-6213-4a0b-828a-35f94ce622a0
        fi
        echo    'Loading Linux 3.13.0-38-generic ...'
        linux    /boot/vmlinuz-3.13.0-38-generic root=UUID=0a72f170-6213-4a0b-828a-35f94ce622a0 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-38-generic
    }
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###


### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###


### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------


=============================== sda2/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=0a72f170-6213-4a0b-828a-35f94ce622a0 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=D7C3-7BE6  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=726d8204-cc66-40d5-8d56-922f6ce1092c none            swap    sw              0       0
--------------------------------------------------------------------------------


====================== sda2/boot/extlinux/extlinux.conf: =======================


--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update




default l0
prompt 1
timeout 50


include themes/debian/theme.cfg
--------------------------------------------------------------------------------


=================== sda2: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)




================= sda2: Location of files loaded by Syslinux: ==================


           GiB - GB             File                                 Fragment(s)




============== sda2: Version of COM32(R) files used by Syslinux: ===============


 boot/extlinux/chain.c32            :  COM32R module (v4.xx)


========= Devices which don't seem to have a corresponding hard drive: =========


sdb 


=============================== StdErr Messages: ===============================


cat: /tmp/BootInfo-ePETZKUs/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-ePETZKUs/Tmp_Log: No such file or directory



```

Output from grepping " EDID " on /var/log/Xorg.0.log   ( This bug could possible be related to EDID settings of my Samsung S22C150 monitor ? )

```
mikobuntu@mikobuntu-MS-7721:/var/log$ cat Xorg.0.log | grep EDID[    26.613] (II) RADEON(0): EDID for output HDMI-0
[    26.686] (II) RADEON(0): EDID for output VGA-0
[    26.686] (II) RADEON(0): EDID Version: 1.3
[    26.686] (II) RADEON(0): EDID (in hex):
[    29.425] (II) RADEON(0): EDID vendor "SAM", prod id 2789
[    29.425] (II) RADEON(0): Using EDID range info for horizontal sync
[    29.425] (II) RADEON(0): Using EDID range info for vertical refresh
[    35.773] (II) RADEON(0): EDID vendor "SAM", prod id 2789
[    36.536] (II) RADEON(0): EDID vendor "SAM", prod id 2789
[    37.272] (II) RADEON(0): EDID vendor "SAM", prod id 2789
[    37.807] (II) RADEON(0): EDID vendor "SAM", prod id 2789
[    40.903] (II) RADEON(0): EDID vendor "SAM", prod id 2789
[    53.747] (II) RADEON(0): EDID vendor "SAM", prod id 2789
[   308.251] (II) RADEON(0): EDID vendor "SAM", prod id 2789
[   695.810] (II) RADEON(0): EDID vendor "SAM", prod id 2789
[  1908.165] (II) RADEON(0): EDID vendor "SAM", prod id 2789


* Possibly related, but I get no output from command  [FONT=Consolas][COLOR=#000000]" parse-edid " from this post here >> [/COLOR][/FONT]http://hotcashew.com/2013/08/fixing-invalid-edid-in-linux-wit-fglrx/     after being able to successfully create the[CODE] edid-decode edid.bin
``` file see here the output from that :--


```
mikobuntu@mikobuntu-MS-7721:~$ edid-decode edid.binExtracted contents:
header:          22 30 30 66 66 66 66 66
serial number:   66 66 66 66 66 66 66 30 30 34
version:         63 32
basic params:    64 65 35 30 61
chroma info:     34 38 34 37 35 39 35 61 31 34
established:     31 37 30
standard:        31 30 33 30 65 33 30 31 62 37 38 32 61 39 30 63
descriptor 1:    31 61 32 35 39 35 35 39 63 32 37 30 65 35 30 35 34 62
descriptor 2:    66 65 66 38 30 37 31 34 66 38 31 63 30 38 31 30 30 38
descriptor 3:    31 38 30 39 35 30 30 61 39 63 30 62 33 30 30 30 31 30
descriptor 4:    31 30 32 33 61 38 30 31 38 37 31 33 38 32 64 34 30 35
extensions:      38
checksum:        32


No header found
Manufacturer: YSF Model 6666 Serial Number 812017254
EDID version: 99.50
Analog display, Input voltage level: 0.7/0.7 V
Sync: Composite 
Maximum image size: 101 cm x 53 cm
Gamma: 1.48
DPMS levels: Suspend Off
Monochrome or grayscale display
Supports GTF timings within operating range
Established timings supported:
  640x480@60Hz
  640x480@67Hz
  800x600@60Hz
  832x624@75Hz
  1280x768@87Hz
  1024x768@70Hz
  1024x768@75Hz
  1280x1024@75Hz
Standard timings supported:
  640x400@108Hz
  656x410@108Hz
  1056x660@111Hz
  632x395@109Hz
  1032x645@115Hz
  696x435@110Hz
  1024x640@117Hz
  632x474@95Hz
Detailed mode: Clock 248.810 MHz, 869 mm x 53 mm
                818  917 1735 3175 hborder 53
                821  824  831 3178 vborder 52
               +hsync -vsync analog composite
Detailed mode: Clock 259.580 MHz, 816 mm x 312 mm
                870 1228 1796  926 hborder 48
                823  826  875 1896 vborder 48
               -hsync -vsync
Detailed mode: Clock 143.850 MHz, 819 mm x 48 mm
                816 1129 1740 2153 hborder 48
               1584 1587 1619 1888 vborder 49
               -hsync -vsync digital composite
Detailed mode: Clock 123.370 MHz, 1592 mm x 1074 mm
               1586 1642 2465 1893 hborder 52
                824  827  876 1128 vborder 48
               -hsync +vsync digital composite
Has 56 extension blocks
Checksum: 0x32 (should be 0xef)
EDID block does not conform at all!
    Block has broken checksum
    Bad year of manufacture
mikobuntu@mikobuntu-MS-7721:~$ 



```


[/CODE]

The full Xorg.0.log   ( If anyone wants to filter through this ?? ) thanks :)

```
[    25.666] X.Org X Server 1.15.1
Release Date: 2014-04-13
[    25.666] X Protocol Version 11, Revision 0
[    25.666] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[    25.666] Current Operating System: Linux mikobuntu-MS-7721 3.13.0-48-lowlatency #80-Ubuntu SMP PREEMPT Thu Mar 12 11:33:22 UTC 2015 x86_64
[    25.666] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-48-lowlatency root=UUID=0a72f170-6213-4a0b-828a-35f94ce622a0 ro quiet splash vt.handoff=7
[    25.666] Build Date: 12 February 2015  02:49:29PM
[    25.666] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[    25.666] Current version of pixman: 0.30.2
[    25.666]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    25.666] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    25.667] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Mar 15 16:40:17 2015
[    25.667] (==) Using config file: "/etc/X11/xorg.conf"
[    25.667] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    25.667] (==) ServerLayout "aticonfig Layout"
[    25.667] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    25.667] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    25.668] (**) |   |-->Device "aticonfig-Device[0]-0"
[    25.668] (==) Automatically adding devices
[    25.668] (==) Automatically enabling devices
[    25.668] (==) Automatically adding GPU devices
[    25.668] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    25.668]     Entry deleted from font path.
[    25.668] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    25.668]     Entry deleted from font path.
[    25.668] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    25.668]     Entry deleted from font path.
[    25.668] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/75dpi,
    built-ins
[    25.668] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    25.668] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    25.668] (II) Loader magic: 0x7f565bc0dd40
[    25.668] (II) Module ABI versions:
[    25.668]     X.Org ANSI C Emulation: 0.4
[    25.668]     X.Org Video Driver: 15.0
[    25.668]     X.Org XInput driver : 20.0
[    25.668]     X.Org Server Extension : 8.0
[    25.668] (II) xfree86: Adding drm device (/dev/dri/card0)
[    25.670] (--) PCI:*(0:0:1:0) 1002:990e:1462:7721 rev 0, Mem @ 0xc0000000/268435456, 0xfef00000/262144, I/O @ 0x0000f000/256
[    25.670] Initializing built-in extension Generic Event Extension
[    25.670] Initializing built-in extension SHAPE
[    25.670] Initializing built-in extension MIT-SHM
[    25.670] Initializing built-in extension XInputExtension
[    25.670] Initializing built-in extension XTEST
[    25.670] Initializing built-in extension BIG-REQUESTS
[    25.670] Initializing built-in extension SYNC
[    25.670] Initializing built-in extension XKEYBOARD
[    25.670] Initializing built-in extension XC-MISC
[    25.670] Initializing built-in extension SECURITY
[    25.670] Initializing built-in extension XINERAMA
[    25.670] Initializing built-in extension XFIXES
[    25.670] Initializing built-in extension RENDER
[    25.670] Initializing built-in extension RANDR
[    25.670] Initializing built-in extension COMPOSITE
[    25.670] Initializing built-in extension DAMAGE
[    25.670] Initializing built-in extension MIT-SCREEN-SAVER
[    25.670] Initializing built-in extension DOUBLE-BUFFER
[    25.670] Initializing built-in extension RECORD
[    25.670] Initializing built-in extension DPMS
[    25.670] Initializing built-in extension Present
[    25.670] Initializing built-in extension DRI3
[    25.670] Initializing built-in extension X-Resource
[    25.670] Initializing built-in extension XVideo
[    25.670] Initializing built-in extension XVideo-MotionCompensation
[    25.670] Initializing built-in extension SELinux
[    25.670] Initializing built-in extension XFree86-VidModeExtension
[    25.670] Initializing built-in extension XFree86-DGA
[    25.670] Initializing built-in extension XFree86-DRI
[    25.670] Initializing built-in extension DRI2
[    25.670] (II) "glx" will be loaded by default.
[    25.670] (WW) "xmir" is not to be loaded by default. Skipping.
[    25.670] (II) LoadModule: "glx"
[    25.697] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    26.148] (II) Module glx: vendor="X.Org Foundation"
[    26.148]     compiled for 1.15.1, module version = 1.0.0
[    26.148]     ABI class: X.Org Server Extension, version 8.0
[    26.148] (==) AIGLX enabled
[    26.148] Loading extension GLX
[    26.148] (II) LoadModule: "fglrx"
[    26.149] (WW) Warning, couldn't open module fglrx
[    26.149] (II) UnloadModule: "fglrx"
[    26.149] (II) Unloading fglrx
[    26.149] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    26.149] (==) Matched fglrx as autoconfigured driver 0
[    26.149] (==) Matched ati as autoconfigured driver 1
[    26.149] (==) Matched fglrx as autoconfigured driver 2
[    26.149] (==) Matched ati as autoconfigured driver 3
[    26.149] (==) Matched modesetting as autoconfigured driver 4
[    26.149] (==) Matched fbdev as autoconfigured driver 5
[    26.149] (==) Matched vesa as autoconfigured driver 6
[    26.149] (==) Assigned the driver to the xf86ConfigLayout
[    26.149] (II) LoadModule: "fglrx"
[    26.150] (WW) Warning, couldn't open module fglrx
[    26.150] (II) UnloadModule: "fglrx"
[    26.150] (II) Unloading fglrx
[    26.150] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    26.150] (II) LoadModule: "ati"
[    26.150] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    26.168] (II) Module ati: vendor="X.Org Foundation"
[    26.168]     compiled for 1.15.1, module version = 7.3.0
[    26.168]     Module class: X.Org Video Driver
[    26.168]     ABI class: X.Org Video Driver, version 15.0
[    26.168] (II) LoadModule: "radeon"
[    26.168] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    26.352] (II) Module radeon: vendor="X.Org Foundation"
[    26.352]     compiled for 1.15.1, module version = 7.3.0
[    26.352]     Module class: X.Org Video Driver
[    26.352]     ABI class: X.Org Video Driver, version 15.0
[    26.352] (II) LoadModule: "modesetting"
[    26.353] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    26.407] (II) Module modesetting: vendor="X.Org Foundation"
[    26.407]     compiled for 1.15.0, module version = 0.8.1
[    26.407]     Module class: X.Org Video Driver
[    26.407]     ABI class: X.Org Video Driver, version 15.0
[    26.407] (II) LoadModule: "fbdev"
[    26.407] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    26.443] (II) Module fbdev: vendor="X.Org Foundation"
[    26.443]     compiled for 1.15.0, module version = 0.4.4
[    26.443]     Module class: X.Org Video Driver
[    26.443]     ABI class: X.Org Video Driver, version 15.0
[    26.443] (II) LoadModule: "vesa"
[    26.443] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.480] (II) Module vesa: vendor="X.Org Foundation"
[    26.480]     compiled for 1.15.0, module version = 2.3.3
[    26.480]     Module class: X.Org Video Driver
[    26.480]     ABI class: X.Org Video Driver, version 15.0
[    26.480] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
    ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
    ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
    SUMO, SUMO, SUMO2, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
    ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
    CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
    OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, HAINAN, HAINAN, HAINAN,
    HAINAN, HAINAN, HAINAN, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
    BONAIRE, BONAIRE, BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
    HAWAII, HAWAII, HAWAII, HAWAII
[    26.491] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    26.492] (II) FBDEV: driver for framebuffer: fbdev
[    26.492] (II) VESA: driver for VESA chipsets: vesa
[    26.492] (++) using VT number 7


[    26.492] (II) [KMS] Kernel modesetting enabled.
[    26.492] (WW) Falling back to old probe method for modesetting
[    26.492] (WW) Falling back to old probe method for fbdev
[    26.492] (II) Loading sub module "fbdevhw"
[    26.492] (II) LoadModule: "fbdevhw"
[    26.492] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    26.522] (II) Module fbdevhw: vendor="X.Org Foundation"
[    26.522]     compiled for 1.15.1, module version = 0.0.2
[    26.522]     ABI class: X.Org Video Driver, version 15.0
[    26.522] (WW) Falling back to old probe method for vesa
[    26.522] (**) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    26.522] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    26.522] (==) RADEON(0): Default visual is TrueColor
[    26.522] (==) RADEON(0): RGB weight 888
[    26.522] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    26.522] (--) RADEON(0): Chipset: "ARUBA" (ChipID = 0x990e)
[    26.522] (II) Loading sub module "dri2"
[    26.522] (II) LoadModule: "dri2"
[    26.522] (II) Module "dri2" already built-in
[    26.522] (II) Loading sub module "exa"
[    26.522] (II) LoadModule: "exa"
[    26.522] (II) Loading /usr/lib/xorg/modules/libexa.so
[    26.536] (II) Module exa: vendor="X.Org Foundation"
[    26.536]     compiled for 1.15.1, module version = 2.6.0
[    26.536]     ABI class: X.Org Video Driver, version 15.0
[    26.536] (II) RADEON(0): KMS Color Tiling: enabled
[    26.536] (II) RADEON(0): KMS Color Tiling 2D: enabled
[    26.536] (II) RADEON(0): KMS Pageflipping: enabled
[    26.536] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    26.538] (II) RADEON(0): Output HDMI-0 using monitor section aticonfig-Monitor[0]-0
[    26.611] (II) RADEON(0): Output VGA-0 has no monitor section
[    26.613] (II) RADEON(0): EDID for output HDMI-0
[    26.686] (II) RADEON(0): EDID for output VGA-0
[    26.686] (II) RADEON(0): Manufacturer: SAM  Model: ae5  Serial#: 1515800392
[    26.686] (II) RADEON(0): Year: 2013  Week: 20
[    26.686] (II) RADEON(0): EDID Version: 1.3
[    26.686] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    26.686] (II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
[    26.686] (II) RADEON(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[    26.686] (II) RADEON(0): Gamma: 2.20
[    26.686] (II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
[    26.686] (II) RADEON(0): First detailed timing is preferred mode
[    26.686] (II) RADEON(0): redX: 0.635 redY: 0.349   greenX: 0.332 greenY: 0.609
[    26.686] (II) RADEON(0): blueX: 0.155 blueY: 0.055   whiteX: 0.312 whiteY: 0.329
[    26.686] (II) RADEON(0): Supported established timings:
[    26.686] (II) RADEON(0): 720x400@70Hz
[    26.686] (II) RADEON(0): 640x480@60Hz
[    26.686] (II) RADEON(0): 640x480@67Hz
[    26.686] (II) RADEON(0): 640x480@72Hz
[    26.686] (II) RADEON(0): 640x480@75Hz
[    26.686] (II) RADEON(0): 800x600@56Hz
[    26.686] (II) RADEON(0): 800x600@60Hz
[    26.686] (II) RADEON(0): 800x600@72Hz
[    26.686] (II) RADEON(0): 800x600@75Hz
[    26.686] (II) RADEON(0): 832x624@75Hz
[    26.686] (II) RADEON(0): 1024x768@60Hz
[    26.686] (II) RADEON(0): 1024x768@70Hz
[    26.686] (II) RADEON(0): 1024x768@75Hz
[    26.686] (II) RADEON(0): 1280x1024@75Hz
[    26.686] (II) RADEON(0): 1152x864@75Hz
[    26.686] (II) RADEON(0): Manufacturer's mask: 0
[    26.686] (II) RADEON(0): Supported standard timings:
[    26.686] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    26.686] (II) RADEON(0): #1: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    26.686] (II) RADEON(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
[    26.686] (II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    26.686] (II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    26.686] (II) RADEON(0): #5: hsize: 1600  vsize 900  refresh: 60  vid: 49321
[    26.686] (II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    26.686] (II) RADEON(0): Supported detailed timing:
[    26.686] (II) RADEON(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[    26.686] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    26.686] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    26.686] (II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 175 MHz
[    26.686] (II) RADEON(0): Monitor name: S22C150
[    26.686] (II) RADEON(0): Serial No: H4LD507605
[    26.686] (II) RADEON(0): EDID (in hex):
[    26.686] (II) RADEON(0):     00ffffffffffff004c2de50a4847595a
[    26.686] (II) RADEON(0):     141701030e301b782a90c1a259559c27
[    26.686] (II) RADEON(0):     0e5054bfef80714f81c0810081809500
[    26.686] (II) RADEON(0):     a9c0b3000101023a801871382d40582c
[    26.686] (II) RADEON(0):     4500dd0c1100001e000000fd00384b1e
[    26.686] (II) RADEON(0):     5111000a202020202020000000fc0053
[    26.686] (II) RADEON(0):     3232433135300a2020202020000000ff
[    26.686] (II) RADEON(0):     0048344c443530373630350a20200061
[    26.686] (II) RADEON(0): Printing probed modes for output VGA-0
[    26.686] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    26.686] (II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    26.686] (II) RADEON(0): Modeline "1600x900"x60.0  118.96  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[    26.686] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    26.686] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    26.686] (II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    26.686] (II) RADEON(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz e)
[    26.686] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    26.686] (II) RADEON(0): Modeline "1280x720"x60.0   74.44  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.7 kHz)
[    26.686] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[    26.686] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    26.686] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    26.686] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    26.686] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    26.686] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    26.686] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    26.686] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    26.686] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    26.686] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[    26.686] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    26.687] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    26.687] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    26.687] (II) RADEON(0): Output HDMI-0 disconnected
[    26.687] (II) RADEON(0): Output VGA-0 connected
[    26.687] (II) RADEON(0): Using exact sizes for initial modes
[    26.687] (II) RADEON(0): Output VGA-0 using initial mode 1920x1080
[    26.687] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    26.687] (II) RADEON(0): mem size init: gart size :3fdde000 vram size: s:30000000 visible:2f7d7000
[    26.687] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    26.687] (==) RADEON(0): DPI set to (96, 96)
[    26.687] (II) Loading sub module "fb"
[    26.687] (II) LoadModule: "fb"
[    26.687] (II) Loading /usr/lib/xorg/modules/libfb.so
[    26.687] (II) Module fb: vendor="X.Org Foundation"
[    26.687]     compiled for 1.15.1, module version = 1.0.0
[    26.687]     ABI class: X.Org ANSI C Emulation, version 0.4
[    26.687] (II) Loading sub module "ramdac"
[    26.687] (II) LoadModule: "ramdac"
[    26.687] (II) Module "ramdac" already built-in
[    26.687] (II) UnloadModule: "modesetting"
[    26.687] (II) Unloading modesetting
[    26.687] (II) UnloadModule: "fbdev"
[    26.687] (II) Unloading fbdev
[    26.687] (II) UnloadSubModule: "fbdevhw"
[    26.687] (II) Unloading fbdevhw
[    26.687] (II) UnloadModule: "vesa"
[    26.687] (II) Unloading vesa
[    26.687] (--) Depth 24 pixmap format is 32 bpp
[    26.687] (II) RADEON(0): [DRI2] Setup complete
[    26.687] (II) RADEON(0): [DRI2]   DRI driver: r600
[    26.687] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[    26.687] (II) RADEON(0): Front buffer size: 8160K
[    26.687] (II) RADEON(0): VRAM usage limit set to 692866K
[    26.687] (==) RADEON(0): Backing store enabled
[    26.687] (II) RADEON(0): Direct rendering enabled
[    26.687] (II) EXA(0): Driver allocated offscreen pixmaps
[    26.687] (II) EXA(0): Driver registered support for the following operations:
[    26.687] (II)         Solid
[    26.687] (II)         Copy
[    26.687] (II)         Composite (RENDER acceleration)
[    26.687] (II)         UploadToScreen
[    26.687] (II)         DownloadFromScreen
[    26.687] (II) RADEON(0): Acceleration enabled
[    26.687] (**) RADEON(0): DPMS enabled
[    26.687] (==) RADEON(0): Silken mouse enabled
[    26.688] (II) RADEON(0): Set up textured video
[    26.688] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    26.688] (II) RADEON(0): [XvMC] Extension initialized.
[    26.688] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    26.688] (WW) RADEON(0): Option "VendorName" is not used
[    26.688] (WW) RADEON(0): Option "ModelName" is not used
[    26.688] (--) RandR disabled
[    26.692] (II) SELinux: Disabled on system
[    27.123] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    27.123] (II) AIGLX: enabled GLX_ARB_create_context
[    27.123] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    27.123] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    27.123] (II) AIGLX: enabled GLX_INTEL_swap_event
[    27.123] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    27.123] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    27.124] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    27.124] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    27.125] (II) AIGLX: Loaded and initialized r600
[    27.125] (II) GLX: Initialized DRI2 GL provider for screen 0
[    27.237] (II) RADEON(0): Setting screen physical size to 508 x 285
[    27.250] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    27.253] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    27.253] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.253] (II) LoadModule: "evdev"
[    27.253] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.263] (II) Module evdev: vendor="X.Org Foundation"
[    27.263]     compiled for 1.15.0, module version = 2.8.2
[    27.263]     Module class: X.Org XInput Driver
[    27.263]     ABI class: X.Org XInput driver, version 20.0
[    27.263] (II) Using input driver 'evdev' for 'Power Button'
[    27.263] (**) Power Button: always reports core events
[    27.263] (**) evdev: Power Button: Device: "/dev/input/event1"
[    27.263] (--) evdev: Power Button: Vendor 0 Product 0x1
[    27.263] (--) evdev: Power Button: Found keys
[    27.263] (II) evdev: Power Button: Configuring as keyboard
[    27.263] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    27.263] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    27.263] (**) Option "xkb_rules" "evdev"
[    27.263] (**) Option "xkb_model" "pc105"
[    27.263] (**) Option "xkb_layout" "gb"
[    27.267] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    27.268] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    27.268] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.268] (II) Using input driver 'evdev' for 'Power Button'
[    27.268] (**) Power Button: always reports core events
[    27.268] (**) evdev: Power Button: Device: "/dev/input/event0"
[    27.268] (--) evdev: Power Button: Vendor 0 Product 0x1
[    27.268] (--) evdev: Power Button: Found keys
[    27.268] (II) evdev: Power Button: Configuring as keyboard
[    27.269] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    27.269] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    27.269] (**) Option "xkb_rules" "evdev"
[    27.269] (**) Option "xkb_model" "pc105"
[    27.269] (**) Option "xkb_layout" "gb"
[    27.269] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:01.0/drm/card0
[    27.269] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    27.270] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event6)
[    27.270] (II) No input driver specified, ignoring this device.
[    27.270] (II) This device may have been added with another device file.
[    27.270] (II) config/udev: Adding input device C-Media USB Headphone Set   (/dev/input/event2)
[    27.270] (**) C-Media USB Headphone Set  : Applying InputClass "evdev keyboard catchall"
[    27.270] (II) Using input driver 'evdev' for 'C-Media USB Headphone Set  '
[    27.270] (**) C-Media USB Headphone Set  : always reports core events
[    27.270] (**) evdev: C-Media USB Headphone Set  : Device: "/dev/input/event2"
[    27.270] (--) evdev: C-Media USB Headphone Set  : Vendor 0xd8c Product 0xc
[    27.270] (--) evdev: C-Media USB Headphone Set  : Found keys
[    27.270] (II) evdev: C-Media USB Headphone Set  : Configuring as keyboard
[    27.270] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb4/4-1/4-1:1.3/input/input5/event2"
[    27.270] (II) XINPUT: Adding extended input device "C-Media USB Headphone Set  " (type: KEYBOARD, id 8)
[    27.270] (**) Option "xkb_rules" "evdev"
[    27.270] (**) Option "xkb_model" "pc105"
[    27.270] (**) Option "xkb_layout" "gb"
[    27.271] (II) config/udev: Adding input device HID 04f3:0103 (/dev/input/event3)
[    27.271] (**) HID 04f3:0103: Applying InputClass "evdev keyboard catchall"
[    27.271] (II) Using input driver 'evdev' for 'HID 04f3:0103'
[    27.271] (**) HID 04f3:0103: always reports core events
[    27.271] (**) evdev: HID 04f3:0103: Device: "/dev/input/event3"
[    27.271] (--) evdev: HID 04f3:0103: Vendor 0x4f3 Product 0x103
[    27.271] (--) evdev: HID 04f3:0103: Found keys
[    27.271] (II) evdev: HID 04f3:0103: Configuring as keyboard
[    27.271] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2.1/1-2.1:1.0/input/input6/event3"
[    27.271] (II) XINPUT: Adding extended input device "HID 04f3:0103" (type: KEYBOARD, id 9)
[    27.271] (**) Option "xkb_rules" "evdev"
[    27.271] (**) Option "xkb_model" "pc105"
[    27.271] (**) Option "xkb_layout" "gb"
[    27.272] (II) config/udev: Adding input device HID 04f3:0103 (/dev/input/event4)
[    27.272] (**) HID 04f3:0103: Applying InputClass "evdev keyboard catchall"
[    27.272] (II) Using input driver 'evdev' for 'HID 04f3:0103'
[    27.272] (**) HID 04f3:0103: always reports core events
[    27.272] (**) evdev: HID 04f3:0103: Device: "/dev/input/event4"
[    27.272] (--) evdev: HID 04f3:0103: Vendor 0x4f3 Product 0x103
[    27.272] (--) evdev: HID 04f3:0103: Found 1 mouse buttons
[    27.272] (--) evdev: HID 04f3:0103: Found scroll wheel(s)
[    27.272] (--) evdev: HID 04f3:0103: Found relative axes
[    27.272] (II) evdev: HID 04f3:0103: Forcing relative x/y axes to exist.
[    27.272] (--) evdev: HID 04f3:0103: Found absolute axes
[    27.272] (II) evdev: HID 04f3:0103: Forcing absolute x/y axes to exist.
[    27.272] (--) evdev: HID 04f3:0103: Found keys
[    27.272] (II) evdev: HID 04f3:0103: Configuring as mouse
[    27.272] (II) evdev: HID 04f3:0103: Configuring as keyboard
[    27.272] (II) evdev: HID 04f3:0103: Adding scrollwheel support
[    27.272] (**) evdev: HID 04f3:0103: YAxisMapping: buttons 4 and 5
[    27.272] (**) evdev: HID 04f3:0103: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    27.272] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2.1/1-2.1:1.1/input/input7/event4"
[    27.272] (II) XINPUT: Adding extended input device "HID 04f3:0103" (type: KEYBOARD, id 10)
[    27.272] (**) Option "xkb_rules" "evdev"
[    27.272] (**) Option "xkb_model" "pc105"
[    27.272] (**) Option "xkb_layout" "gb"
[    27.272] (II) evdev: HID 04f3:0103: initialized for relative axes.
[    27.272] (WW) evdev: HID 04f3:0103: ignoring absolute axes.
[    27.272] (**) HID 04f3:0103: (accel) keeping acceleration scheme 1
[    27.272] (**) HID 04f3:0103: (accel) acceleration profile 0
[    27.272] (**) HID 04f3:0103: (accel) acceleration factor: 2.000
[    27.272] (**) HID 04f3:0103: (accel) acceleration threshold: 4
[    27.273] (II) config/udev: Adding input device  USB OPTICAL MOUSE (/dev/input/event5)
[    27.273] (**)  USB OPTICAL MOUSE: Applying InputClass "evdev pointer catchall"
[    27.273] (II) Using input driver 'evdev' for ' USB OPTICAL MOUSE'
[    27.273] (**)  USB OPTICAL MOUSE: always reports core events
[    27.273] (**) evdev:  USB OPTICAL MOUSE: Device: "/dev/input/event5"
[    27.273] (--) evdev:  USB OPTICAL MOUSE: Vendor 0 Product 0x538
[    27.273] (--) evdev:  USB OPTICAL MOUSE: Found 3 mouse buttons
[    27.273] (--) evdev:  USB OPTICAL MOUSE: Found scroll wheel(s)
[    27.273] (--) evdev:  USB OPTICAL MOUSE: Found relative axes
[    27.273] (--) evdev:  USB OPTICAL MOUSE: Found x and y relative axes
[    27.273] (II) evdev:  USB OPTICAL MOUSE: Configuring as mouse
[    27.273] (II) evdev:  USB OPTICAL MOUSE: Adding scrollwheel support
[    27.273] (**) evdev:  USB OPTICAL MOUSE: YAxisMapping: buttons 4 and 5
[    27.273] (**) evdev:  USB OPTICAL MOUSE: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    27.273] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2.3/1-2.3:1.0/input/input8/event5"
[    27.273] (II) XINPUT: Adding extended input device " USB OPTICAL MOUSE" (type: MOUSE, id 11)
[    27.273] (II) evdev:  USB OPTICAL MOUSE: initialized for relative axes.
[    27.273] (**)  USB OPTICAL MOUSE: (accel) keeping acceleration scheme 1
[    27.273] (**)  USB OPTICAL MOUSE: (accel) acceleration profile 0
[    27.273] (**)  USB OPTICAL MOUSE: (accel) acceleration factor: 2.000
[    27.273] (**)  USB OPTICAL MOUSE: (accel) acceleration threshold: 4
[    27.273] (II) config/udev: Adding input device  USB OPTICAL MOUSE (/dev/input/mouse0)
[    27.273] (II) No input driver specified, ignoring this device.
[    27.273] (II) This device may have been added with another device file.
[    27.273] (II) config/udev: Adding input device USB2.0 Camera (/dev/input/event12)
[    27.273] (**) USB2.0 Camera: Applying InputClass "evdev keyboard catchall"
[    27.273] (II) Using input driver 'evdev' for 'USB2.0 Camera'
[    27.273] (**) USB2.0 Camera: always reports core events
[    27.273] (**) evdev: USB2.0 Camera: Device: "/dev/input/event12"
[    27.273] (--) evdev: USB2.0 Camera: Vendor 0x1e4e Product 0x102
[    27.273] (--) evdev: USB2.0 Camera: Found keys
[    27.273] (II) evdev: USB2.0 Camera: Configuring as keyboard
[    27.273] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2.4/1-2.4:1.0/input/input15/event12"
[    27.273] (II) XINPUT: Adding extended input device "USB2.0 Camera" (type: KEYBOARD, id 12)
[    27.273] (**) Option "xkb_rules" "evdev"
[    27.273] (**) Option "xkb_model" "pc105"
[    27.273] (**) Option "xkb_layout" "gb"
[    27.274] (II) config/udev: Adding input device HD-Audio Generic Front Mic (/dev/input/event11)
[    27.274] (II) No input driver specified, ignoring this device.
[    27.274] (II) This device may have been added with another device file.
[    27.274] (II) config/udev: Adding input device HD-Audio Generic Rear Mic (/dev/input/event10)
[    27.274] (II) No input driver specified, ignoring this device.
[    27.274] (II) This device may have been added with another device file.
[    27.274] (II) config/udev: Adding input device HD-Audio Generic Line (/dev/input/event9)
[    27.274] (II) No input driver specified, ignoring this device.
[    27.274] (II) This device may have been added with another device file.
[    27.274] (II) config/udev: Adding input device HD-Audio Generic Line Out (/dev/input/event8)
[    27.274] (II) No input driver specified, ignoring this device.
[    27.274] (II) This device may have been added with another device file.
[    27.274] (II) config/udev: Adding input device HD-Audio Generic Front Headphone (/dev/input/event7)
[    27.274] (II) No input driver specified, ignoring this device.
[    27.274] (II) This device may have been added with another device file.
[    29.274] (II) XKB: reuse xkmfile /var/lib/xkb/server-11E5978A89165D56F1B4A2145DB8D0A1B3FE4475.xkm
[    29.275] (II) XKB: reuse xkmfile /var/lib/xkb/server-11E5978A89165D56F1B4A2145DB8D0A1B3FE4475.xkm
[    29.425] (II) RADEON(0): EDID vendor "SAM", prod id 2789
[    29.425] (II) RADEON(0): Using EDID range info for horizontal sync
[    29.425] (II) RADEON(0): Using EDID range info for vertical refresh
[    29.425] (II) RADEON(0): Printing DDC gathered Modelines:
[    29.425] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    29.425] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    29.425] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    29.425] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    29.425] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    29.425] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    29.425] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    29.425] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    29.425] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    29.425] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    29.425] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    29.425] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    29.425] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    29.425] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    29.425] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    29.425] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    29.425] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    29.425] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    29.425] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    29.425] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    29.425] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    29.425] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    30.299] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.413] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.416] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.419] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.421] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.423] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.427] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.432] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.434] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.435] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.437] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.439] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.441] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.444] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.446] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.448] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.450] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.452] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.454] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.456] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.458] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.461] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.463] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.465] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.467] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.469] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.471] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.473] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.477] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.479] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.481] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.482] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.484] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.486] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.487] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.489] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.493] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.495] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.496] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.498] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.500] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.501] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.503] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.505] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.507] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.511] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.513] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.515] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.516] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.518] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.520] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.522] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.524] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.528] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.530] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.532] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.534] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.535] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.537] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.539] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.541] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.545] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.547] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.548] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.550] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.552] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.554] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.556] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.558] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.562] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.565] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.568] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.571] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.573] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.574] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.576] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.579] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.580] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.582] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.583] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.585] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.586] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.587] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.589] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.590] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.592] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.595] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.596] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.598] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.599] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.600] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.602] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.603] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.605] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.606] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.609] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.613] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.615] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.617] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.619] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.620] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.622] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.624] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.626] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.629] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.631] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.633] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.635] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.637] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.639] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.641] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.643] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.646] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.648] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.651] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.653] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.655] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.657] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.660] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.663] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.666] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.668] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.670] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.672] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.674] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.676] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.680] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.683] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.685] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.687] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.689] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.691] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.696] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.698] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.700] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.702] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.704] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.706] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.709] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.712] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.714] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.716] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.719] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.721] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.723] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.725] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.729] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.731] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.734] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    30.736] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    31.544] (II) XKB: reuse xkmfile /var/lib/xkb/server-1C26D45DD050810BEE816121A134BE8B55D6AB70.xkm
[    35.773] (II) RADEON(0): EDID vendor "SAM", prod id 2789
[    35.773] (II) RADEON(0): Using hsync ranges from config file
[    35.773] (II) RADEON(0): Using vrefresh ranges from config file
[    35.773] (II) RADEON(0): Printing DDC gathered Modelines:
[    35.773] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    35.773] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    35.773] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    35.773] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    35.774] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    35.774] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    35.774] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    35.774] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    35.774] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    35.774] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    35.774] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    35.774] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    35.774] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    35.774] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    35.774] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    35.774] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    35.774] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    35.774] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    35.774] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    35.774] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    35.774] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    35.774] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    36.016] (II) RADEON(0): Allocate new frame buffer 1680x1056 stride 1696
[    36.040] (II) RADEON(0): VRAM usage limit set to 693723K
[    36.536] (II) RADEON(0): EDID vendor "SAM", prod id 2789
[    36.536] (II) RADEON(0): Using hsync ranges from config file
[    36.536] (II) RADEON(0): Using vrefresh ranges from config file
[    36.536] (II) RADEON(0): Printing DDC gathered Modelines:
[    36.536] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    36.536] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    36.536] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    36.536] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    36.536] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    36.536] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    36.536] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    36.536] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    36.536] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    36.536] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    36.536] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    36.536] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    36.536] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    36.536] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    36.536] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    36.536] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    36.536] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    36.536] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    36.536] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    36.536] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    36.536] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    36.536] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    37.079] (II) XKB: reuse xkmfile /var/lib/xkb/server-B8CD4FE5A1833D7AB4B402792017A55B628FCF2D.xkm
[    37.272] (II) RADEON(0): EDID vendor "SAM", prod id 2789
[    37.272] (II) RADEON(0): Using hsync ranges from config file
[    37.272] (II) RADEON(0): Using vrefresh ranges from config file
[    37.272] (II) RADEON(0): Printing DDC gathered Modelines:
[    37.272] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    37.272] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    37.272] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    37.272] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    37.272] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    37.272] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    37.272] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    37.272] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    37.272] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    37.272] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    37.272] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    37.272] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    37.272] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    37.272] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    37.272] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    37.272] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    37.272] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    37.272] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    37.272] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    37.272] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    37.272] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    37.272] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    37.807] (II) RADEON(0): EDID vendor "SAM", prod id 2789
[    37.807] (II) RADEON(0): Using hsync ranges from config file
[    37.807] (II) RADEON(0): Using vrefresh ranges from config file
[    37.807] (II) RADEON(0): Printing DDC gathered Modelines:
[    37.807] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    37.807] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    37.807] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    37.807] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    37.807] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    37.807] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    37.807] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    37.807] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    37.807] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    37.807] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    37.807] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    37.807] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    37.807] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    37.807] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    37.807] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    37.807] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    37.807] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    37.807] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    37.807] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    37.807] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    37.807] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    37.807] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    38.270] (II) XKB: reuse xkmfile /var/lib/xkb/server-B8CD4FE5A1833D7AB4B402792017A55B628FCF2D.xkm
[    40.903] (II) RADEON(0): EDID vendor "SAM", prod id 2789
[    40.903] (II) RADEON(0): Using hsync ranges from config file
[    40.903] (II) RADEON(0): Using vrefresh ranges from config file
[    40.903] (II) RADEON(0): Printing DDC gathered Modelines:
[    40.903] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    40.903] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    40.903] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    40.903] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    40.903] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    40.903] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    40.903] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    40.903] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    40.903] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    40.903] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    40.903] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    40.903] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    40.903] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    40.903] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    40.903] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    40.903] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    40.903] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    40.903] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    40.904] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    40.904] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    40.904] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    40.904] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    42.405] (II) XKB: reuse xkmfile /var/lib/xkb/server-314DD79035E9F035CB16F21BBDC5087F36438642.xkm
[    53.747] (II) RADEON(0): EDID vendor "SAM", prod id 2789
[    53.747] (II) RADEON(0): Using hsync ranges from config file
[    53.747] (II) RADEON(0): Using vrefresh ranges from config file
[    53.747] (II) RADEON(0): Printing DDC gathered Modelines:
[    53.747] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    53.747] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    53.747] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    53.747] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    53.747] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    53.747] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    53.747] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    53.747] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    53.747] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    53.747] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    53.747] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    53.747] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    53.747] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    53.747] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    53.747] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    53.747] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    53.747] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    53.747] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    53.747] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    53.747] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    53.747] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    53.747] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[   308.251] (II) RADEON(0): EDID vendor "SAM", prod id 2789
[   308.251] (II) RADEON(0): Using hsync ranges from config file
[   308.251] (II) RADEON(0): Using vrefresh ranges from config file
[   308.251] (II) RADEON(0): Printing DDC gathered Modelines:
[   308.251] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[   308.251] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   308.251] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   308.251] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   308.251] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   308.251] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   308.251] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   308.251] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   308.251] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   308.251] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   308.251] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   308.251] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   308.251] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   308.251] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   308.251] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   308.251] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   308.251] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[   308.251] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[   308.251] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   308.251] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[   308.251] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   308.251] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[   695.810] (II) RADEON(0): EDID vendor "SAM", prod id 2789
[   695.810] (II) RADEON(0): Using hsync ranges from config file
[   695.810] (II) RADEON(0): Using vrefresh ranges from config file
[   695.810] (II) RADEON(0): Printing DDC gathered Modelines:
[   695.810] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[   695.810] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   695.810] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   695.810] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   695.810] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   695.810] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   695.810] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   695.810] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   695.810] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   695.810] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   695.810] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   695.810] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   695.810] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   695.810] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   695.810] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   695.810] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   695.810] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[   695.810] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[   695.810] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   695.810] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[   695.810] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   695.810] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[  1908.165] (II) RADEON(0): EDID vendor "SAM", prod id 2789
[  1908.165] (II) RADEON(0): Using hsync ranges from config file
[  1908.165] (II) RADEON(0): Using vrefresh ranges from config file
[  1908.165] (II) RADEON(0): Printing DDC gathered Modelines:
[  1908.165] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  1908.165] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1908.165] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1908.165] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1908.165] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1908.165] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1908.165] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1908.165] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1908.165] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1908.165] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1908.165] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1908.165] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1908.165] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1908.166] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1908.166] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1908.166] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1908.166] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[  1908.166] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[  1908.166] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1908.166] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[  1908.166] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[  1908.166] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
```


Output of command :-   sudo get-edid | parse-edid | edid-decode 

```
mikobuntu@mikobuntu-MS-7721:~$ sudo get-edid | parse-edid | edid-decode This is read-edid version 3.0.1. Prepare for some fun.
Attempting to use i2c interface
Looks like no busses have an EDID. Sorry!
Attempting to use the classical VBE interface


	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
	Function supported
	Call successful


	VBE version 300
	VBE string at 0xc01cc "AMD ATOMBIOS"


VBE/DDC service about to be called
	Report DDC capabilities


	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
	Function supported
	Call successful


	Monitor and video card combination does not support DDC1 transfers
	Monitor and video card combination supports DDC2 transfers
	0 seconds per 128 byte EDID block transfer
	Screen is not blanked during DDC transfer


Reading next EDID block


VBE/DDC service about to be called
	Read EDID


	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call successful


Looks like VBE was successful. Have a good day.
Checksum Correct


Extracted contents:
header:          53 65 63 74 69 6f 6e 20
serial number:   22 4d 6f 6e 69 74 6f 72 22 0a
version:         09 49
basic params:    64 65 6e 74 69
chroma info:     66 69 65 72 20 22 53 32 32 43
established:     31 35 30
standard:        22 0a 09 4d 6f 64 65 6c 4e 61 6d 65 20 22 53 32
descriptor 1:    32 43 31 35 30 22 0a 09 56 65 6e 64 6f 72 4e 61 6d 65
descriptor 2:    20 22 53 41 4d 22 0a 09 23 20 4d 6f 6e 69 74 6f 72 20
descriptor 3:    4d 61 6e 75 66 61 63 74 75 72 65 64 20 77 65 65 6b 20
descriptor 4:    32 30 20 6f 66 20 32 30 31 33 0a 09 23 20 45 44 49 44
extensions:      20
checksum:        76


No header found
Manufacturer: HRM Model 6e6f Serial Number 1919906921
EDID version: 9.73
Analog display, Input voltage level: 0.7/0.7 V
Sync: Composite 
Maximum image size: 101 cm x 110 cm
Gamma: 2.16
DPMS levels: Suspend Off
RGB color display
Supports GTF timings within operating range
Established timings supported:
  640x480@60Hz
  640x480@67Hz
  800x600@60Hz
  832x624@75Hz
  1280x768@87Hz
  1024x768@70Hz
  1280x1024@75Hz
Standard timings supported:
  520x325@70Hz
  320x240@73Hz
  1136x852@96Hz
  1056x792@104Hz
  872x654@93Hz
  1120x840@97Hz
  504x315@94Hz
  912x570@110Hz
Detailed mode: Clock 172.020 MHz, 1135 mm x 3698 mm
                817 1159 1772  870 hborder 97
                 34   56   70 2348 vborder 109
               -hsync +vsync analog composite
Detailed mode: Clock 87.360 MHz, 1902 mm x 1129 mm
               1107 1398 1942 4500 hborder 111
                 34   86  147 2348 vborder 114
               -hsync -vsync analog composite
Detailed mode: Clock 249.090 MHz, 1568 mm x 1399 mm
               1646 2019 2645 3299 hborder 101
               1889 1911 1916 3012 vborder 107
               -hsync -vsync analog composite
Detailed mode: Clock 123.380 MHz, 1059 mm x 1312 mm
               1568 1617 1668 3215 hborder 68
                800  832  858  850 vborder 73
               -hsync +vsync analog composite
Has 32 extension blocks
Checksum: 0x76 (should be 0x23)
EDID block does not conform at all!
	Block has broken checksum
	Bad year of manufacture




```


* Please note that I have been trying all kinds of purging the proprietary FGLXR drivers the past few days, messing with grub settings etc , but so far nothing has changed ( Maybe wont make fixing this bug any easier, but I'm sure someone on the forums will have a solution as always ;)   *


Please let me know if any other info is required and thanks in advance ;)

---

### Post by neu2buntu on 2015-03-20
Good news for me, I tried my set up with a newly acquired HDMI to VGA converter ( which was only a few dollars / pounds ) and now I can access my bios properly without the messed up screen and everything else is now working as expected. This has been bugging me for over 2 years now and money was at a shortage or I would have invested in a new monitor. So i think I can mark this as solved as it seems to be the easiest workaround without having to mess with EDID settings etc. Hopefully this post will at least help someone in the future with a similar setup/problem ;)

---

### Post by neu2buntu on 2015-03-23
update .... I also think I have found the culprit to what was causing my total system lock ups , chromium-browser I havn't had a crash all day since disabling some GPU settings in chromium .I thought I would add this just in case someone was having this freezing issue with radeon graphics ..thanks :)

---

