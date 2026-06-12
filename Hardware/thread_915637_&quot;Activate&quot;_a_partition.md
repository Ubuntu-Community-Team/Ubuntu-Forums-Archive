---
title: "&quot;Activate&quot; a partition"
date: 2008-09-10
forum: Hardware
---

### Post by langemyr on 2008-09-10
I just recently installed Ubuntu into my laptop and divided my hard drive into two partitions. Both ex2. I am a new-beginner on linux/ubuntu and are not sure on how to activate the other one.

---

### Post by Liviu-Theodor on 2008-09-10
> **langemyr said:**
> I just recently installed Ubuntu into my laptop and divided my hard drive into two partitions. Both ex2. I am a new-beginner on linux/ubuntu and are not sure on how to activate the other one.

What do you mean by "activate"? You don't have access to it?

And one question: did you declared on of partitions as swap? If so, you can not access it, because it is used only by Linux, as virtual memory.

---

### Post by langemyr on 2008-09-10
By activate: So that I can use the other partition, because I cant "find" it nor store anything in it.
Think i created 2 partitions with ex2 and 1 small one as a virtual memory drive or something.

---

### Post by Liviu-Theodor on 2008-09-10
Try to remember, when you installed ubuntu, you mounted one partition as "[FONT="Courier New"]/[/FONT]" (because ubuntu, and any Linux, requires one such partition) and with the other one, what have you done? Usually it is declared as "[FONT="Courier New"]/home[/FONT]". And, unless the partition are small, it is better to use the **ext3** filesystem rather than **ext2**. The best use for an **ext2** partition would be a separated "[FONT="Courier New"]/boot[/FONT]" and/or "[FONT="Courier New"]/tmp[/FONT]" partition.

So, if it is mounted with a specific name, you just need to use it normally as a folder (if you write to that specific folder, it will be used that specific partition, with no need to worry, as in Windows, which drive letter to use).

---

### Post by IntuitiveNipple on 2008-09-10
Please copy the output of the following commands into a reply so we can understand the PC configuration:

```

ls -l /dev/disk/by-id

for DEV in $(ls -1 /dev/[sh]d?); do echo ${DEV}; fdisk -lu /dev/${DEV}; done

mount

```

---

### Post by langemyr on 2008-09-10
"ls -l /dev/disk/by-id" gave me:

[I]lrwxrwxrwx 1 root root  9 2008-09-10 18:11 ata-Hitachi_HTS541612J9SA00_SB3D41E5KJDY7E -> ../../sda
lrwxrwxrwx 1 root root 10 2008-09-10 18:11 ata-Hitachi_HTS541612J9SA00_SB3D41E5KJDY7E-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-09-10 18:11 ata-Hitachi_HTS541612J9SA00_SB3D41E5KJDY7E-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-09-10 18:11 ata-Hitachi_HTS541612J9SA00_SB3D41E5KJDY7E-part3 -> ../../sda3
lrwxrwxrwx 1 root root  9 2008-09-10 18:11 scsi-1ATA_Hitachi_HTS541612J9SA00_SB3D41E5KJDY7E -> ../../sda
lrwxrwxrwx 1 root root 10 2008-09-10 18:11 scsi-1ATA_Hitachi_HTS541612J9SA00_SB3D41E5KJDY7E-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-09-10 18:11 scsi-1ATA_Hitachi_HTS541612J9SA00_SB3D41E5KJDY7E-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-09-10 18:11 scsi-1ATA_Hitachi_HTS541612J9SA00_SB3D41E5KJDY7E-part3 -> ../../sda3
[/I]


"for DEV in $(ls -1 /dev/[sh]d?); do echo ${DEV}; fdisk -lu /dev/${DEV}; done

mount" Gave me:

[I]/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda1 on /home type ext2 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/langemyr/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=langemyr)
[/I]

---

### Post by IntuitiveNipple on 2008-09-10
> **langemyr said:**
> 
"for DEV in $(ls -1 /dev/[sh]d?); do echo ${DEV}; fdisk -lu /dev/${DEV}; done

This should be executed as a single command, not with 'mount'. Here iss what the result should look like:
```

for DEV in $(ls -1 /dev/[sh]d?); do echo ${DEV}; fdisk -lu /dev/${DEV}; done

/dev/sda
/dev/sdb
/dev/sdc
/dev/sdd
/dev/sde
/dev/sdf
/dev/sdg
/dev/sdh
/dev/sdi

```
In your case I'd only expect to see:
```

/dev/sda

```

> **langemyr said:**
> 
mount" Gave me:

[I]/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda1 on /home type ext2 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/langemyr/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=langemyr)
[/I]
That output shows you've got the first partition (/dev/sda1) as the mount-point for /home/ and the second partition (/dev/sda2) as the mount-point for the root (/) file-system. That's two partitions so far. No sign of a swap partition.

In addition, the output of "ls -l /dev/disk/by-id" shows there is a third partition (/dev/sda3) that is currently not used.

If you can retry the fdisk command on the disk we might get a clearer idea of what is what:
```

sudo fdisk -ul /dev/sda

```
Please also report the results of:
```

for VOL in $(ls -1 /dev/sda?); do echo $VOL; vol_id ${VOL}; done

```

I'm wondering why the /home/ file-system is only ext2? It would be preferable to have it as ext3 since the journalling is a useful protection against unexpected crashes or incomplete writes.

---

### Post by langemyr on 2008-09-11
"sudo fdisk -ul /dev/sda":

[I]
Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    97659134    48829536   83  Linux
/dev/sda2   *    97659135   226628954    64484910   83  Linux
/dev/sda3       226628955   234436544     3903795   82  Linux swap / Solaris
[/i]

"for VOL in $(ls -1 /dev/sda?); do echo $VOL; vol_id ${VOL}; done":
[i] sudo mount /dev/sda3 /media/Floppy
/dev/sda3 looks like swapspace - not mounted
mount: you must specify the filesystem type

/dev/sda1
/dev/sda1: error opening volume
/dev/sda2
/dev/sda2: error opening volume
/dev/sda3
/dev/sda3: error opening volume
[/i]


I also tried (which i found after searching abit on the forums):
sudo mkdir /media/Floppy

and then:
sudo mount /dev/sda3 /media/Floppy

and I got.. in return:
/dev/sda3 looks like swapspace - not mounted
mount: you must specify the filesystem type

---

