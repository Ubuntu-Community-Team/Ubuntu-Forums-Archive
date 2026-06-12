---
title: "Help using two OS on two HD"
date: 2010-06-21
forum: Hardware
---

### Post by JoshuaaXD on 2010-06-21
Hi, I've been using Ubuntu 9.10 on a single hard drive and I don't have any other OS on it, I recently picked up another HD and it has Windows XP pro on it. When I had the two operating systems on a single hard drive on start up I was given a choice between Windows and Ubuntu, I have both hard drive hooked up currently and I wasn't able to choose between the operating systems. Can someone offer a solution?

---

### Post by mikewhatever on 2010-06-21
You'll need to add a custom Windows entry to Grub. Let's start by you posting the output of **sudo fdisk -l**.

---

### Post by wilee-nilee on 2010-06-21
> **JoshuaaXD said:**
> Hi, I've been using Ubuntu 9.10 on a single hard drive and I don't have any other OS on it, I recently picked up another HD and it has Windows XP pro on it. When I had the two operating systems on a single hard drive on start up I was given a choice between Windows and Ubuntu, I have both hard drive hooked up currently and I wasn't able to choose between the operating systems. Can someone offer a solution?

In the terminal in Ubuntu, if your using grub2
```
sudo update-grub
```
If this doesn't fix it post the bootscript in my signature in code tags.

---

### Post by JoshuaaXD on 2010-06-21
> **wilee-nilee said:**
> In the terminal in Ubuntu, if your using grub2
```
sudo update-grub
```If this doesn't fix it post the bootscript in my signature in code tags.

Okay that seem promising I'll restart and see what happens =]

```
joshua@joshua-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-22-generic
Found initrd image: /boot/initrd.img-2.6.31-22-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sdb1
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

done

```

---

### Post by JoshuaaXD on 2010-06-21
Okay I updated grub and restarted the computer, my second hard drive with windows on it was recognized and when I cam to start it with that I got a screen saying Error: Invalid Signature

I'll try figuring out what to do with whats in your signature wilee-nilee.

---

### Post by wilee-nilee on 2010-06-21
> **JoshuaaXD said:**
> Okay I updated grub and restarted the computer, my second hard drive with windows on it was recognized and when I cam to start it with that I got a screen saying Error: Invalid Signature

I'll try figuring out what to do with whats in your signature wilee-nilee.

mikewhatever may be correct with editing grub but post the bootscript first, I think it is simpler then that probably.

---

### Post by JoshuaaXD on 2010-06-21
I loaded the script these are the results, no progress. I'm thinking it is a problem within windows, the hard drive is from another computer and that computer is a great deal weaker and every single peice of hardware on it is different than what I have on my Linux machine. I wouldn't know if that would affect me being able to just hook up its hard drive to my machine.

```
         Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 8192.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x09b009b0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   153,324,359   153,324,297  83 Linux
/dev/sda2         153,324,360   156,296,384     2,972,025   5 Extended
/dev/sda5         153,324,423   156,296,384     2,971,962  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa286a286

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    39,086,144    39,086,082   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 3965 MB, 3965190144 bytes
49 heads, 48 sectors/track, 3292 cylinders, total 7744512 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               8,192     7,744,511     7,736,320   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4f9b372d-f079-4552-9604-c46e4230fd23   ext4                                     
/dev/sda5        9c278b18-4951-4ad5-ada8-b7d862d7b903   swap                                     
/dev/sdb1        42748A4B748A4221                       ntfs                                     
/dev/sdc1        0812-004B                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/0812-004B         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 4f9b372d-f079-4552-9604-c46e4230fd23
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
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4f9b372d-f079-4552-9604-c46e4230fd23
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=4f9b372d-f079-4552-9604-c46e4230fd23 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4f9b372d-f079-4552-9604-c46e4230fd23
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=4f9b372d-f079-4552-9604-c46e4230fd23 ro single 
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4f9b372d-f079-4552-9604-c46e4230fd23
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=4f9b372d-f079-4552-9604-c46e4230fd23 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4f9b372d-f079-4552-9604-c46e4230fd23
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=4f9b372d-f079-4552-9604-c46e4230fd23 ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=4f9b372d-f079-4552-9604-c46e4230fd23 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9c278b18-4951-4ad5-ada8-b7d862d7b903 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   6.2GB: boot/grub/core.img
   4.7GB: boot/grub/grub.cfg
    .2GB: boot/initrd.img-2.6.31-14-generic
    .3GB: boot/initrd.img-2.6.31-22-generic
    .2GB: boot/vmlinuz-2.6.31-14-generic
    .2GB: boot/vmlinuz-2.6.31-22-generic
    .3GB: initrd.img
    .2GB: initrd.img.old
    .2GB: vmlinuz
    .2GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

I tried Mikewhatever's solution and I got this

```
joshua@joshua-desktop:~$ sudo fdisk /dev/sdb1

The number of cylinders for this disk is set to 2432.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

```

---

### Post by wilee-nilee on 2010-06-21
First I would use the key prompt to choose the HD to boot from, mine is f12 and see if XP even boots. The fdisk read out is suspicious for sure if it is true. That XP could at the least have a rootkit in it, and who knows what else. Some rootkits can't even be found.

---

### Post by JoshuaaXD on 2010-06-21
Tried that, I get the Windows XP screen saying there was a problem shutting down and giving me choices of starting in safe mode, last working config, start normally and all that good stuff. I tried starting it normally and the screen went blank and the computer restarted, I tried with last working configuration and it went blank and restarted, I even tried running it on safe mode and had the same result. I give up lol I'll just put the HD back into it's tired machine haha, it just would have been nice to have Windows on my current machine along with Ubuntu for daily use. Every time I had the two on the same HD one or the other would fail haha.

---

### Post by mikewhatever on 2010-06-21
Try this:
```
gksudo gedit /boot/grub/device.map
```

add the following line, save and exit.
```
(hd1)  /dev/sdb
```

then run
```
sudo update grub
```

---

### Post by wilee-nilee on 2010-06-21
> **JoshuaaXD said:**
> Tried that, I get the Windows XP screen saying there was a problem shutting down and giving me choices of starting in safe mode, last working config, start normally and all that good stuff. I tried starting it normally and the screen went blank and the computer restarted, I tried with last working configuration and it went blank and restarted, I even tried running it on safe mode and had the same result. I give up lol I'll just put the HD back into it's tired machine haha, it just would have been nice to have Windows on my current machine along with Ubuntu for daily use. Every time I had the two on the same HD one or the other would fail haha.

Here is a link to a XP cd so you could get in to run a chkdsk c: /f /r in repair if you want to mess with it.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

We are assuming that the c: location is correct look on Google or ask more questions if this doesn't make sense.

---

### Post by wilee-nilee on 2010-06-21
> **mikewhatever said:**
> Try this:
```
gksudo gedit /boot/grub/device.map
```

add the following line, save and exit.
```
(hd1)  /dev/sdb
```

then run
```
sudo update grub
```

He can boot it from the HD it is corrupted.

---

### Post by mikewhatever on 2010-06-21
wilee-nilee, you must be seeing something that I don't. Care to explain?

---

### Post by wilee-nilee on 2010-06-21
> **mikewhatever said:**
> wilee-nilee, you must be seeing something that I don't. Care to explain?

I'm just going by this, after the OP booted from the HD.
> Tried that, I get the Windows XP screen saying there was a problem shutting down and giving me choices of starting in safe mode, last working config, start normally and all that good stuff. I tried starting it normally and the screen went blank and the computer restarted, I tried with last working configuration and it went blank and restarted, I even tried running it on safe mode and had the same result. I give up lol I'll just put the HD back into it's tired machine haha, it just would have been nice to have Windows on my current machine along with Ubuntu for daily use. Every time I had the two on the same HD one or the other would fail haha.

I think it is bootable, but is corrupted that is why I gave the link to a XP ISO which is a legit download and suggested the chkdsk options.

I suspect that the XP is messed up we haven't been able to get a response of it works okay on the original computer that would be a good start.

There is also the fdisk that says that it may not even boot from another OS, but this could be wrong. But the fact that it boots but won't even get through a safe start is strange, and a chkdsk can be run from a install disc where it should always be run from really.

---

### Post by DillyT33 on 2010-06-21
Well hey, even if you don't get Win XP to work off the HD. Just put it back in the old machine. 

Format it in Cmd. 

And then pop it back into your Linux machine.

A little extra memory couldn't hurt.

And it's not that hard to find a copy of XP from somewhere. Then just install it on the new HD and dual boot.

Good luck either way!

=)

---

### Post by DillyT33 on 2010-06-21
Well hey, even if you don't get Win XP to work off the HD. Just put it back in the old machine. 

Format it in Cmd. 

And then pop it back into your Linux machine.

A little extra memory couldn't hurt.

And it's not that hard to find a copy of XP from somewhere. Then just install it on the new HD and dual boot.

Good luck either way!

:)

---

### Post by wilee-nilee on 2010-06-21
> **DillyT33 said:**
> Well hey, even if you don't get Win XP to work off the HD. Just put it back in the old machine. 

Format it in Cmd. 

And then pop it back into your Linux machine.

A little extra memory couldn't hurt.

And it's not that hard to find a copy of XP from somewhere. Then just install it on the new HD and dual boot.

Good luck either way!

=)

You have to have a activate key to keep it going. And be careful of suggesting otherwise any other method is not supported on the forum.

---

### Post by mikewhatever on 2010-06-21
wilee-nilee, thanks, I missed that post.

---

### Post by oldfred on 2010-06-22
the grub boot stanza is incomplete. The osprober usually inserts a correct entry with windows so there may be another problem but I would try a custom entry (or two) to see if it works.

Missing set root = command which is essential:
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    drivemap -s (hd0) ${root}
    chainloader +1
}

Possible better double check that I put in correct UUID:
menuentry "Windows XP Pro (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 42748A4B748A4221 
    drivemap -s (hd0) ${root}
    chainloader +1
}

If you directly boot windows from The BIOS does it boot? I would expect that it should. You can just use the one time boot key rather than change BIOS.

I still do not know if the drivemap command needs hd1 or hd0 when the {root} is used. I think {root} is the variable that is set by set root so it should be hd1 and you want swap with hd0, but it may be 
    drivemap -s (hd1) ${root}
You can try one and then when booting if it does not work use e to edit and scroll down and change to the other as a test.

copy above stanza to 40_custom and run sudo update-grub
gksudo gedit /etc/grub.d/40_custom

---

### Post by wilee-nilee on 2010-06-22
I guess he tried the boot from the HD and couldn't get it to boot, in any mode including safe. I don't know if the boot from bios is any different. I put the XP ISO link in and thought that if they could get in the chkdsk /r/f might get it at least so it would boot,from the HD then grub could be worked with

---

### Post by JoshuaaXD on 2010-06-22
Sorry I haven't been my linux machine, I had taken the hard drive out of my linux machine and put it back into it's original case. I decided to live with the inconvenience of switching computers if I needed to since I only have one monitor, keyboard, mouse, power cord, ect. I'll go back and work from the next suggestions tomorrow. The hard drive boots and runs perfectly on the machine that it came in, but for some reason it won't run on my machine, it originally ran windows and I've had linux and windows on it at different times I know it will run windows and it runs it better than Ubuntu. Before I asked for help on the forums I thought I would just be able to put the HD with Windows into my computer and have that as the master harddrive and when I have that on I would take my hard drive with ubuntu have it in as the secondary hd wipe it and then install Ubuntu onto the secondary drive. It seemed start forward and I actually did basically the same thing last week only both hard drives were going to have Ubuntu (don't ask why). When I hooked up the Windows Hard Drive on its own to my machine I got the screen saying windows didn't shut down properly and did the same things I did later on and ended up with the computer restarting every time I chose an option even in safe mode.

I only want to have windows on my computer because I do have a need for it at times, everyone does. I have a windows mobile phone and I have a zune. Unfortunately Microsoft doesn't want to recognise there are people that prefer to use other operating systems than windows. I have a clean copy of windows XP pro, it is at my dad's house and I would need to pick it up so I either wipe the drive put it on my machine and install a new and clean version or I try to get the drive working how it is now.

---

### Post by JoshuaaXD on 2010-06-22
> **wilee-nilee said:**
> I'm just going by this, after the OP booted from the HD.
I suspect that the XP is messed up we haven't been able to get a response of it works okay on the original computer that would be a good start.


Yes it boots just fine from the original computer that is why I haven't been on to reply I've been too busy downloading programs I need and talking myspace haha

> **DillyT33 said:**
> Well hey, even if you don't get Win XP to work off the HD. Just put it back in the old machine. 

Format it in Cmd. 

And then pop it back into your Linux machine.

A little extra memory couldn't hurt.

And it's not that hard to find a copy of XP from somewhere. Then just install it on the new HD and dual boot.

Good luck either way!

=)
I would end up with an extra 20gb of memory giving me 100 total gb lol, I feel like that is overkill, it's ironic because I'm thinking about upgrading the HD in my ps3 to 500gb haha

> **oldfred said:**
> 
If you directly boot windows from The BIOS does it boot? I would expect that it should. You can just use the one time boot key rather than change BIOS.

I am not even going to touch BIOS I would be too afraid to change something that wasn't supposed to be changed, I'm not that knowledgeable of computers to do that. I know how to build a computer, get it running, and fix basic problems.

---

