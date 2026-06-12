---
title: "Ubuntu dual boot with XP stops my DVD drive working"
date: 2014-09-11
forum: Hardware
---

### Post by Stepehen on 2014-09-11
Basically I have uninstalled and reinstalled Ubuntu 3 times now to make sure it was defiantly installing Ubuntu that made the DVD drive not work. But basically when I uninstall Ubuntu I can use my DVD drive on windows XP, but when I install Ubuntu, I can no longer use my DVD drive and it does not work in XP, so I can't run games or software on XP. Does anyone know how to fix this? 

Thanks

---

### Post by yancek on 2014-09-11
Did the DVD drive work to install Ubuntu or did you use a flash drive to install it?
When you installed Ubuntu, did you try putting a data DVD of some kind in the drive?  Did it work?
What does "does not work" mean?  When you put a data DVD of some kind in the drive what happens?

---

### Post by Stepehen on 2014-09-12
The DVD drive works in ubuntu, and it is in the bios menu, and loads up on start up. It works, it's just not showing on XP. Not showing in Device Manager, or in My computer. But it only happened after I installed Ubuntu, and I am not sure what is going on. I basically just can't use it in XP. But it is working fine, and it worked fine to install Ubuntu.

---

### Post by yancek on 2014-09-12
>  it's just not showing on XP. Not showing in Device Manager,

I'm not sure what you mean by that.  Do you mean that there is no longer a DVD entry/option in your xp Device Manager windows?
Or do you mean that you can not see anythng on the Ubuntu DVD from xp?  windows can't read Linux filesystems so it would not show anything on that DVD.  If you mean you cannot put any DVD whatever is on it and it will not work in xp that's a different problem.  It would be completely illogical for that to happen.  Installing a second operating system on a computer is not going to disable hardware for another system.  The two operating systems are totally separate.  Could you clarify exactly what is happening?

---

### Post by Stepehen on 2014-09-13
> **yancek said:**
> I'm not sure what you mean by that.  Do you mean that there is no longer a DVD entry/option in your xp Device Manager windows?

I mean after installing Ubuntu, when I go back on to XP (as I did a dual boot), I can no longer see the DVD drive in the 'My Computer' File, and when I check Device Manager in XP, no DVD drive is displays. So I can't play games or install any disks in XP. I uninstalled Ubuntu to see if it was ubuntu and it was. I then installed it again to see if it was a one time thing. It did it again hide my DVD drive in XP. So then I uninstalled ubuntu again and then installed it with a different partition hoping that would work and again it has completely hide my dvd drive in XP. The DVD drive works in ubuntu and on boot. But I don't watch DVDs so the only time I need my DVD drive is to burn DVDs, or to install software or to play games. Basically I wanted xp to play games and use some software I am use too, while I got use to how ubuntu works. Plus I don't think linux supports most games yet. Given the games are old, broken sword angel of death for example.

---

### Post by oldfred on 2014-09-13
Are you installing Ubuntu on same drive as XP or another hard drive?
Is system an old IDE with hardware jumpers to set boot device or jumpers for cable-select?
Perhaps adding another boot device is confusing BIOS and cable select options?

---

### Post by Stepehen on 2014-09-13
> **oldfred said:**
> Are you installing Ubuntu on same drive as XP or another hard drive?
Is system an old IDE with hardware jumpers to set boot device or jumpers for cable-select?
Perhaps adding another boot device is confusing BIOS and cable select options?


1. Yes, same drive. 
2. Not sure it is a laptop. It uses IDE cables. Not sure about jumpers.
3. Don't know.

I use XP home, have a GeForce Go 7150 GTX Graphics card, Dual processors 2ghz. 3gb DDR Ram.

---

### Post by oldfred on 2014-09-13
I do not think with a Laptop that IDE should be an issue. 
And installing on same drive should not make any difference at all to system, it is just another operating system.

BIOS enumerates devices and each operating system uses that info on what software drivers to load.

Have you tried booting XP from a total cold boot?
Or shutting down completely, removing battery, holding power switch for a few seconds to remove residual power and boot directly into XP?

Post this, you may want to use code tags as it may be longer. In advanced editor you can easily add tags with # icon.
       cat /boot/grub/grub.cfg

---

### Post by Stepehen on 2014-09-13
Not sure what you mean? I have turned my computer on and then selected XP from the Ubuntu menu, but not sure how I would bypass that menu...

---

### Post by oldfred on 2014-09-13
Post the grub.cfg

It always occurs when you boot XP via grub, but not if you restore the Windows boot loader to MBR (with Ubuntu still installed)?

---

### Post by Stepehen on 2014-09-14
I am really new to ubuntu. What is a Grub.cfg?

---

### Post by Stepehen on 2014-09-14
So I looked in to what the Grub is and found where it is stored, I looked up MBR, and I don't really know how to edit either. I have not done dual booting before or installed linux so it's all new to me.

---

### Post by yancek on 2014-09-14
grub.cfg is  a file in the /boot/grub directory which contains a lot of code as well as the menu you see on boot.  If you look through it, you will a number of lines beginning with the word "menuentry".  After that, you will see the name of the operating system and possible the partition it is on.  Whatever is in quotes after the workd "menuentry" should be what you see on the screen when you boot.

OldFred just asked you to post the contents of this grub.cfg file to look at here.

---

### Post by Stepehen on 2014-09-14
Grub file: 

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
insmod part_msdos
insmod ext2
set root='hd0,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  bb4fc01e-8295-4587-83fc-b3072b2de3e0
else
  search --no-floppy --fs-uuid --set=root bb4fc01e-8295-4587-83fc-b3072b2de3e0
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
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-bb4fc01e-8295-4587-83fc-b3072b2de3e0' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  bb4fc01e-8295-4587-83fc-b3072b2de3e0
    else
      search --no-floppy --fs-uuid --set=root bb4fc01e-8295-4587-83fc-b3072b2de3e0
    fi
    linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=bb4fc01e-8295-4587-83fc-b3072b2de3e0 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-32-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-bb4fc01e-8295-4587-83fc-b3072b2de3e0' {
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-advanced-bb4fc01e-8295-4587-83fc-b3072b2de3e0' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  bb4fc01e-8295-4587-83fc-b3072b2de3e0
        else
          search --no-floppy --fs-uuid --set=root bb4fc01e-8295-4587-83fc-b3072b2de3e0
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=bb4fc01e-8295-4587-83fc-b3072b2de3e0 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-recovery-bb4fc01e-8295-4587-83fc-b3072b2de3e0' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  bb4fc01e-8295-4587-83fc-b3072b2de3e0
        else
          search --no-floppy --fs-uuid --set=root bb4fc01e-8295-4587-83fc-b3072b2de3e0
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=bb4fc01e-8295-4587-83fc-b3072b2de3e0 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  bb4fc01e-8295-4587-83fc-b3072b2de3e0
    else
      search --no-floppy --fs-uuid --set=root bb4fc01e-8295-4587-83fc-b3072b2de3e0
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  bb4fc01e-8295-4587-83fc-b3072b2de3e0
    else
      search --no-floppy --fs-uuid --set=root bb4fc01e-8295-4587-83fc-b3072b2de3e0
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Microsoft Windows XP Home Edition (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-6E9C8E2A9C8DECC1' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  6E9C8E2A9C8DECC1
    else
      search --no-floppy --fs-uuid --set=root 6E9C8E2A9C8DECC1
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
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
```

---

### Post by oldfred on 2014-09-14
Do you only have one Windows install? 
And does it have boot flag. 

When you boot to grub menu and select Windows try manually deleting these two lines and see if it makes any difference. It still should boot XP. Use e and scroll down and just delete lines.
        parttool ${root} hidden-
    drivemap -s (hd0) ${root}

    
The parttool command (I think) is to unhide a NTFS partition that is hidden so you can boot it when another Windows install has boot flag.
The drivemap command is used to tell Windows sda is BIOS boot drive when you boot with grub from sdb or any other drive. BIOS enumerates drives and Windows likes to be first. But whatever drive you boot from with BIOS is always the first drive. If you only have one drive  {root} should also be hd0. But DVD may be enumerated also??

---

### Post by Stepehen on 2014-09-14
I have windows XP home installed. I don't know if it has boot flag. Feel I should know that, but as I said never done dual boot before so not really done much with booting up. How would I check? 

I tried to edit the grub file, but it will not let me. Will not let me change the permissions either. Which I find odd. How do you edit the grub file?

Thanks for explaining. Gives me something to research.

Oh and it's Ubuntu 14.04  32bit.

---

### Post by yancek on 2014-09-14
You can check from Ubuntu to see if the xp partition with boot files is marked as active, has boot flag set.  If you run sudo fdisk -l(lower case Letter L in the command) it will show output similar to below:

```
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT

``` 

The asterisk under boot is what you are looking for.  To edit any grub files which are all system files, you need root privileges, use sudo.  What was suggested was to do a one time edit of the entry.  When you boot, use your arrow keys to scroll down to the xp entry, then hit the e key on your keyboard and mouse to the lines mentioned above and delete the lines referred to.

---

### Post by Stepehen on 2014-09-14
I got this: 

```
   
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   125837144    62918541    7  HPFS/NTFS/exFAT
/dev/sda2       125837310   195371007    34766849    5  Extended
/dev/sda5       125837312   190289919    32226304   83  Linux
/dev/sda6       190291968   195371007     2539520   82  Linux swap / Solaris


```

---

### Post by oldfred on 2014-09-14
You are not supposed to edit grub.cfg, but as you boot you can edit grub directly. That is a one time change, but since just testing that is all you need.

You only have one Windows install and * says it has boot flag.

Use e on grub menu for Windows scroll to edit or remove lines. Then see if that makes any difference.

---

### Post by Stepehen on 2014-09-14
I tried to do what you said, restarted pressed 'e' on the ubuntu boot menu. It takes me to this weird place I don't understand there is no code for the grub file. And I don't see any way to access it, par maybe through the command line, but I don't know any linux commands, as I said I am new to linux and ubuntu. 

What do I do after I press 'e'? I can take a picture and upload it if you wish to see the screen I get.

---

### Post by oldfred on 2014-09-14
If you are on XP line in grub menu as you boot your should just see this:

```
menuentry 'Microsoft Windows XP Home Edition (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-6E9C8E2A9C8DECC1' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  6E9C8E2A9C8DECC1
    else
      search --no-floppy --fs-uuid --set=root 6E9C8E2A9C8DECC1
    fi
    [COLOR=#ff0000]parttool ${root} hidden-
    drivemap -s (hd0) ${root}[/COLOR]
    chainloader +1
}

```

Delete the two lines in red.
Make sure each line is still a separate line

---

### Post by Stepehen on 2014-09-14
Alright, I will restart, and take a picture if it's not that.

---

### Post by Stepehen on 2014-09-14
That isn't what it says on mine. This is what is writen

```
recordfail
load_video
gfxmode $linux_gfx_mode
insmod gzio
insmod part_msdos
indmod ext2
set root='hd0,msdos5'
if [x$feature_platform_search_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  bb4fc0ie-(loads of numbers)
else
    search --no-floppy --fs-uuid --set=root bb4fc0ie-(loads of numbers again)
fi
linux     /boot/vmlinuz-3.13.0-32-generic root=UUID=bb4fc0ie-(loads of numbers again) ro  quiet splash $vt_handoff
initrd     /boot/initrd.img-3.13.0-32-generic
```

Sorry it took so long to reply had to install phone software and get it working so could read the picture.

---

### Post by yancek on 2014-09-14
Your earlier post showed windows on sda1, the output in your last post shows an entry on sda5 and it is the menuentry for Ubuntu on sda5.  That's not what is wanted.  When you boot the machine you will see the Grub boot menu.  You should see an entry for Ubuntu at the top.  There will likely be multiple entries for Ubuntu and also memtest and there should be one for windows xp.  As soon as you see the menu, hit the down arrow key on your keyboard until the entry for windows xp (whatever it's called) is highlighted on the screen.  When that is done, hit the 'e' key on your  keyboard to edit.  The entry you posted is for Ubuntu, not for xp.

---

### Post by Stepehen on 2014-09-14
Oh right. I didn't realise I had to highlight the operating system before I pressed 'e'. Noob mistake. I hate been new, but as is said, everyone starts somewhere, else they don't get any where.

---

### Post by Stepehen on 2014-09-14
Right so I did that, pretty sure I did it right pressed 'e' on XP and then edit them lines out pressed F10 to boot. Did it twice to make sure I didn't make a mistake some how the first time. But DVD drive is still not showing in XP.

---

### Post by oldfred on 2014-09-14
I am running out of ideas of things to try. 
Not seem this type of issue before.

---

### Post by Stepehen on 2014-09-14
Do you think partitioning ubuntu in a different way might work? No swap area? 

I know when I uninstall ubuntu it works on xp. So not sure what is happening?

---

### Post by oldfred on 2014-09-14
I still think it is something related to BIOS and how grub then boots XP.

You could test that by leaving Ubuntu installed but just install a Windows boot loader to MBR. Then system will directly boot Windows. Then restore grub and I expect your issue will be back.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

Is your BIOS the most current version from Vendor. Or is a newer version even available anymore?

---

### Post by Stepehen on 2014-09-14
I don't get why it would be the bios when it worked to install ubuntu and the DVD drive works. If it was the bios surely it would not work to begin with. I think it's something to do with the instillation? Since it works right up to that point I can only assume some how Ubuntu is either taking control over the dvd drive and for some reason this hides it from XP, or that XP is somehow malfunctioning due to another operating system being on the same hard drive and it doesn't know how to share the DVD drive. But as I said it works again after I uninstall ubuntu. But I don't want to do that permanently because I like how stable the internet is and how it never crashes no matter how many tabs I open on the internet browser it just deals with it. Unlike XP which freezes up and crashes. I would like to use Ubuntu in general and xp for games and possible any software I can't find a replacement for.

---

### Post by yancek on 2014-09-14
I can see why you think the way you explain in your last post but because something happened immediately after a prior event, does not mean the prior event caused it.  Operating systems on separate partitions don't take over and control hardware and prevent it being used by another OS.  It's pretty illogical but, I don't know what's happening.   

A possible solution is to get a flash drive and put Ubuntu on it and then you could have the windows bootloader  on your primary drive and Ubuntu on a flash and select the boot device in the BIOS.

---

### Post by Stepehen on 2014-09-15
I know that, however that argument is usually used when there is no correlation. In this case when I uninstall ubuntu the DVD drive instantly works again. So something to do with the instillation is NOT blocking the drive from working. It's doing something which makes the drive not work when XP is loaded up. That is a correlation. As in you can repeatedly test this by uninstalling and reinstalling the drive and watching it go on and off. That is a correlation. The question of why is the real question. For example the theory of gravity works based on evidence, but the real actual underlining cause is still not very well understood. What I am saying is basically this is a result of installing ubuntu. I just don't think its the bios that is the problem. It could be the DVD drive, but I think more likely it's some thing to do with it being shared on one hdd, and like the other operating system can't locate it due to the new settings. 

What happens if I don't have a swap area?

---

### Post by oldfred on 2014-09-15
I am sure just having Ubuntu on drive is not issue. That is not seen by Windows.
I do still think it is grub & BIOS.

I really like yancek's suggestion of moving grub to a flash drive and keeping the XP boot loader on hard drive. That would prove the issue. You then are booting XP directly.

Do you have any flash drives? Does your system boot from a flash drive. Only systems from about 2006 or so will boot from a flash drive. If not we can even create a CD or DVD that boots Ubuntu. Or heaven forbid there is a real complicated way to image the MBR and have Windows boot that image.

---

### Post by Stepehen on 2014-09-15
I don't really want to put it on a flash drive. In the future I plan on buying a new laptop and probable having something like a dual boot with ubuntu or another Linux distro and the latest version of windows. I want to get use to using linux because I have a feeling sooner or later that it will support games and at which point I will probable rarely use windows. If at all. But till then... Given in the future I may have two hard drives on what ever system I get. I would like to learn how to put it on one hard drive as this means the second hard drive would just be storage which means less likely to malfunction due to use. 

But I will try uninstalling it and using no swap area and see what happens.

---

### Post by Stepehen on 2014-09-15
Maybe there is a better solution. The only real reason I want to use XP is to play a game? Is there some way to install and run games on Ubuntu that I am unaware of? And can I get a burner program to burn iso's?

---

### Post by oldfred on 2014-09-15
Ubuntu has a built in DVD burner, brasero. I prefer the one that comes with Kubuntu, K3b which I just install to my Ubuntu.

Some games can be played with wine, but wine often only partially works for Windows applications.

I do not game, but Steam is now available for Linux, but only some titles. Generally to run those games you need a new system with higher end video card. You almost then always want the proprietary driver for speed.
[http://www.phoronix.com/scan.php?page=article&item=valve_source_march2014&num=1](http://www.phoronix.com/scan.php?page=article&item=valve_source_march2014&num=1)
Unvanquished with open source video
[http://www.phoronix.com/scan.php?page=article&item=unvanquished_026&num=1](http://www.phoronix.com/scan.php?page=article&item=unvanquished_026&num=1)

---

