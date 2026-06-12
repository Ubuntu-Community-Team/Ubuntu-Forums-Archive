---
title: "Ubuntu 8.10 will not recognize my external HD"
date: 2009-03-12
forum: Hardware
---

### Post by Korwynz on 2009-03-12
I am brand new to linux but am pretty quick with it.  When i first installed ubuntu it was through windows.  at that time it would see my external 80 gig FAT32 iomega HD but it wouldnt mount.  now that i have ubuntu taking over the hard drive it wont even appear.  i have tried the usb in every slot and to be sure tried it on windows and it works fine.  any suggestions from the smart ones out there? :)

---

### Post by Wazomba on 2009-03-12
I suggest you first search the forum. This topic is widely discussed, though in some cases, no "quick & easy" solution is available. It can give you a search path. It's a driver pb. You should check the repos or elsewhere for a driver for your specifiq material & config.

I've the same problem w/ a IDE Western Digital Hardrive that I fixed  into the box of my dead CDRW, an old QPS-525 SCSI to USB box. No solution found at that time anywhere. I'm still looking for a workaround or fix.

Good luck!

---

### Post by Korwynz on 2009-03-12
i have searched but most of what i am finding are people having trouble mounting on an ntfs external and this doesnt exactly apply to me but regardless i tried some of what was suggested for those types with still no resolution :(

---

### Post by taurus on 2009-03-12
Plug your external harddrive back into a windows machine.  Then, use the _safely remove hardware_ icon (bottom right corner) to unmount it first before you unplug it from your machine.  Now, plug it back into Ubuntu machine and if it doesn't automount, open a terminal and post the outputs of these commands.

```
dmesg | tail
sudo fdisk -l
df -h
```

---

### Post by nwadams on 2009-03-13
i'm having a similar problem where it detects the drive only some of the time. When the drive is detected it mounts properly but it only detects the drive about 25% of the time.

---

### Post by Korwynz on 2009-03-14
this didnt seem to work... it showed me only my partitioned drives but not the external. and when i typed in the first line it said demsg wasnt a valid command :(

---

### Post by nwadams on 2009-03-14
here's my output code  
 dmesg | tail
```
[  117.718712] usb 4-1: new high speed USB device using ehci_hcd and address 6
[  117.800254] usb 4-1: device descriptor read/64, error -71
[  118.008372] usb 4-1: device descriptor read/64, error -71
[  118.224093] usb 4-1: new high speed USB device using ehci_hcd and address 7
[  118.336829] usb 4-1: device descriptor read/64, error -71
[  118.543017] usb 4-1: device descriptor read/64, error -71
[  118.611988] usb 4-1: new high speed USB device using ehci_hcd and address 8
[  118.953842] usb 4-1: device not accepting address 8, error -71
[  119.012137] usb 4-1: new high speed USB device using ehci_hcd and address 9
[  119.304023] usb 4-1: device not accepting address 9, error -71

```

sudo fdisk -l
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c21a78e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7295    58597056   83  Linux
/dev/sda2           29903       30401     4008217+  82  Linux swap / Solaris
/dev/sda3            7296       29902   181590727+  83  Linux

Partition table entries are not in disk order
```

df -h
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              56G  3.0G   50G   6% /
varrun                1.5G  104K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   52K  1.5G   1% /dev
devshm                1.5G   12K  1.5G   1% /dev/shm
lrm                   1.5G   44M  1.5G   3% /lib/modules/2.6.24-23-generic/volatile
/dev/sda3             172G   21G  144G  13% /home
gvfs-fuse-daemon       56G  3.0G   50G   6% /home/nwadams/.gvfs

```

---

### Post by taurus on 2009-03-14
> **nwadams said:**
> here's my output code  
 dmesg | tail
```
[  117.718712] usb 4-1: new high speed USB device using ehci_hcd and address 6
[  117.800254] usb 4-1: device descriptor read/64, error -71
[  118.008372] usb 4-1: device descriptor read/64, error -71
[  118.224093] usb 4-1: new high speed USB device using ehci_hcd and address 7
[  118.336829] usb 4-1: device descriptor read/64, error -71
[  118.543017] usb 4-1: device descriptor read/64, error -71
[  118.611988] usb 4-1: new high speed USB device using ehci_hcd and address 8
[  118.953842] usb 4-1: device not accepting address 8, error -71
[  119.012137] usb 4-1: new high speed USB device using ehci_hcd and address 9
[  119.304023] usb 4-1: device not accepting address 9, error -71

```

sudo fdisk -l
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c21a78e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7295    58597056   83  Linux
/dev/sda2           29903       30401     4008217+  82  Linux swap / Solaris
/dev/sda3            7296       29902   181590727+  83  Linux

Partition table entries are not in disk order
```

df -h
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              56G  3.0G   50G   6% /
varrun                1.5G  104K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   52K  1.5G   1% /dev
devshm                1.5G   12K  1.5G   1% /dev/shm
lrm                   1.5G   44M  1.5G   3% /lib/modules/2.6.24-23-generic/volatile
/dev/sda3             172G   21G  144G  13% /home
gvfs-fuse-daemon       56G  3.0G   50G   6% /home/nwadams/.gvfs

```

What kind of external drive do you have?  Does it work if you connect it to another machine?

Try running these commands and see if it would show up.

```
lsusb
dmesg | tail
```

---

### Post by nwadams on 2009-03-14
ok here's my lsusb right after i plug it in to my laptop (computer that it doesn't work on 

```
Bus 004 Device 026: ID 0c0b:b157 Dura Micro, Inc. (Acomdata) 
Bus 004 Device 004: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 007 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000 
```

and about 3 seconds later i run lsusb again and its exactly the same except the top line is not there (Dura Micro, Inc. (Acomdata))  Thats my usb hard drive. 

It mounted once on my desktop computer and i unmounted and tried to plug it back in to that computer and it woudl'nt mount. dmesg | tail is very similar to the one I posted before.

[EDIT] I'm going to try another external hard drive tomorrow and see if it works better. If it does i'll just switch the hard drives in them [/EDIT]

---

### Post by Korwynz on 2009-03-14
jason@Nexus:~$ lsusb
Bus 006 Device 003: ID 059b:0177 Iomega Corp. Hi-Speed USB-to-IDE Bridge Controller
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jason@Nexus:~$ dmesg | tail
[ 1015.584565] sd 7:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1015.584569] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1015.585564] sd 7:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1015.585568] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1015.586563] sd 7:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1015.586567] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1015.587563] sd 7:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1015.587567] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1015.588569] sd 7:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1015.588573] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information

---

### Post by taurus on 2009-03-14
Now

```
sudo fdisk -l
```

---

### Post by Korwynz on 2009-03-14
jason@Nexus:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

---

### Post by nwadams on 2009-03-14
try rebooting yoru computer with the usb drive plugged in. It should mount when you boot up with it plugged in (i know its not a fix, but its a potentially interesting fact.

---

### Post by taurus on 2009-03-14
Do you have any important files on that 80GB drive?

Try installing gparted and see if it even detects your external harddrive.

```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
```
Use the drop down tab on the right to see if /dev/sdb is even listed.

---

### Post by Korwynz on 2009-03-14
Unfortunately, yes, i have some important things on the external HD.  but here is a funny thing.  i tried the suggestion of rebooting with the usb drive plugged in and the splash screen hangs for a lengthy period of time.  left it for almost 5 minutes.  i have to unplug it and restart to get into gnome.

---

### Post by nwadams on 2009-03-14
ya it does that sometimes. But sometimes it boots properly and mounts. But mine atleast is not being deteced by gparted when its not mounted correctly.

EDIT: Did you install by any chance using a live usb rather than a cd?? Thats How i installed (usb)

---

### Post by Korwynz on 2009-03-14
mine never boots up when its plugged in :(  its not even seeing something plugged in.  

to answer your second question, i installed using a live cd.

---

### Post by nwadams on 2009-03-14
hmm. I did a test. It boots if it was plugged in, then rebooted. But if it was rebooted and then plugged in during post it woudln't boot...Odd I think. 

So yours won't mount at all no matter what you do? 


Bus 006 Device 003: ID 059b:0177 Iomega Corp. Hi-Speed USB-to-IDE Bridge Controller

is that your external usb device??

EDIT: we can try to force mount the device...

---

### Post by Korwynz on 2009-03-14
yea the iomega is my drive.  how would we go about forcing the mount?

---

### Post by nwadams on 2009-03-14
you'll need a mount point somewhere (example /media/disk)

if you have one good, if not u can make one

```
sudo mkdir /media/disk (thats to make the directory if you don't have one)

then

sudo mount -o force /dev/sdb1 /media/disk
```

If it mounts you'll have to sudo umount /dev/sdb1 to unmount it
and if mounting it doesn't work you could try to force mount it again with just /dev/sdb instead of /dev/sdb1 and see what happens

---

### Post by Korwynz on 2009-03-14
jason@Nexus:~$ sudo mkdir /media/disk
jason@Nexus:~$ sudo mount -o force /dev/sdb1 /media/disk
mount: special device /dev/sdb1 does not exist
jason@Nexus:~$ sudo mount -o force /dev/sdb /media/disk
mount: special device /dev/sdb does not exist

---

### Post by nwadams on 2009-03-14
not unexpected...because it is an ide device (ata 100) you could try hdb1 and hdb, but i don't expect it to help

give me 5 mins i'm reading on the problem/solution

---

### Post by Korwynz on 2009-03-14
nope.. hdb didn't work either

---

### Post by nwadams on 2009-03-14
Hi, as root remove (or move to an other folder) these files:

40-permissions.rules
60-persistent-storage.rules

They are here: /etc/udev/rules.d/

After doing this, download both files below and put them into the rules.d folder

[http://www.esnips.com/doc/2ca0b833-cae6-4522-81ff-d6d0439ddf70/65-persistent-storage.rules.tar](http://www.esnips.com/doc/2ca0b833-cae6-4522-81ff-d6d0439ddf70/65-persistent-storage.rules.tar)

[http://www.esnips.com/doc/79f10bc4-bb62-439c-995d-398a7b9ac210/40-permissions.rules.tar](http://www.esnips.com/doc/79f10bc4-bb62-439c-995d-398a7b9ac210/40-permissions.rules.tar)

Rename the 65-persistent-storage.rules to 60-persistent-storage.rules

that may or may not fix your problem, however i've no idea.

---

### Post by Korwynz on 2009-03-14
this is progress!  i did what u said with those files.  i can see the usb disk on the file browser.  but i cant seem to mount it.  i tried as before the force mount with sdb1 and it didnt work but when i tried with plain ol' sdb it hung.  so not sure what to do now

---

### Post by taurus on 2009-03-14
What is the output of this command again?

```
sudo fdisk -l
```

---

### Post by Korwynz on 2009-03-14
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

---

### Post by taurus on 2009-03-14
Still not showing up.

```
lsusb
dmesg | tail
```

---

### Post by Korwynz on 2009-03-14
jason@Nexus:~$ lsusb
Bus 006 Device 003: ID 059b:0177 Iomega Corp. Hi-Speed USB-to-IDE Bridge Controller
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jason@Nexus:~$ dmesg | tail
[  286.463165] sd 7:0:0:0: [sdb] Sense Key : No Sense [current] 
[  286.463169] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[  286.464128] sd 7:0:0:0: [sdb] Sense Key : No Sense [current] 
[  286.464132] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[  286.465148] sd 7:0:0:0: [sdb] Sense Key : No Sense [current] 
[  286.465151] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[  286.466126] sd 7:0:0:0: [sdb] Sense Key : No Sense [current] 
[  286.466130] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[  286.467128] sd 7:0:0:0: [sdb] Sense Key : No Sense [current] 
[  286.467132] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information


I'm starting to wonder if i'm a special case :(

---

### Post by nwadams on 2009-03-14
Its an error in how your specific hardware is (or in your case not) supported. 

When its in teh file browser what happens when you try to click on it?

how long did you wait with just sdb? because it can sometimes take up to a minute to mount.

EDIT: i'm gonna create a new thread for my problem as it is now unrelated to yours.

---

### Post by Korwynz on 2009-03-14
says unable to mount when i click it.  in the force mount i let it go for about 2-3 minutes and it just hung there

---

### Post by nwadams on 2009-03-14
and you tried hdb1 / hdb as well as sdb1 / sdb?

can you post what's in your etc/fstab file?

gedit /etc/fstab to see your fstab file

---

### Post by Korwynz on 2009-03-14
yea hdb1 and hdb didnt wok either.. here is the fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3e9292f3-c080-4ac0-b415-534ccebecda5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b18e3319-5b12-4ec1-aa3a-a16afd0cc832 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Korwynz on 2009-03-15
i guess there is no hope for me :(

---

### Post by nwadams on 2009-03-15
not true. I'm out of ideas as to what to do now. I've never seen a device show up in the file manager but not in fdisk. I was kind of hoping someone else would have an idea, but i'll keep looking.

edit: will it show up in gparted now?

---

### Post by Korwynz on 2009-03-15
here, i started a new thread dealing with this new problem.  [http://ubuntuforums.org/showthread.php?t=1096987]("http://ubuntuforums.org/showthread.php?t=1096987")  this way people can see the new issue.  on the new thread i reference this in case someone else may have some ideas.  thank you for the effort Nwadams, being a first time user is tough so it's great to have good people like you around who care so much :)

---

### Post by nwadams on 2009-03-15
your welcome. Glad I could help. If tis any consolation the drive apparently worked properly in gusty...(an older version)

---

### Post by sdswingr on 2009-03-16
having a similar problem. Wouldn't even recognize the drive when first plugged in. I rebooted with it plugged in, it is recognized but unable to mount...
here is some of the info 

dmesg | tail
[ 1329.406968] Buffer I/O error on device sdb, logical block 0
[ 1359.516064] usb 1-1: reset full speed USB device using uhci_hcd and address 2
[ 1390.888064] usb 1-1: reset full speed USB device using uhci_hcd and address 2
[ 1422.260060] usb 1-1: reset full speed USB device using uhci_hcd and address 2
[ 1453.632181] usb 1-1: reset full speed USB device using uhci_hcd and address 2
[ 1485.008058] usb 1-1: reset full speed USB device using uhci_hcd and address 2
[ 1516.376060] usb 1-1: reset full speed USB device using uhci_hcd and address 2
[ 1517.658429] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[ 1517.658452] end_request: I/O error, dev sdb, sector 0
[ 1517.658467] Buffer I/O error on device sdb, logical block 0

sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c25da

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30314   243497173+  83  Linux
/dev/sda2           30315       30401      698827+   5  Extended
/dev/sda5           30315       30401      698796   82  Linux swap / Solaris

 df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             229G   65G  153G  30% /
tmpfs                 117M     0  117M   0% /lib/init/rw
varrun                117M  104K  117M   1% /var/run
varlock               117M     0  117M   0% /var/lock
udev                  117M  2.7M  114M   3% /dev
tmpfs                 117M  136K  117M   1% /dev/shm
lrm                   117M  2.0M  115M   2% /lib/modules/2.6.27-11-generic/volatile

lsusb
Bus 001 Device 002: ID 1058:0402 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Help is greatly appreciated..this drive has worked perfectly fine with every distro except 8.10

---

