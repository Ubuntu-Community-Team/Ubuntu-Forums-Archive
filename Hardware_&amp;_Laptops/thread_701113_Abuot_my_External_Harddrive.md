---
title: "Abuot my External Harddrive"
date: 2008-02-19
forum: Hardware &amp; Laptops
---

### Post by kenny2010ken on 2008-02-19
hello everyone

I have this Western Digital external harddrive

it works when if I plug it in while turning on Ubuntu 7.10 AMD64

but somehow it will pup up this message that it cannot mount the harddrive

and if I unplug it and plug in back it does not show up anymore

I have my Vista and Ubuntu on this laptop

if I can use my external harddrive on Ubuntu I think I'll fully using this OS

but now I just try to fix this problem

thanks

---

### Post by Yellow Pasque on 2008-02-19
Plug your disk in. What output do these commands give you?
```
sudo fdisk -l
sudo lshw -C disk
```
Another thing you should look at is the Removable Media settings in the System Menu.
Also, post your /etc/fstab file.

---

### Post by pettertorp on 2008-02-19
I have the same problem. here is the info when I type the commands (would be amazing if anyone could help me on this);
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa16af192

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18728   150432628+  83  Linux
/dev/sda2           18729       19457     5855692+   5  Extended
/dev/sda5           18729       19457     5855661   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS
petter@petter-laptop:~$ sudo lshw -C disk
  *-cdrom
       description: DVD-RAM writer
       product: MATSHITADVD-RAM UJ-851S
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: 1.50
       serial: HD34 132924
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=nodisc
  *-disk
       description: SCSI Disk
       product: FUJITSU MHW2160B
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 891F
       serial: K10NT762D5C8
       size: 149GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-disk
       description: SCSI Disk
       product: FreeAgentDesktop
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@8:0.0.0
       logical name: /dev/sdb
       version: 100D
       serial: 6QG1SB60
       size: 465GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=4

---

### Post by Yellow Pasque on 2008-02-19
peter, try this:
First if you're using something earlier than Gutsy (7.10), grab the ntfs-3g driver
```
sudo apt-get install ntfs-3g
```
Also, make sure your mounting folder is empty and has the proper permissions.
```
cd /media; sudo mkdir disk; sudo chmod 777 disk
```
Now, let's mount us some external drives!
```
sudo mount -t ntfs-3g /dev/sdb1 /media/disk
```
Does that do the trick?

---

### Post by pettertorp on 2008-02-19
will it format the external hd? or will all the files still be there?

---

### Post by Yellow Pasque on 2008-02-19
The files will still be there. If you want to do read-only access, use ntfs instead of ntfs-3g.

---

### Post by pettertorp on 2008-02-19
petter@petter-laptop:/media$ sudo apt-get install ntfs-3g
Reading package lists... Done
Building dependency tree
Reading state information... Done
ntfs-3g is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
petter@petter-laptop:/media$ cd /media; sudo mkdir disk; sudo chmod 777 disk
mkdir: cannot create directory `disk': File exists
petter@petter-laptop:/media$ sudo mount -t ntfs-3g /dev/sdbl /media/disk
Failed to access '/dev/sdbl': No such file or directory
petter@petter-laptop:/media$  

seems to be some error on the last one, not sure if I have all things installed correctly or not.

---

### Post by Yellow Pasque on 2008-02-19
sdb**1** <-- That's the number "ONE"
EDIT: I should also have you use this option to give non-root users access
```
sudo mount -t ntfs-3g -o uid=1000 /dev/sdb1 /media/disk
```

---

### Post by pettertorp on 2008-02-19
ah. but when I write in that I get this back

Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/disk -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/disk ntfs-3g defaults,force 0 0

and when I try to force it it gives me permission denied on the 2nd option and "only root can do that" on the 1st option.

---

### Post by pettertorp on 2008-02-19
> **Temüjin said:**
> sdb**1** <-- That's the number "ONE"
EDIT: I should also have you use this option to give non-root users access
```
sudo mount -t ntfs-3g -o uid=1000 /dev/sdb1 /media/disk
```

petter@petter-laptop:~$ sudo mount -t ntfs-3g -o uid=1000 /dev/sdb1 /media/disk
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/disk -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/disk ntfs-3g defaults,force 0 0
petter@petter-laptop:~$

---

### Post by Yellow Pasque on 2008-02-19
If it complains about super-user/root permissions, use the sudo qualifier in front of a command.
```
sudo mount -t ntfs-3g -o force,uid=1000 /dev/sdb1 /media/disk
```

---

### Post by pettertorp on 2008-02-19
thank you :)
saved all my back-ups from the past 5 years!

---

### Post by Yellow Pasque on 2008-02-19
> **pettertorp said:**
> thank you :)
saved all my back-ups from the past 5 years!
Awesome! You're welcome.

---

### Post by kenny2010ken on 2008-02-21
after typing in > sudo fdisk -l and > sudo lshw -C diskMine shows this

> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe9e6bd8e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12454   100030128+   7  HPFS/NTFS
/dev/sda2           13729       14593     6948112+   7  HPFS/NTFS
/dev/sda3           12455       13304     6827625   83  Linux
/dev/sda4           13305       13728     3405780    5  Extended
/dev/sda5           13305       13728     3405748+  82  Linux swap / Solaris

and this

>  *-cdrom                 
       description: DVD-RAM writer
       product: HL-DT-ST DVDRAM GSA-T10N
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: PC05
       serial: KY471K71935
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=nodisc
  *-disk
       description: SCSI Disk
       product: TOSHIBA MK1234GS
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: AH00
       serial: 17RTT9IXT
       size: 111GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5

seems like it doesn't show anything like my 500Gb external harddrive

it is connected by USB2

one thing I noticed is that when I use my external harddrive under Vista

it sometimes will turn off itself... but power-off

but when I try to read data from it, I can hear the noise of reading hard drive.

under Ubuntu, it just pop out a box said "data lose, please use the 'unplug' to unplug your hard drive"

and when I unplug it and connect it back, nothing returns

---

### Post by konungursvia on 2008-02-24
I had the same issues. Solved by sharing the whole drive with all users, then any user and any software can cleanly mount and unmount. It is the unclean unmounts that cause it to not mount the subsequent times.

---

