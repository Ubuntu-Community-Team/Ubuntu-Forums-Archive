---
title: "Dualboot system only starts in Ubuntu"
date: 2006-01-10
forum: Installation &amp; Upgrades
---

### Post by jimmp226 on 2006-01-10
Here's my problem. I installed Ubuntu on my lap top in a dual boot system with Windows XP. I reinstalled windows and left a 17gb partition for Ubuntu. According to Windows C:Ubuntu  D:WindowsXP. I then installed Ubuntu in that partition. Ubutu lists Windows at:hda5  and Ubuntu at:hda6. When I restart my computer a window appears that will let me choose witch operating system to load. If I choose Windows I get an error code that says: this partition does not exist. I can not load into Windows from there. I have to load Ubuntu. Any ideas?
Thanks in advance. Jim

---

### Post by Sef on 2006-01-10
This is from Ubuntu's FAQ Guide:

8.7.	

How to add Windows entry into GRUB menu?

If you need to reinstall GRUB, read How do I check disk space and view the partition table? 

Launch System->Administration->Boot 

Click on Add. 

Choose a name such as "Windows XP" and the OS type is unknown. 

Assuming that /dev/hda1 is the location of Windows partition, choose that from the drop-down list

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-rescuemode]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-rescuemode")

I hope this works for you.  It could if the problem is is that GRUB is simply not seeing the Windows partition.

---

### Post by jimmp226 on 2006-01-10
Thanks Sef. Windows is located at hda5 on the hard drive.

Launch  System->Administration-> there is nothing like boot to click on.

I'm still stuck? Jim

---

### Post by ingram on 2006-01-10
I had a similar problem, it turned out I needed to use parted to make it so that the windows partition was not hidden.

---

### Post by jimmp226 on 2006-01-10
Ingram what is "parted"? I'm pretty new at this and have never heard of this. Thanks. Jim

---

### Post by jimmp226 on 2006-01-11
BTT-   Sorry to do this but I'm still stuck. Still cant get Windows to start. If I cant get this working today I'm going to wipe the disk and stick with Windows only. I need to get my computer running with or without Ubuntu. Thanks in advance. Jim

---

### Post by J77 on 2006-01-11
Why not wipe everything, stick on windows in a partition 1/3 of your hd leaving the rest free. Then install ubuntu in the free space - worked fine for me: [http://ubuntuforums.org/showthread.php?p=644696#post644696](http://ubuntuforums.org/showthread.php?p=644696#post644696)

J77 :)

---

### Post by jimmp226 on 2006-01-11
I allready did that. I have a 60gb hard drive. I left C: witha a 17 gb partition for Ubuntu and put Windows in D: a 43gb partition. According to Ubuntu Windows is in hda5 if that helps. This is the 4th time I've done this and this is as far as I have gotten so far so it's getting better (at least thats what I keep telling my self lol). Thanks in advance. Jim

---

### Post by J77 on 2006-01-11
[QUOTE=jimmp226]I allready did that. I have a 60gb hard drive. I left C: witha a 17 gb partition for Ubuntu and put Windows in D: a 43gb partition. According to Ubuntu Windows is in hda5 if that helps. This is the 4th time I've done this and this is as far as I have gotten so far so it's getting better (at least thats what I keep telling my self lol). Thanks in advance. Jim[/QUOTE]I'm only guessing, but did you repartition the free space you set aside for ubuntu as I detail in the link in my post above?

You may need space for /boot which the auto-partitioning of ubuntu doesn't provide?

J77

---

### Post by jimmp226 on 2006-01-11
No I did not. I setup a 800mb partition as a swap file and the rest went to Ubuntu no /boot partition. Any ideas? Thanks. Jim

---

### Post by J77 on 2006-01-11
[QUOTE=jimmp226]No I did not. I setup a 800mb partition as a swap file and the rest went to Ubuntu no /boot partition. Any ideas? Thanks. Jim[/QUOTE]You may want to set up a /boot parttion on your next run then. Again check out my set-up here: [http://ubuntuforums.org/showthread.php?p=644696#post644696](http://ubuntuforums.org/showthread.php?p=644696#post644696)

Like I said somewhere else tho' - I'm no expert, just finding stuff out as I go along...

:)

Also - that /boot partion of mine is the only one designated as 'primary'

---

### Post by Kipper on 2006-01-11
Hello, what's your current satus. Can you still boot into Ubuntu but not Windows?

I need you to post the follwing things here so I can see what the current layout of your partitions are, and what GRUB is trying to do.

Firsty find the file "menu.lst" which should be in /boot/grub and list is contents here. ( **sudo cat /boot/grub/menu.lst** might do it)

Secondly to see the partitions on your hard drive do,  **sudo fdisk -l /dev/hda**. The "-l" is a minus sign followed by a lowercase leter "L" NOT the number one. Post the output of the command here.

What I suspect is happening is that you have installed Ubunutu ahead of Windows on your hard drive and Windows likes to live in the first primary partition of your hard drive, Windows drive C, hence you cannot boot Windows right now. If, this turns out to be the case it may be possible to use an entry in the "menu.lst" file to trick Windows into thinking its in the right place.

---

### Post by jimmp226 on 2006-01-11
Hi Kipper thanks for the help. Ubuntu is installed ahead of Windows in the   C: partition  Windows is installed in the   D: partition lst me know if you still need the menu.list and fdisk. Thanks . Jim

---

### Post by jimmp226 on 2006-01-11
Here's the menu.lst you requested.

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        20

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title        Ubuntu, kernel 2.6.12-10-386
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.12-10-386 root=/dev/hda6 ro quiet splash
initrd        /boot/initrd.img-2.6.12-10-386
savedefault
boot

title        Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.12-10-386 root=/dev/hda6 ro single
initrd        /boot/initrd.img-2.6.12-10-386
boot

title        Ubuntu, kernel 2.6.12-9-386
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.12-9-386 root=/dev/hda6 ro quiet splash
initrd        /boot/initrd.img-2.6.12-9-386
savedefault
boot

title        Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.12-9-386 root=/dev/hda6 ro single
initrd        /boot/initrd.img-2.6.12-9-386
boot

title        Ubuntu, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows
root        (hd0,4)
savedefault
makeactive
chainloader    +1

---

### Post by Kipper on 2006-01-11
Thanks for that, but I still need so see the partitions as listed by the fdisk command.

---

### Post by jimmp226 on 2006-01-11
Heres the fdisk information you also asked for. Thanks again. Jim


Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2               1        7296    58605088+   f  W95 Ext'd (LBA)
/dev/hda5            2168        7296    41198661    7  HPFS/NTFS
/dev/hda6               1        2067    16603083   83  Linux
/dev/hda7            2068        2167      803218+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by Kipper on 2006-01-11
While I'm waiting for confirmation of your current partitions, try this for your "Windows" section in the "menu.lst" file. 

Replace: 

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows
root (hd0,4)
savedefault
makeactive
chainloader +1

With this:

#MICROSOFT (MS) on first drive and NON-FIRST partition
 title MS on NON-FIRST partition
 root (hd0,4)
 map (hd0,4) (hd0,0)
 map (hd0,0) (hd0,4)
 makeactive
 chainloader +1

Let me know if that fixes it.

---

### Post by Kipper on 2006-01-11
Thanks for your partition table entries, but what did you use to generate that list? Linux "fdisk" is better.

Your first partition /dev/dha1 appears to be hidden and I suspect is a primary partition. Somehow you have ended up with Windows in a logical partition inside your extended partition. This has totally foxed Windows. GRUB may still be able to boot it though. 

When you use an extended partition, which is just a container for your logical partitions, the Linux number jumps from 2 to 5. This does not mean you have lost two partitions, /devhda3 and /dev/hda4 don't exist.

---

### Post by jimmp226 on 2006-01-11
OK KIpper I'm trying to keep up here. I changed the entry in menu.lst and restarted my computer. At the point where you decide which operating system and click on Windows I get:

    "Booting 'Microsoft Windows'

root      (hda0,4)
 Filesystem type unknown, partition type 0x7
savedefault
makeactive

Error 12: Invalid device requested

Press any key to continue"

I used     sudo fdisk -l /dev/hda
I think I entered it right if not let me know where to get the right information.
Thanks a hole bunch for the help. Jim

---

### Post by Kipper on 2006-01-11
As they say, "That's a dual-boot system Jim, but not as we know it". Ok let's see is we can go where the stars are all glowy. I must stop smoking this stuf...

After my last post I had another thought. That hidden partition could be what your initial Winodws install was using to boot from, whereas /dev/hda5 is where all the WindowsXP progs/data lives. 

If this is true then the Windows section of the "menu.lst" file could be this:

title Microsoft Windows
unhide (hd0,0)
root (hd0,0)
savedefault
makeactive
chainloader +1

Give it shot.

---

### Post by jimmp226 on 2006-01-11
OK Kipper I changed menu.lst like you said and restarted the computer. Trying to get Windows to run I get this message:


     Booting 'Microsoft Windows'

unhide    (hd0,0)
root       (hd0,0)

Error 22:   No Such Partition


Hopes this helpsand thanks again. Jim

---

### Post by Kipper on 2006-01-11
Ok, exaclty how was WinXP installed in the first case? Was it installed before Ubuntu? Was it pre-installed on your system? If you installed it yourself, did you just use the Window InstallCD's to partition and format your disc or did you use a pre-exisitng system and other partitioning software before installing WinXP?

Right now, I don't know how to boot your Windows system wiht GRUB. This hidden partition has me scratching my head.

Re-installing everything is a last resort, but I would think you have data on your  NTFS partition you want to keep. It might be just a case of going through the WInXP recovery process to make WinXP bootable again, but then you have to mess around to get back inot Linux. What's your priority?

---

### Post by jimmp226 on 2006-01-11
I reindtalled Windows myself. I used the partition utillity on the Windows Install disk. The first partition I left blank in FAT32. Then I made a partition in NTFS windows. I need Windows alot more than Ubuntu. I mainly installed Ubuntu to learn about Linux systems, everything is in Windows. I can reinstall either operating system at this point it's just a matter of time you know. Again thank you for all your help Kipper I have no idea as to what I'm doing?

---

### Post by Kipper on 2006-01-11
Jim,

Hang in there. Re-installing is a last resort. We know we can get that to work. But If you can work your way through the WinXP recovery process via the WinXP install disk then at least your Windows will be up and running and perhaps  we can reinstall and sort out Linux after that.

On the other hand, if you feel re-installing WinXP is the way you want to go, I would strongly recommend you choose a more starightforward partition scheme for WinXP. Make the first WinXp partition NTFS (drive C), make a second partiton FAT32 (drive D) - it can be shared read/write with Linux. Make sure you Install WinXP on drive C.

Then when you install Ubuntu it should recognise this as a pretty standard layout.

---

### Post by lha on 2006-01-12
[QUOTE=jimmp226]Heres the fdisk information you also asked for. Thanks again. Jim


Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2               1        7296    58605088+   f  W95 Ext'd (LBA)
/dev/hda5            2168        7296    41198661    7  HPFS/NTFS
/dev/hda6               1        2067    16603083   83  Linux
/dev/hda7            2068        2167      803218+  82  Linux swap / Solaris

Partition table entries are not in disk order[/QUOTE]

[QUOTE=jimmp226]I reindtalled Windows myself. I used the partition utillity on the Windows Install disk. The first partition I left blank in FAT32. Then I made a partition in NTFS windows. I need Windows alot more than Ubuntu. I mainly installed Ubuntu to learn about Linux systems, everything is in Windows. I can reinstall either operating system at this point it's just a matter of time you know. Again thank you for all your help Kipper I have no idea as to what I'm doing?
[/QUOTE]

You say you partitioned your drive in two before installing Windows. I presume it's partition table looked like

```
hda1       1 - 2167    fat32    17GB
hda2    2168 - 7296    extended
|-hda5  2168 - 7296    ntfs     40GB
```

Now it's this
```
hda2       1 - 7296    extended
|-hda6     1 - 2067    Linux      16GB
|-hda7  2068 - 2167    Linux swap .7GB
|-hda5  2168 - 7296    ntfs       40GB
```

This means you don't have that fat32 partition anymore. You have deleted it during install and enlargened your extended partition to cover whole hd. Then you have created hda6 and hda7 for Ubuntu. I do hope you have backups if you had important files on fat partition. :( 

At the moment, you don't have any primary partitions. This situation is not trivial to fix. It is not a problem for Linux, but Windows really likes to be on a primary partition. Windows' boot loader was on hda1 as Windows always installs it into the first primary partition it sees. By removing hda1 you also vaporized ntldr. You may have all your data intact on hda5 (ntfs partition) but without ntldr (Windows' boot loader) you can't boot Windows. There's also another problem. Windows wants logical partitions to be in order. You have hda6 and hda7 before hda5. Again, not a problem for Linux but Windows may run into troubles with this, eg refuse to read logical partitions.

Reinstalling might not be a bad idea at all.

---

### Post by Kipper on 2006-01-12
Ouch, Lha, your are hard on the man, But you are right. I'm stupid I didn't look at those numbers hard enough. The first partition appears to have been zapped. 

A re-install is all that's left to get WinXP up and running.

---

### Post by jimmp226 on 2006-01-12
Holy Dual Boot Batman. I got it to work I just needed to reinstall everything. The problem was that partition. Thanks everyone for all the help I really appericiate it.
I still dont know what I'm doing with Linux so I'll be prowling the forum for any ideas. Again thank's for all the help. Jim

---

### Post by Kipper on 2006-01-13
Another happy penguin, brilliant! There's a million and one websites with stuff about Linux, and plenty of forums like this. You'll soon be a Linux junkie :p

---

### Post by Topsiho on 2006-01-13
I noticed that Windows is in partition hda5. That is a logical partition.

If I am correct (I am not sure of this) Windows must be in a primary partition, that is hda1 to hda4. Maybe it even has to sit in hda1, where it resides after installing Windows first on an empty disk.

If this is correct than you have to reinstall Windows in hda1

I have to do a small explanation here: a disk can be divided into partitions. There are at most 4 primary partitions possible: hda1 to hda4. If more partitions are necessary one should make 1 or more extended partitions which can be subdivided into logical partitions. Those are the partitions hda5, hda6 etc.

So please repartition your disk along these lines and install windows in hda1, and all will be OK I suppose.

The partitioning may be done when installing Ubuntu (manual install), and when Ubuntu is installed you can use gparted (sudo apt-get install gparted) which is a look-alike of the Windows program PartitionMagic (which you could also use after first installing Windows, of course, only it costs you more :) )

Hope this helps,

Topsiho

---

