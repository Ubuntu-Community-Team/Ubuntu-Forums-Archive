---
title: "HP Laptop unable to mount second hard drive"
date: 2010-04-23
forum: Hardware
---

### Post by tangerine0469 on 2010-04-23
OK, here is the dilemma i have an HP laptop from my work that i am working on.

Spec's:
Xubuntu-9.10-desktop-i386 installed
HP dv9260nr
250g hard drive (root)
120g hard drive (secondary)
HD-DVD player (i know its obsolete) 
a few other bells and whistles that almost all new laptops have

anyway, my problem is this. the install went smoothly everything is now on the 250g drive. i have been trying for a few days now to be able to mount the 120g drive. it is empty and formatted to ext4. i can view the drive in gparted and exaile music player but i **_cannot _**read any of the data on the drive nor can i mount it. when i am browsing the file system it doesn't even show up. i have tried to unmount and mount it in the terminal and get nowhere. any ideas?

---

### Post by Drenriza on 2010-04-23
```
cat /etc/fstab |less
```
print the output here
 
```
dmesg |less
```
print the output here
 
the secondary drive is that usb or what is that?
 
If it is a usb drive, unplug and replug the drive. run 
```
dmesg |less
```
print the output here
 
or else just run the command at system start-up

---

### Post by tangerine0469 on 2010-04-23
> **Drenriza said:**
> ```
cat /etc/fstab |less
``````
dmesg |less
```the secondary drive is that usb or what is that?

    # /etc/fstab: static file system information.
  #
  # Use 'blkid -o value -s UUID' to print the universally unique identifier # for a device; this may be used with UUID= as a more robust way to name # devices that works even if disks are added and removed. See fstab(5).
  #
  # <file system> <mount point>   <type>  <options>       <dump>  <pass>
  proc            /proc           proc    defaults        0       0
  # / was on /dev/sda1 during installation
  UUID=add78ecc-28fb-4c6f-bc45-b4204fb305b1 /               ext4    
  errors=remount-ro 0       1
  # swap was on /dev/sda5 during installation
  UUID=842ab7a2-a0ec-4075-a726-c1a0a16a771a none            swap    
  sw              0       0
  /dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
  (END)
  



and

   [    0.000000] Initializing cgroup subsys cpuset
  [    0.000000] Initializing cgroup subsys cpu
  [    0.000000] Linux version 2.6.31-20-generic (buildd@palmer) (gcc 
  version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #58-Ubuntu SMP Fri Mar 12 
  05:23:09 UTC 2010 (Ubuntu 2.6.31-20.58-generic)
  [    0.000000] KERNEL supported cpus:
  [    0.000000]   Intel GenuineIntel
  [    0.000000]   AMD AuthenticAMD
  [    0.000000]   NSC Geode by NSC
  [    0.000000]   Cyrix CyrixInstead
  [    0.000000]   Centaur CentaurHauls
  [    0.000000]   Transmeta GenuineTMx86
  [    0.000000]   Transmeta TransmetaCPU
  [    0.000000]   UMC UMC UMC UMC
  [    0.000000] BIOS-provided physical RAM map:
  [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
  [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
  [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
  [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe70000 (usable)
  [    0.000000]  BIOS-e820: 000000007fe70000 - 000000007ff00000 (ACPI NVS)
  [    0.000000]  BIOS-e820: 000000007ff00000 - 0000000080000000 (reserved)
  [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
  [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
  :
  

the drives are both internal, i have not had any issues using my usb drives.

---

### Post by Morbius1 on 2010-04-23
Would you post the output of the following command please:

**sudo blkid -c /dev/null**

---

### Post by tangerine0469 on 2010-04-23
> **Morbius1 said:**
> Would you post the output of the following command please:

**sudo blkid -c /dev/null**


john@john-laptop:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="add78ecc-28fb-4c6f-bc45-b4204fb305b1" TYPE="ext4" 
/dev/sda5: UUID="842ab7a2-a0ec-4075-a726-c1a0a16a771a" TYPE="swap" 
/dev/sdb1: LABEL="Data" UUID="a5a84cbf-cb67-4d65-92e3-a8fc2b6fa89b" TYPE="ext4" 
john@john-laptop:~$

---

### Post by Morbius1 on 2010-04-23
See if you can add a line in /etc/fstab to have that partition mount at boot:

Open **Terminal**
Type **sudo mkdir /media/Data**
Type [B]gksu gedit /etc/fstab
[/B] 
Add the following line to fstab:
```
/dev/sdb1 /media/Data ext4 defaults,noatime 0 2
```Save the file, exit gedit, and back in the terminal type:
**sudo mount -a**

What that will do is mount the partition to /media/Data with owner= root and with read / write permissions to root only. So you will have to change permissions or change ownership:

For example:

Open **Terminal**
Type** sudo chown -R morbius /media/Data**
[COLOR=Blue]*This will change ownership  from root to morbius*[/COLOR]

OR

Open **Terminal**
Type **sudo chmod -R 0777 /media/Data**
[COLOR=Blue][I]This will still have ownership = root but with read / write access to everyone.

EDIT: just realized you using xubuntu. Change gedit to whatever your default text editor is.
[/I][/COLOR]

---

### Post by tangerine0469 on 2010-04-23
that worked perfectly. thank you.

---

