---
title: "lost second hard drive after installing 9.04"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by windowsareslow on 2009-04-26
Folks:
I installed Jaunty and everything went fine, but upon restarting, I cannot see my second hard drive.  I am doing this:

40G drive:  OS and home drives
320G drive:  Just data

The 40G is fine, but the 320 is either not visable or partially visable.  Here is my fdisk stuff:

bob@bob-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0008d14e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   625137344   312568641   83  Linux

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xedb0edb0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    76903154    38451546   83  Linux
/dev/sdb2        76903155    80292869     1694857+   5  Extended
/dev/sdb5        76903218    80292869     1694826   82  Linux swap / Solaris
bob@bob-desktop:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=625137282, Id=83
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size= 76903092, Id=83, bootable
/dev/sdb2 : start= 76903155, size=  3389715, Id= 5
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
/dev/sdb5 : start= 76903218, size=  3389652, Id=82

Any ideas?

---

### Post by windowsareslow on 2009-04-26
Ok, I think I am on to something here:  note my fstab contents:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=14531143-a047-4d3e-b6aa-7feced4c526f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=1ab10a9c-cdfa-456b-8d39-e832326160d0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1 /mnt/thumb vfat uid=500,gid=500,umask=000,exec,dev,suid,rw 1 0
/dev/sdb1 /media/320G_drive ext3 defaults,relatime 0 2


That looks out of whack.

---

### Post by windowsareslow on 2009-04-26
Ok, for some reason my hardrives all renamed themselves.  The logical names are different now.  I edited my /etc/fstab:

Took out:
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#/dev/sda1 /mnt/thumb vfat uid=500,gid=500,umask=000,exec,dev,suid,rw 1 0
#/dev/sdb1 /media/320G_drive ext3 defaults,relatime 0 2

and added:
/dev/sda /media/320G_drive ext3 defaults,relatime 0 2
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

It turns out my cdrom drive wasn't working either for the same reason.

ok, solved I guess.  I don't fully grasp what is going on here but at least I have my drive/data back.

---

### Post by TexSquid on 2009-04-26
I have the same problem. I think. Couls you give me a quick guide on how to edit etc/fstab. 

Here are my results

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe4651a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    75200264    37600101   83  Linux
/dev/sda2        75200265    78172289     1486012+   5  Extended
/dev/sda5        75200328    78172289     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0026ae0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   160071659    80035798+   7  HPFS/NTFS

---

### Post by windowsareslow on 2009-04-26
Tex:
Basically read the instructions for adding a second hard drive at:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

That tells you the basics.  Do NOT format anything.  You have to run

sudo lshw -C disk

to get the new logical names and edit the fstab to match.  The actual command for editing is sudo gedit /etc/fstab.  I can't tell you I just copied the old lines that referred to my drives and edited the logical names at the start.  I am not really an expert but that worked for me.

Bob

---

### Post by TexSquid on 2009-04-28
Thanx, I tried that and I get ...

sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

This is a second hard drive with only media that I have had thru a Windows box and 3 Ubuntu distros. It showed  initially with Jaunty but then disappeared from the filesystem. It now shows in the file system but I cannot access it.
I had my music files loaded on Rhythm Box and when I just opened it they drained away .

The  80G drive showing under fileystem in media states 0 items 30.5  G free space so the files must still be there.

---

### Post by TexSquid on 2009-04-29
bump

---

### Post by windowsareslow on 2009-04-29
Do these commands and post the output, maybe I can figure something out to try.

sudo fdisk -lu

sudo sfdisk -d

sudo lshw -C disk

cat /etc/fstab

bob

---

### Post by TexSquid on 2009-04-30
thanx, bob 

sudo sfdisk -d

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 75200202, Id=83, bootable
/dev/sda2 : start= 75200265, size=  2972025, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 75200328, size=  2971962, Id=82
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=160071597, Id= 7
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0

 sudo lshw -C disk

  *-disk:0                
       description: ATA Disk
       product: MAXTOR 6L040J2
       vendor: Maxtor
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: A93.
       serial: 662206237375
       size: 37GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=e4651a0a
  *-disk:1
       description: ATA Disk
       product: Maxtor 6Y080P0
       vendor: Maxtor
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: YAR4
       serial: Y2V702XE
       size: 76GiB (81GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0026ae0a
  *-cdrom
       description: DVD writer
       product: DVD LS DW1655
       vendor: BENQ
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: BCAB
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc
  *-disk:0
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdc
  *-disk:1
       description: SCSI Disk
       product: SD-MS-SM
       vendor: eUSB
       physical id: 0.0.1
       bus info: scsi@2:0.0.1
       logical name: /dev/sdd
       version: 5.07
       capabilities: removable
       configuration: ansiversion=2
     *-medium
          physical id: 0
          logical name: /dev/sdd

 cat /etc/fstab

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=64948eb3-90a7-49a7-b9bb-ed126bd6964c / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=3c0214e5-9758-43b8-aea5-1497d538a110 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sdb /media/BigDisc vfat defaults 0 0



  and like I said before, this is the first time I have not been able to access the drive, even in Jaunty.

---

### Post by windowsareslow on 2009-05-01
Tex:

Just try adding a "1" to /dev/stb in the last line:



# /etc/fstab: static file system information.
#
# -- This file has been automaticly generated by ntfs-config --
#
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=64948eb3-90a7-49a7-b9bb-ed126bd6964c / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=3c0214e5-9758-43b8-aea5-1497d538a110 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sdb1 /media/BigDisc vfat defaults 0 0

---

### Post by klapauciuspdx on 2009-05-01
I think I might have an answer for you..... Had a similar problem...

Per this page:

[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

the device names can change between boots... what happened to me is that it would switch, and die during the startup, because my fstab only had an entry for the second drive that was of the form 'dev/hdb1' along with the relevant parameters.  

On that page, it mentions that those drive labels may change when the system is rebooted, which is what causes the problem.  

What you have to do is to generate a UUID for the second hard drive.

Comment out the line for the label, and create a new line for the UUID or replace the label portion of that line with "UUID=blahblahblah".

You can determine the UUID by issuing 

sudo vol_id /dev/x , where /dev/x is the assigned drive label, according to lshw.  

My machine was switching between /dev/sda1 and /dev/sdb1 for the second drive.  

I commented out the line for the second drive and rebooted.  This should allow the machine to come up on the primary drive and / partition.

if you run 'sudo lshw | less ' it will let you page through the hardware attached to the machine.  Since there's a size difference between your two drives, you should be able to find them in sections of that file, under 'disk'.  One should be your primary, and there will be a label for it, like /dev/sda.  Find the other disk, and in the descriptor block for it, there will be another label.

Use:  sudo vol_id (label)

This should generate a small block of text with a UUID line in it.  You can now go into /etc/fstab, and either uncomment the line with the appropriate label, and replace the label on that line with "UUID=" followed by the UUID number generated earlier, or create a new line with the UUID portion followed by whatever filesystem parameters you want to use.  Once you've made that change, reboot the system, and you should be good to go.

Feel free to contact me if you still have problems, or if I've confused you, I know what the issue was, and how to correct it, but I don't always know how to explain it properly.

K.

---

### Post by windowsareslow on 2009-05-01
Thanks, I had seen that also.  My "fix" I posted earlier had already broken once, so I was considering this.  I was unclear that you can just use the UUID in that way.  I will check it out.

---

### Post by TexSquid on 2009-05-02
this is what I get..

texsquid@
~$ sudo vol_id /dev/sdb
unknown or non-unique volume type (--probe-all lists possibly conflicting types)
texsquid@
:~$ sudo vol_id /dev/sdb1
unknown or non-unique volume type (--probe-all lists possibly conflicting types)

I am also getting a logical error message on the secomd hard drive on boot

as for
sudo blkid
/dev/sda1: UUID="64948eb3-90a7-49a7-b9bb-ed126bd6964c" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="3c0214e5-9758-43b8-aea5-1497d538a110"

no second drive appears

---

### Post by klapauciuspdx on 2009-05-02
Texsquid,

It looks like you may have at least one, and possibly a couple of USB external drives attached per the output of your lshw.  If that's the case, I would recommend removing them first.  With the machine being able to change device labels between boots, minimizing the additional hardware may be the easiest way to deal with it. It's tossing a few more drives into the mix, which can confuse things further.

That way, you could add the additional internal drive with a minimum amount of fussing with it.  If the additional USB drives are going to be relatively permanently attached to the machine, you can add them later and put the additional drives in the fstab as necessary.

Also, BTW, blkid gives you the same UUID.  They will both provide the same output.  The UUID number is the important bit. 

K.

---

### Post by whiskeyjack on 2009-05-06
I ran into this same problem; Installed Kubuntu 9.04 (inside windows) and everything seemed to work fine, except my secondary HD wasn't accessible.

I checked through GParted, and found the drive, but with no partitions.

Upon rebooting to Windows, I found that the partition was pooched; or at least, the 48-bit LBA "function" was gone. I had had the same problem when i first installed the drive (that i could only create a partition of 137GB when its a 1TB drive), but that had been fixed after upgrading my BIOS.

Now though, despite having uninstalled kubuntu, i still cannot see more than 137GB of my drive. I haven't repartitioned or formated yet, as i don't want to lose all the data on the drive.

Also, desipte having uninstalled kubuntu, i still have it as a choice at bootup.

Any ideas?

---

### Post by klapauciuspdx on 2009-05-06
> **whiskeyjack said:**
> I ran into this same problem; Installed Kubuntu 9.04 (inside windows) and everything seemed to work fine, except my secondary HD wasn't accessible.

I checked through GParted, and found the drive, but with no partitions.

Upon rebooting to Windows, I found that the partition was pooched; or at least, the 48-bit LBA "function" was gone. I had had the same problem when i first installed the drive (that i could only create a partition of 137GB when its a 1TB drive), but that had been fixed after upgrading my BIOS.

Now though, despite having uninstalled kubuntu, i still cannot see more than 137GB of my drive. I haven't repartitioned or formated yet, as i don't want to lose all the data on the drive.

Also, desipte having uninstalled kubuntu, i still have it as a choice at bootup.

Any ideas?

Unfortunately not... I tend to run my linux boxes on separate hardware, so I am not terribly familiar with the manner in which you've installed.  It's possible that it's just Windows interpretation of what's there.  Windows is not known for playing nicely with other operating systems ( read up what they've done to make Samba difficult ), and it is my personal opinion that they make it as difficult as possible for the end user( Question for the DOJ:  How in the heck is this not monopolistic behavior? ).  

You might be able to retrieve at least part of the data by burning a LiveCD, booting off that, and moving data to an external drive, depending upon how much data there is... Wish I knew more about it, but I haven't had much time to do the research.  Was laid off back in November, but I've been doing friends/family tech support pretty much non-stop, and that's Windows and Mac.  It would be nice if it paid, but it gets me back in practice if I have to go back to desktop support.

K.

---

### Post by whiskeyjack on 2009-05-07
Hey all!

I've come across more information; I ran Active Partition Recovery, and it says my secondary HDD is fine, no problems with the MBR, PT, or FS.

THEN, I tried to play a DVD in my drive, and no disc is being read; the drive barely notices anything is happening.

I'm suspicious that installing Kubuntu has made a change to the boot system of my PC and didn't undo it when in uninstalled; especially since I still get a boot menu to choose between xp and kubuntu when i start up.

I'm getting to re-install winxp overtop to see if that fixes it, but if anyone has any ideas of where else to look, I'ld appreciate it!

Thanx!
WJ

---

