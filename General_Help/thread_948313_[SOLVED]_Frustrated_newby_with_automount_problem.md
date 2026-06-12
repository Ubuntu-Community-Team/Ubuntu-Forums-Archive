---
title: "[SOLVED] Frustrated newby with automount problem"
date: 2008-10-15
forum: General Help
---

### Post by eels68 on 2008-10-15
HI.

**Problem :** My USB Thumb drive and External Hard drive don't automount.

**Strange happenings :** They do mount if plugged in and turned on before system start up (thats is If I plug in my thumb drive and/or turn on my external hard drive before turning on my system they will be mounted)
          They, also, do mount themselves after I type "lsusb" in the terminal screen. (It seems to wake them up - so to speak)

**Further information :** I have no problem with these devices automounting on my wifes computer, She is running the same as me, Ubuntu 8.04.1 LTS Desktop Edition (plus any upgrades etc that the system wanted done)
There is no problem with the USB ports and the BIOS has all the USB functions enabled.

I must mention that I am new to both LINUX and UBUNTU (about 2 weeks now) and that any suggestions be typed out in a idiot friendly way :) 
I have taken the liberty to providing the following information to help those who can help me. 

**_These were done with my thumb drive plugged in but unmounted._**



*_I typed in "dmesg | tail" and got this:_*

rob@rob-desktop:~$ dmesg | tail
[ 1118.832021] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 1118.833635] sd 5:0:0:0: [sdc] 390721969 512-byte hardware sectors (200050 MB)
[ 1118.834500] sd 5:0:0:0: [sdc] Write Protect is off
[ 1118.834506] sd 5:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 1118.834510] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 1118.834517]  sdc: sdc1
[ 1118.854507] sd 5:0:0:0: [sdc] Attached SCSI disk
[ 1118.854577] sd 5:0:0:0: Attached scsi generic sg3 type 0
[ 1118.958305] sd 5:0:0:0: [sdc] Sense Key : No Sense [current] 
[ 1118.958322] sd 5:0:0:0: [sdc] Add. Sense: No additional sense information



*_After typing "sudo fdisk -l" I got:_*

rob@rob-desktop:~$ sudo fdisk -l
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9349    75095811   83  Linux
/dev/sda2            9350        9726     3028252+   5  Extended
/dev/sda5            9350        9726     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00008002

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    7  HPFS/NTFS




*_After typing "cat /etc/fstab" I got:_*

rob@rob-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=99dafdfc-8501-4b28-b008-bc69749bdfc2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=baef4df9-93f1-4348-965d-55cf0044352b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0      0



After typing "lsusb" Igot:

rob@rob-desktop:~$ lsusb
Bus 005 Device 004: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 046d:c30a Logitech, Inc. 
Bus 001 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  


**_The following was done with my thumb drive in and mounted._**


_"dsmeg | tail"_

rob@rob-desktop:~$ dmesg | tail
[ 5193.302958] sd 6:0:0:0: [sdc] Write Protect is off
[ 5193.302964] sd 6:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 5193.302969] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 5193.306445] sd 6:0:0:0: [sdc] 7830528 512-byte hardware sectors (4009 MB)
[ 5193.307193] sd 6:0:0:0: [sdc] Write Protect is off
[ 5193.307199] sd 6:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 5193.307203] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 5193.307208]  sdc: sdc1
[ 5193.349815] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[ 5193.349880] sd 6:0:0:0: Attached scsi generic sg3 type 0



_"sudo fdisk -l"_

rob@rob-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9349    75095811   83  Linux
/dev/sda2            9350        9726     3028252+   5  Extended
/dev/sda5            9350        9726     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00008002

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdc: 4009 MB, 4009230336 bytes
16 heads, 32 sectors/track, 15294 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       15294     3915248    b  W95 FAT32



_"cat /etc/fstab"_

rob@rob-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=99dafdfc-8501-4b28-b008-bc69749bdfc2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=baef4df9-93f1-4348-965d-55cf0044352b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



_"lsusb"_

rob@rob-desktop:~$ lsusb
Bus 005 Device 007: ID 0930:6545 Toshiba Corp. 
Bus 005 Device 004: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 046d:c30a Logitech, Inc. 
Bus 001 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  


I thank anyone who can help me. I also hope that I have provided enough information - likewise I hope I didn't over do it.

Have a nice day.

---

### Post by marshall.robert on 2008-10-15
when i get a break in about 15 mins ill give you more info as im able to boot my laptop.

basically i think its a setting that needs to be edited with the gconf program (applications - sytem - gconf) you may need to edit your menus to get it to appear (right click - edit menu).

if you want screenshots please say.

---

### Post by eels68 on 2008-10-15
Thanks for your quick reply.

I cant seem to find this "gconf". I typed "gconf-editor" in terminal and got the configuration editor, I presume that is what I will be after?

No screen shot needed at this stage - thanks.

---

### Post by marshall.robert on 2008-10-15
yeah, gconf editor, its like regedit for gnome.

open it, and go apps -> nautilus and they key you are looking for is media_automount. there should be a tickbox next to it, if its unticked then tick it, if it is ticked then you have a different problem.

hope this works

---

### Post by eels68 on 2008-10-15
Looks like a different problem, the "media_automount" box is checked

---

### Post by marshall.robert on 2008-10-15
are you sure you arnt getting confusd between it mounting and opening the folder when plugged in?

---

### Post by eels68 on 2008-10-15
Nah. 
I plug it in and nothing happens what so ever. I can only see it and access it after typing "lsusb" in the terminal screen....after typing that it mounts and the icon for it pops up on the screen.

---

### Post by marshall.robert on 2008-10-15
well, thats as far as my knowledge goes, perhaps you could make a script or something to repeat the procedure you do to mount a stick?

---

### Post by eels68 on 2008-10-16
Thanks for your time and help. Very much appreciated. :)

---

### Post by eels68 on 2008-10-17
Hi.

I thought I would post how I solved my little problem here just incase there are others who end up with this problem.

Firstly, I researched this for a week and had some help from a fellow called Robert, from England. My thanks go out to Robert for both his time and knowledge.

The problem I had was my thumb drive and external hard drive would not automount, in fact the only way I could get them to mount was to type "lsusb" in the terminal screen, this seemed to wake the devices up so to speak. I was getting rather frustrated. I settled on a solution that is a sort of temporary fix, but one that works everytime I boot up.


Firstly I open a terminal screen and typed the following (without quotations):

"sudo gedit /etc/rc.local"

At the bottom of the window that opens up and on the line just before the last line that reads "exit 0" I typed the following (without quotations)"

"modprobe -r ehci_hcd"

I then clicked the save button and quit out of that window.


The next time the computer starts up it runs through that little 'modprobe' command and when ever you plug in your thumb drive it will automount. The same applied for my external hard drive it now automounts too.

If you do the above but don't want to restart your computer for this session then open a terminal screen and type the following (without quotations)"

"sudo modprobe -r ehci_hcd"

this will enable the use of the thumb drive for this session only.


****I must point out that this worked for me and I have had no problems at all, it may not be right for you****

Have a great day. :)

---

