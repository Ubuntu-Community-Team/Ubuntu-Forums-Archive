---
title: "Cannot find disk: Error fsyncing/closing /dev/sda: Input/output error"
date: 2021-09-11
forum: Hardware
---

### Post by bwindsor22 on 2021-09-11
Hey all, attempting to install ubuntu on a box which formerly had arch, and running into this issue. Hoping that I can find an OS which will recognize /dev/sda as my drive and install there.

A quick diagnosis:

The disk is not appearing where I think it should:
* Gparted, when launched from a usb stick, only shows /dev/sdc
* sudo fdisk -l shows only /dev/sdc, /dev/sdc1, and /dev/loop0
* df -h  shows udev tmpfs, /dev/sdc1, /dev/loop0, overlay, and several tmpfs

/dev/sdc is my usb stick:
* udevadm info --query=all /dev/sdc shows that /dev/sdc is DEVLINKS=[...]Lexar_USB_Flash_Drive[...]

Yet /dev/sda still exists
* cat /proc/partitions shows sda, sda1, sda2, sda3, sdc, and loop0
* sudo parted /dev/sda unit s print gives the error in the title: 
> Warning: Error fsyncing/closing /dev/sda1: Input/output error
> Warning: Error fsyncing/closing /dev/sda2: Input/output error
> Warning: Error fsyncing/closing /dev/sda3: Input/output error
>Error: /dev/sda: unrecognized disk label
>Model: ATA SATA SSD (scsi)
>Disk: /dev/sda: 62533296s
>Sector size (logical/physical): 512B/512B
>Partition Table: unknown

FWIW, when I try to install ubuntu from a live flash drive, I get the same "Input/output error" with an option to retry.

Any help appreciated! Is my SSD (/dev/sda) just hosed? Is there another disk reformat util you think I should try running?

---

### Post by bwindsor22 on 2021-09-11
Also, a quick summary of what I've tried: 
* Install ubuntu from flash drive --> doesn't recognize /dev/sda
* Run gparted from flash drive [debian based] --> doesn't recognize /dev/sda, "input/output error" when running some commands
* Run systemrescue from flash drive --> launches and shows a desktop, but still no /dev/sda in df -h, similar commands. Running "gparted" from the systemrescue boot gives "Error fsyncing/closing /dev/sda1: Input/output error"

---

### Post by bwindsor22 on 2021-09-11
Update 2: "sudo shred -v /dev/sda" gives the same "Input/output error"

---

### Post by tea for one on 2021-09-11
> **bwindsor22 said:**
> Any help appreciated! Is my SSD (/dev/sda) just hosed? Is there another disk reformat util you think I should try running?

It's not looking very fruitful right now.

Anyway let's crack on..............

Are you using an Ubuntu live session?

What does  Disks (gnome-disk-utility) show?

Alternatively via a terminal:-
```
sudo gdisk /dev/sda

```

---

### Post by bwindsor22 on 2021-09-11
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289167&stc=1[/IMG]

---

### Post by bwindsor22 on 2021-09-11
[SIZE=4]initial gdisk attempt below
[/SIZE]
untu@ubuntu:~$ sudo gdisk /dev/sda
GPT fdisk (gdisk) version 1.0.5

[B]Warning! Read error 5; strange behavior now likely!
Warning! Read error 5; strange behavior now likely![/B]
Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries in memory.

Command (? for help): 

Command (? for help): ?
b    back up GPT data to a file
c    change a partition's name
d    delete a partition
i    show detailed information on a partition
l    list known partition types
n    add a new partition
o    create a new empty GUID partition table (GPT)
p    print the partition table
q    quit without saving changes
r    recovery and transformation options (experts only)
s    sort partitions
t    change a partition's type code
v    verify disk
w    write table to disk and exit
x    extra functionality (experts only)
?    print this menu

Command (? for help): v

No problems found. 62533229 free sectors (29.8 GiB) available in 1
segments, the largest of which is 62533229 (29.8 GiB) in size.

Command (? for help): p
Disk /dev/sda: 62533296 sectors, 29.8 GiB
Model: SATA SSD        
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): 1960C385-E122-43CF-ACCF-41BF9AA0F136
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 62533262
Partitions will be aligned on 2048-sector boundaries
Total free space is 62533229 sectors (29.8 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name

Command (? for help):

---

### Post by bwindsor22 on 2021-09-11
Command (? for help): n
Partition number (1-128, default 1): 1
First sector (34-62533262, default = 2048) or {+-}size{KMGTP}: +
Last sector (2048-62533262, default = 62533262) or {+-}size{KMGTP}: 
Current type is 8300 (Linux filesystem)
Hex code or GUID (L to show codes, Enter = 8300): 8303
Changed type of partition to 'Linux x86 root (/)'

Command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT) to /dev/sda.
Unable to save backup partition table! Perhaps the 'e' option on the experts'
menu will resolve this problem.
Warning! An error was reported when writing the partition table! This error
MIGHT be harmless, or the disk might be damaged! Checking it is advisable.
Command (? for help): v       

No problems found. 2014 free sectors (1007.0 KiB) available in 1
segments, the largest of which is 2014 (1007.0 KiB) in size.

---

### Post by bwindsor22 on 2021-09-11
[SIZE=4]disk now looks different in "Disk", but reformat fails[/SIZE]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289168&stc=1[/IMG]

---

### Post by bwindsor22 on 2021-09-11
yes, on Ubuntu booted from flash drive now, was on systemrescue previously

---

### Post by bwindsor22 on 2021-09-11
[SIZE=5]After the above, I exited gdisk, and re-ran, seeing the same error. Write appears to fail, and when I re-run gdisk, I don't see any partitions.

[/SIZE]


ubuntu@ubuntu:~$ sudo gdisk /dev/sda
GPT fdisk (gdisk) version 1.0.5

Warning! Read error 5; strange behavior now likely!
Warning! Read error 5; strange behavior now likely!
Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries in memory.

Command (? for help): ?
b    back up GPT data to a file
c    change a partition's name
d    delete a partition
i    show detailed information on a partition
l    list known partition types
n    add a new partition
o    create a new empty GUID partition table (GPT)
p    print the partition table
q    quit without saving changes
r    recovery and transformation options (experts only)
s    sort partitions
t    change a partition's type code
v    verify disk
w    write table to disk and exit
x    extra functionality (experts only)
?    print this menu

Command (? for help): n
Partition number (1-128, default 1): 1
First sector (34-62533262, default = 2048) or {+-}size{KMGTP}: 
Last sector (2048-62533262, default = 62533262) or {+-}size{KMGTP}: 
Current type is 8300 (Linux filesystem)
Hex code or GUID (L to show codes, Enter = 8300): 8300
Changed type of partition to 'Linux filesystem'

Command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT) to /dev/sda.
Unable to save backup partition table! Perhaps the 'e' option on the experts'
menu will resolve this problem.
Warning! An error was reported when writing the partition table! This error
MIGHT be harmless, or the disk might be damaged! Checking it is advisable.

Command (? for help): p
Disk /dev/sda: 62533296 sectors, 29.8 GiB
Model: SATA SSD        
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): 572BD20F-57B3-478A-B745-846E517F9333
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 62533262
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048        62533262   29.8 GiB    8300  Linux filesystem

Command (? for help): i
Using 1
Partition GUID code: 0FC63DAF-8483-4772-8E79-3D69D8477DE4 (Linux filesystem)
Partition unique GUID: 9E2405B5-841A-4FD7-AF6F-D2D3FA222E25
First sector: 2048 (at 1024.0 KiB)
Last sector: 62533262 (at 29.8 GiB)
Partition size: 62531215 sectors (29.8 GiB)
Attribute flags: 0000000000000000
Partition name: 'Linux filesystem'

Command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT) to /dev/sda.
Unable to save backup partition table! Perhaps the 'e' option on the experts'
menu will resolve this problem.
[B]Warning! An error was reported when writing the partition table! This error
MIGHT be harmless, or the disk might be damaged! Checking it is advisable.[/B]

Command (? for help): 
[B]Command (? for help): ^C
ubuntu@ubuntu:~$ sudo gdisk /dev/sda[/B]
GPT fdisk (gdisk) version 1.0.5

Warning! Read error 5; strange behavior now likely!
Warning! Read error 5; strange behavior now likely!
Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries in memory.

[B]Command (? for help): i
No partitions[/B]

---

### Post by bwindsor22 on 2021-09-11
Hmm, stack overflow seems to think error #5 means likely hardware error
[https://askubuntu.com/questions/715358/gdisk-unable-to-write-gpt-table](https://askubuntu.com/questions/715358/gdisk-unable-to-write-gpt-table)

---

### Post by tea for one on 2021-09-11
Quite probably a hardware problem.
I'll post back if I can think of anything else which may help.

---

