---
title: "WiFi, Then Boot-Up Problems In Lucid"
date: 2010-08-27
forum: Hardware
---

### Post by calmblythe on 2010-08-27
Hey, guys, I just got my brand new Dell Studio XPS 16 that I've been waiting on for mooonths with the plan of installing Lucid onto it (Dual-booting alongside Win7 Ultimate x64) and everything would be right with the world.

The installation went down without a hitch, but then I noticed that WiFi wasn't working. When I hit the WiFi toggle button, Bluetooth would come on and it works fine (I paired it with my phone), but the option to connect to Wireless Networks is greyed out.

I looked around and tried some fixes in Terminal that I'd seen in different places on the Internet (idr what they were and they're gone now) that didn't fix it. I also installed some updates. I restarted the machine and Ubuntu just wouldn't finish booting up. It would always be stuck at the part with "Ubuntu" and the white dots that gradually become red, but only the first one turns red.
I left it for 10 minutes and still no progress.

After restarting a couple times and getting the same result, I tried repairing, then reformatting the part of the disc with 10.04 and writing over it with a fresh installation (I had to use the advanced disk space allotment feature because the others were either 'write over everything' or 'write alongside everything' -- I told it to reformat the partition with 10.04 and mount 'from /' (first time using the advanced one, btw)).
The installation went fine, as far as I could tell. When I restarted, however, Lucid booted beyond the part with the dots, the screen went blank, then nothing..

Even a fresh installation doesn't work. :(
Do you have any suggestions? 


PS: My laptop connects using an Intel Centrino Advanced-N 6250 AGN.

---

### Post by ptptaylor on 2010-08-27
I don't suppose you installed Ubuntu with WUBI did you?

I had some wireless problems and issues after installing a kernel update with WUBI. 

If it's not that then I'm not sure what the problem is..

---

### Post by calmblythe on 2010-08-27
> **ptptaylor said:**
> I don't suppose you installed Ubuntu with WUBI did you?

I had some wireless problems and issues after installing a kernel update with WUBI.

Yeah, I used Wubi. After the booting up and signing in, I installed some 200+ security and else updates. I'm not sure, exactly, if there was a kernel update, though. I also installed an ATI/AMD proprietary FGLRX graphics driver. It's after installing these, and restarting, that the problems really began.

I found that hitting certain keys (including, maybe limited to, the period (.)) made the boot-up proceed, after stopping on the blank screen.

---

### Post by bcbc on 2010-08-27
If you installed with wubi, then it was on a virtual disk. Reinstalling would have done it on the actual partition. 

Run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results back.

---

### Post by calmblythe on 2010-08-27
Here are the results: 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325    30,800,324    30,720,000   7 HPFS/NTFS
/dev/sda3          30,800,325   616,726,762   585,926,438   7 HPFS/NTFS
/dev/sda4         616,728,574   976,773,119   360,044,546   5 Extended
/dev/sda5         616,728,576   962,082,815   345,354,240  83 Linux
/dev/sda6         962,084,864   976,773,119    14,688,256  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        62424F38424F1069                       ntfs       RECOVERY                      
/dev/sda3        6612514812511E7D                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        bbc9999d-4587-4471-93cd-958dacd01a87   ext4                                     
/dev/sda6        f9b75da3-cc36-487a-872c-f05dbe197f25   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set bbc9999d-4587-4471-93cd-958dacd01a87
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set bbc9999d-4587-4471-93cd-958dacd01a87
set locale_dir=($root)/boot/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set bbc9999d-4587-4471-93cd-958dacd01a87
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=bbc9999d-4587-4471-93cd-958dacd01a87 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set bbc9999d-4587-4471-93cd-958dacd01a87
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=bbc9999d-4587-4471-93cd-958dacd01a87 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set bbc9999d-4587-4471-93cd-958dacd01a87
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set bbc9999d-4587-4471-93cd-958dacd01a87
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 62424f38424f1069
    chainloader +1
}
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
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=bbc9999d-4587-4471-93cd-958dacd01a87 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f9b75da3-cc36-487a-872c-f05dbe197f25 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 423.2GB: boot/grub/core.img
 341.6GB: boot/grub/grub.cfg
 316.8GB: boot/initrd.img-2.6.32-24-generic-pae
 423.2GB: boot/vmlinuz-2.6.32-24-generic-pae
 316.8GB: initrd.img
 423.2GB: vmlinuz
```

---

### Post by bcbc on 2010-08-27
OK so the wubi is gone and now you have a real installation.

What graphics card do you have?

---

### Post by calmblythe on 2010-08-27
I have some experience with Ubu, Mint and openSUSE, but I'm still really novice-y. Can you please explain what you meant by:
> **bcbc said:**
> If you installed with wubi, then it was on a virtual disk. Reinstalling would have done it on the actual partition. 
and 
> **bcbc said:**
> OK so the wubi is gone and now you have a real installation.

As for, 
> **bcbc said:**
> What graphics card do you have?
I have an ATI Mobility Radeon HD 4670, according to Speccy.

---

### Post by bcbc on 2010-08-27
> **calmblythe said:**
> I have some experience with Ubu, Mint and openSUSE, but I'm still really novice-y. Can you please explain what you meant by:
 
and 


As for, 

I have an ATI Mobility Radeon HD 4670, according to Speccy.
You said earlier you installed with wubi - you also described reinstalling but by your description it wasn't a wubi install.

I was just stating that there were no wubi files and that you did in fact have a direct install. Reason being that sometimes you get different advice depending on how you installed.

Anyway - try this link [http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

Maybe booting with xforcevesa will get it booting and then you can look for an ati driver for your graphics card.

You can override like this:
when you see the grub entry, press 'e' to edit, go to where it says 'quiet splash' and add the workaround after that e.g. 'quiet splash xforcevesa' (without quotes). Then CTRL+X to boot.

The F6 option is only for the Live CD workaround.

---

### Post by calmblythe on 2010-08-27
I was browsing through the threads and came across [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475) and learned that the problem I came across after installing the driver is the "Bootup/Plymouth" bug.

About the installation, I think there may have been some miscommunication. I thought Wubi was the name of the installer used to place Ubu in it's own physical partition. Sorry about that.
I hadn't used Wubi at all. I booted from the LiveCD I'd made and installed it from there.

---

### Post by bcbc on 2010-08-27
> **calmblythe said:**
> I was browsing through the threads and came across [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475) and learned that the problem I came across after installing the driver is the "Bootup/Plymouth" bug.

About the installation, I think there may have been some miscommunication. I thought Wubi was the name of the installer used to place Ubu in it's own physical partition. Sorry about that.
I hadn't used Wubi at all. I booted from the LiveCD I'd made and installed it from there.

OK no prob (that's why I asked for the bootinfoscript). I think you're thinking of Ubiquity (the installer).

Did you find a fix to your problems via that link?

---

### Post by calmblythe on 2010-08-27
The link you shared with me -- is it addressing Plymouth or a problem you thought I had as a result of the miscommunication? I'm just wondering, 'cause I'll prob'ly fix the Boot-up/Plymouth thing next time I start up Ubu, even though it's not that much of a problem anymore.

My real concern now is Ubu not being able to use WiFi.

---

### Post by bcbc on 2010-08-27
> **calmblythe said:**
> The link you shared with me -- is it addressing Plymouth or a problem you thought I had as a result of the miscommunication? I'm just wondering, 'cause I'll prob'ly fix the Boot-up/Plymouth thing next time I start up Ubu, even though it's not that much of a problem anymore.

My real concern now is Ubu not being able to use WiFi.

I thought you said you got stuck while booting Ubuntu? Not much point worrying about the wifi if you can't even boot it :)

So, I guess you can boot it now? What wifi card do you have?

---

### Post by calmblythe on 2010-08-27
lol. Yeah, I mentioned earlier that I managed to get by it by pressing some keys.

> I found that hitting certain keys (including, maybe limited to, the period (.)) made the boot-up proceed, after stopping on the blank screen.

Uhm, my laptop connects using an Intel Centrino Advanced-N 6250 AGN.

---

### Post by bcbc on 2010-08-27
> **calmblythe said:**
> lol. Yeah, I mentioned earlier that I managed to get by it by pressing some keys.



Uhm, my laptop connects using an Intel Centrino Advanced-N 6250 AGN.

oh, that's a wireless card, lol

Try this link... [http://ubuntuforums.org/showthread.php?t=1529993](http://ubuntuforums.org/showthread.php?t=1529993) it links to a couple of bugs on launchpad, one of them has a backports library for lucid.

---

### Post by calmblythe on 2010-08-27
Thanks.
I'll read, try 'em out and report back with the results.

---

### Post by calmblythe on 2010-08-28
I tried the backports thing; it didn't seem to work.

---

### Post by bcbc on 2010-08-28
I recommend creating a new post in the networking and wireless subforum. Or adding a post to the other thread. Hopefully someone with more experience will help you.

---

### Post by calmblythe on 2010-08-29
Okay, thanks again for your help.
I'll do that.

---

### Post by calmblythe on 2010-09-05
I found a solution, for those who may stumble across this: [http://ubuntuforums.org/showthread.php?p=9623453&highlight=AGN+6250#post9623453](http://ubuntuforums.org/showthread.php?p=9623453&highlight=AGN+6250#post9623453)

I'll test to see if it lasts, then report back here with my findings.

---

### Post by calmblythe on 2010-09-05
From what I see, The XPS Studio 16 picks up wireless networks now, but it can't connect to them. Also, it appears to be in a static state, so to speak. i.e. Whatever it picks up is stuck as is. So if you move into an area with new networks, they won't register. The ones that were registered at boot-up will remain, reporting whatever signal strength they had at the time [of boot-up].

So, really, my problem hasn't been fixed. :(

---

