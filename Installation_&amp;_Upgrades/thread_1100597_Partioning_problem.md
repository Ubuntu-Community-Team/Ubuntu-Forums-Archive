---
title: "Partioning problem"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by moody7890 on 2009-03-19
i have ubuntu 8.04 live cd and when i try to install it i receive during installation partioning only two choices:
1- use entire disk
2-manual
i have 4 ntfs partitions and 1 etx3 and windows vista on one ntfs partion 
i don't want to remove vista or any data on other ntfs partitions 
when i choose manual i don't find any of my partitions despite that i find all my partitions in home folder and i can access and modify them freely
please help me 
thank u

---

### Post by thebitguru on 2009-03-19
Are you comfortable with command line?  Run the terminal application and paste the output to the following command.

```
fdisk -l /dev/sda
```

Depending on your hardware you might have to do hda instead of sda.

---

### Post by moody7890 on 2009-03-19
i receive :
Cannot open /dev/sda

---

### Post by thebitguru on 2009-03-19
Make sure you are root, 'sudo -i'.  Also, try /dev/hda if it still can't open sda.

---

### Post by moody7890 on 2009-03-19
i recreive :

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7bab2cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+   7  HPFS/NTFS
/dev/sda2            2433       19457   136753312+   f  W95 Ext'd (LBA)
/dev/sda3           16710       18090    11088896    7  HPFS/NTFS
/dev/sda5            2433       10942    68356543+   7  HPFS/NTFS
/dev/sda6           10943       16709    46323396    7  HPFS/NTFS
/dev/sda7           18091       19457    10980396   83  Linux
root@ubuntu:~#

---

### Post by thebitguru on 2009-03-19
Hmm... all of your partitions are listed so I am not sure why the manual partitioning step won't show you the Linux ones.  Which of these seven partitions do you see?

---

### Post by moody7890 on 2009-03-19
none

---

### Post by moody7890 on 2009-03-19
hello are you still here

---

### Post by thebitguru on 2009-03-19
Sorry, had to get back to work.  Anyways, try this.  Instead of using the 'install' link on the desktop, open a terminal and run 'sudo ubiquity'.  See if you see the partition this way.

---

### Post by moody7890 on 2009-03-19
i get the same result

---

### Post by moody7890 on 2009-03-19
Please help me

---

### Post by moody7890 on 2009-03-20
Doesn't this problem have a solution or what?

---

### Post by moody7890 on 2009-03-21
shall i search for another package of linux then?

---

### Post by thebitguru on 2009-03-21
Can you post the contents of /var/log/partman?  That might have some clues about the problem.

Also, are you using 8.04 instead of 8.10 for a reason?  I am guessing that with 8.10 you might have better luck (but that's not an excuse for things to not work in 8.04 :))

[http://manpages.ubuntu.com/manpages/hardy/man8/ubiquity.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/ubiquity.8.html)

---

### Post by moody7890 on 2009-03-22
/bin/partman: *******************************************************
/lib/partman/init.d/30parted: *******************************************************
parted_server: ======= Starting the server
parted_server: main_loop: iteration 1
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: OPEN =dev=sda /dev/sda
parted_server: Read command: OPEN
parted_server: command_open()
parted_server: Request to open =dev=sda
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Note =dev=sda as unchanged
parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 2
parted_server: Opening infifo
/lib/partman/init.d/35dump: *******************************************************
/lib/partman/init.d/35dump: IN: DUMP =dev=sda
parted_server: Read command: DUMP
parted_server: command_dump()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 3
parted_server: Opening infifo
Device: yes
Model: ATA WDC WD1600AABS-0
Path: /dev/sda
Sector size: 512
Sectors: 312581808
Sectors/track: 63
Heads: 255
Cylinders: 19457
Partition table: no
/lib/partman/init.d/70update_partitions: *******************************************************
/lib/partman/init.d/70update_partitions: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 4
parted_server: Opening infifo
/lib/partman/init.d/75auto_mountpoints: *******************************************************
/lib/partman/init.d/80autouse_swap: *******************************************************
/lib/partman/init.d/80autouse_swap: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 5
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 6
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 7
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sda
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 8
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: Unable to get maximum primary partition count on /var/lib/partman/devices/=dev=sda
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sda', totalfree: '0', diskfree: '0', diskpart: 'none', diskpath: 'none'
/lib/partman/automatically_partition/10resize_use_free/choices: Found no resizable partitions
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 9
parted_server: Opening infifo
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/lib/partman/automatically_partition/20some_device/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 10
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 11
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sda
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 12
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: Unable to get maximum primary partition count on /var/lib/partman/devices/=dev=sda
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sda', totalfree: '0', diskfree: '0', diskpart: 'none', diskpath: 'none'
/lib/partman/automatically_partition/10resize_use_free/choices: Found no resizable partitions
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 13
parted_server: Opening infifo
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/bin/partman: IN: QUIT
parted_server: Read command: QUIT
parted_server: Quitting

---

### Post by thebitguru on 2009-03-22
Based on [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/288675](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/288675), I think the fact that you are seeing the existing partitions is what is causing the problem.  Let's try to unmount those.  Can you paste the output of the following command?

```
mount
```

This will show you several lines like the ones below...

```

/dev/sda1 on /media/part2 type ntfs (rw,relatime)
/dev/sda2 on /media/part1 type ntfs (rw,relatime)

```

You need to unmount the ones that start with /dev/sda using 'umount', e.g. 'umount /dev/sda1'.  After doing this restart the install program (don't reboot) and hopefully you will see the partitions.

---

### Post by moody7890 on 2009-03-22
it didn't work

---

### Post by thebitguru on 2009-03-22
Can you paste the output of 'mount' after you have unmounted?  Also, can you paste the partman log file?

---

### Post by moody7890 on 2009-03-22
ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

---

### Post by moody7890 on 2009-03-22
/bin/partman: *******************************************************
/lib/partman/init.d/30parted: *******************************************************
parted_server: ======= Starting the server
parted_server: main_loop: iteration 1
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: OPEN =dev=sda /dev/sda
parted_server: Read command: OPEN
parted_server: command_open()
parted_server: Request to open =dev=sda
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Note =dev=sda as unchanged
parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 2
parted_server: Opening infifo
/lib/partman/init.d/35dump: *******************************************************
/lib/partman/init.d/35dump: IN: DUMP =dev=sda
parted_server: Read command: DUMP
parted_server: command_dump()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 3
parted_server: Opening infifo
Device: yes
Model: ATA WDC WD1600AABS-0
Path: /dev/sda
Sector size: 512
Sectors: 312581808
Sectors/track: 63
Heads: 255
Cylinders: 19457
Partition table: no
/lib/partman/init.d/70update_partitions: *******************************************************
/lib/partman/init.d/70update_partitions: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 4
parted_server: Opening infifo
/lib/partman/init.d/75auto_mountpoints: *******************************************************
/lib/partman/init.d/80autouse_swap: *******************************************************
/lib/partman/init.d/80autouse_swap: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 5
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 6
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 7
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sda
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 8
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: Unable to get maximum primary partition count on /var/lib/partman/devices/=dev=sda
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sda', totalfree: '0', diskfree: '0', diskpart: 'none', diskpath: 'none'
/lib/partman/automatically_partition/10resize_use_free/choices: Found no resizable partitions
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 9
parted_server: Opening infifo
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/lib/partman/automatically_partition/20some_device/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 10
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 11
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sda
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 12
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: Unable to get maximum primary partition count on /var/lib/partman/devices/=dev=sda
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sda', totalfree: '0', diskfree: '0', diskpart: 'none', diskpath: 'none'
/lib/partman/automatically_partition/10resize_use_free/choices: Found no resizable partitions
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 13
parted_server: Opening infifo
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/bin/partman: IN: QUIT
parted_server: Read command: QUIT
parted_server: Quitting
/bin/partman: *******************************************************
/lib/partman/init.d/30parted: *******************************************************
parted_server: ======= Starting the server
parted_server: main_loop: iteration 1
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: OPEN =dev=sda /dev/sda
parted_server: Read command: OPEN
parted_server: command_open()
parted_server: Request to open =dev=sda
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Note =dev=sda as unchanged
parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 2
parted_server: Opening infifo
/lib/partman/init.d/35dump: *******************************************************
/lib/partman/init.d/35dump: IN: DUMP =dev=sda
parted_server: Read command: DUMP
parted_server: command_dump()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 3
parted_server: Opening infifo
Device: yes
Model: ATA WDC WD1600AABS-0
Path: /dev/sda
Sector size: 512
Sectors: 312581808
Sectors/track: 63
Heads: 255
Cylinders: 19457
Partition table: no
/lib/partman/init.d/70update_partitions: *******************************************************
/lib/partman/init.d/70update_partitions: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 4
parted_server: Opening infifo
/lib/partman/init.d/75auto_mountpoints: *******************************************************
/lib/partman/init.d/80autouse_swap: *******************************************************
/lib/partman/init.d/80autouse_swap: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 5
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 6
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 7
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sda
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 8
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: Unable to get maximum primary partition count on /var/lib/partman/devices/=dev=sda
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sda', totalfree: '0', diskfree: '0', diskpart: 'none', diskpath: 'none'
/lib/partman/automatically_partition/10resize_use_free/choices: Found no resizable partitions
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 9
parted_server: Opening infifo
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/lib/partman/automatically_partition/20some_device/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 10
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 11
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sda
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 12
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: Unable to get maximum primary partition count on /var/lib/partman/devices/=dev=sda
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sda', totalfree: '0', diskfree: '0', diskpart: 'none', diskpath: 'none'
/lib/partman/automatically_partition/10resize_use_free/choices: Found no resizable partitions
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 13
parted_server: Opening infifo
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/45auto/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 14
parted_server: Opening infifo
/bin/partman: IN: QUIT
parted_server: Read command: QUIT
parted_server: Quitting
/bin/partman: *******************************************************
/lib/partman/init.d/30parted: *******************************************************
parted_server: ======= Starting the server
parted_server: main_loop: iteration 1
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: OPEN =dev=sda /dev/sda
parted_server: Read command: OPEN
parted_server: command_open()
parted_server: Request to open =dev=sda
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Note =dev=sda as unchanged
parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 2
parted_server: Opening infifo
/lib/partman/init.d/35dump: *******************************************************
/lib/partman/init.d/35dump: IN: DUMP =dev=sda
parted_server: Read command: DUMP
parted_server: command_dump()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 3
parted_server: Opening infifo
Device: yes
Model: ATA WDC WD1600AABS-0
Path: /dev/sda
Sector size: 512
Sectors: 312581808
Sectors/track: 63
Heads: 255
Cylinders: 19457
Partition table: no
/lib/partman/init.d/70update_partitions: *******************************************************
/lib/partman/init.d/70update_partitions: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 4
parted_server: Opening infifo
/lib/partman/init.d/75auto_mountpoints: *******************************************************
/lib/partman/init.d/80autouse_swap: *******************************************************
/lib/partman/init.d/80autouse_swap: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 5
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 6
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 7
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sda
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 8
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: Unable to get maximum primary partition count on /var/lib/partman/devices/=dev=sda
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sda', totalfree: '0', diskfree: '0', diskpart: 'none', diskpath: 'none'
/lib/partman/automatically_partition/10resize_use_free/choices: Found no resizable partitions
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 9
parted_server: Opening infifo
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/lib/partman/automatically_partition/20some_device/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 10
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 11
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sda
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 12
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: Unable to get maximum primary partition count on /var/lib/partman/devices/=dev=sda
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sda', totalfree: '0', diskfree: '0', diskpart: 'none', diskpath: 'none'
/lib/partman/automatically_partition/10resize_use_free/choices: Found no resizable partitions
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 13
parted_server: Opening infifo
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/45auto/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 14
parted_server: Opening infifo
/bin/partman: IN: QUIT
parted_server: Read command: QUIT
parted_server: Quitting
/bin/partman: *******************************************************
/lib/partman/init.d/30parted: *******************************************************
parted_server: ======= Starting the server
parted_server: main_loop: iteration 1
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: OPEN =dev=sda /dev/sda
parted_server: Read command: OPEN
parted_server: command_open()
parted_server: Request to open =dev=sda
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Note =dev=sda as unchanged
parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 2
parted_server: Opening infifo
/lib/partman/init.d/35dump: *******************************************************
/lib/partman/init.d/35dump: IN: DUMP =dev=sda
parted_server: Read command: DUMP
parted_server: command_dump()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 3
parted_server: Opening infifo
Device: yes
Model: ATA WDC WD1600AABS-0
Path: /dev/sda
Sector size: 512
Sectors: 312581808
Sectors/track: 63
Heads: 255
Cylinders: 19457
Partition table: no
/lib/partman/init.d/70update_partitions: *******************************************************
/lib/partman/init.d/70update_partitions: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 4
parted_server: Opening infifo
/lib/partman/init.d/75auto_mountpoints: *******************************************************
/lib/partman/init.d/80autouse_swap: *******************************************************
/lib/partman/init.d/80autouse_swap: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 5
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 6
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 7
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sda
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 8
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: Unable to get maximum primary partition count on /var/lib/partman/devices/=dev=sda
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sda', totalfree: '0', diskfree: '0', diskpart: 'none', diskpath: 'none'
/lib/partman/automatically_partition/10resize_use_free/choices: Found no resizable partitions
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 9
parted_server: Opening infifo
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/lib/partman/automatically_partition/20some_device/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 10
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 11
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sda
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 12
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: Unable to get maximum primary partition count on /var/lib/partman/devices/=dev=sda
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sda', totalfree: '0', diskfree: '0', diskpart: 'none', diskpath: 'none'
/lib/partman/automatically_partition/10resize_use_free/choices: Found no resizable partitions
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 13
parted_server: Opening infifo
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/45auto/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 14
parted_server: Opening infifo
/bin/partman: IN: QUIT
parted_server: Read command: QUIT
parted_server: Quitting
/bin/partman: *******************************************************
/lib/partman/init.d/30parted: *******************************************************
parted_server: ======= Starting the server
parted_server: main_loop: iteration 1
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: OPEN =dev=sda /dev/sda
parted_server: Read command: OPEN
parted_server: command_open()
parted_server: Request to open =dev=sda
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Note =dev=sda as unchanged
parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 2
parted_server: Opening infifo
/lib/partman/init.d/35dump: *******************************************************
/lib/partman/init.d/35dump: IN: DUMP =dev=sda
parted_server: Read command: DUMP
parted_server: command_dump()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 3
parted_server: Opening infifo
Device: yes
Model: ATA WDC WD1600AABS-0
Path: /dev/sda
Sector size: 512
Sectors: 312581808
Sectors/track: 63
Heads: 255
Cylinders: 19457
Partition table: no
/lib/partman/init.d/70update_partitions: *******************************************************
/lib/partman/init.d/70update_partitions: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 4
parted_server: Opening infifo
/lib/partman/init.d/75auto_mountpoints: *******************************************************
/lib/partman/init.d/80autouse_swap: *******************************************************
/lib/partman/init.d/80autouse_swap: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 5
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 6
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 7
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sda
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 8
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: Unable to get maximum primary partition count on /var/lib/partman/devices/=dev=sda
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sda', totalfree: '0', diskfree: '0', diskpart: 'none', diskpath: 'none'
/lib/partman/automatically_partition/10resize_use_free/choices: Found no resizable partitions
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 9
parted_server: Opening infifo
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/lib/partman/automatically_partition/20some_device/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 10
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 11
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sda
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 12
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: Unable to get maximum primary partition count on /var/lib/partman/devices/=dev=sda
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sda', totalfree: '0', diskfree: '0', diskpart: 'none', diskpath: 'none'
/lib/partman/automatically_partition/10resize_use_free/choices: Found no resizable partitions
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 13
parted_server: Opening infifo
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/45auto/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 14
parted_server: Opening infifo
/bin/partman: IN: QUIT
parted_server: Read command: QUIT
parted_server: Quitting
/bin/partman: *******************************************************
/lib/partman/init.d/30parted: *******************************************************
parted_server: ======= Starting the server
parted_server: main_loop: iteration 1
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: OPEN =dev=sda /dev/sda
parted_server: Read command: OPEN
parted_server: command_open()
parted_server: Request to open =dev=sda
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Note =dev=sda as unchanged
parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 2
parted_server: Opening infifo
/lib/partman/init.d/35dump: *******************************************************
/lib/partman/init.d/35dump: IN: DUMP =dev=sda
parted_server: Read command: DUMP
parted_server: command_dump()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 3
parted_server: Opening infifo
Device: yes
Model: ATA WDC WD1600AABS-0
Path: /dev/sda
Sector size: 512
Sectors: 312581808
Sectors/track: 63
Heads: 255
Cylinders: 19457
Partition table: no
/lib/partman/init.d/70update_partitions: *******************************************************
/lib/partman/init.d/70update_partitions: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 4
parted_server: Opening infifo
/lib/partman/init.d/75auto_mountpoints: *******************************************************
/lib/partman/init.d/80autouse_swap: *******************************************************
/lib/partman/init.d/80autouse_swap: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 5
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 6
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 7
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sda
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 8
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: Unable to get maximum primary partition count on /var/lib/partman/devices/=dev=sda
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sda', totalfree: '0', diskfree: '0', diskpart: 'none', diskpath: 'none'
/lib/partman/automatically_partition/10resize_use_free/choices: Found no resizable partitions
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 9
parted_server: Opening infifo
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/lib/partman/automatically_partition/20some_device/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 10
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 11
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sda
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 12
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: Unable to get maximum primary partition count on /var/lib/partman/devices/=dev=sda
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sda', totalfree: '0', diskfree: '0', diskpart: 'none', diskpath: 'none'
/lib/partman/automatically_partition/10resize_use_free/choices: Found no resizable partitions
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: No partitions
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 13
parted_server: Opening infifo
/lib/partman/automatically_partition/80custom/choices: *******************************************************

---

### Post by thebitguru on 2009-03-22
Weird, it still can't find the partition table.

```

parted_server: Opening infifo
Device: yes
Model: ATA WDC WD1600AABS-0
Path: /dev/sda
Sector size: 512
Sectors: 312581808
Sectors/track: 63
Heads: 255
Cylinders: 19457
Partition table: no

```

Sorry, I am out of ideas.  Does anyone else have any ideas?

---

### Post by hexanol on 2009-03-22
Maybe you could give the output of "sudo parted /dev/sda unit s print" and also "sudo dd if=/dev/sda bs=512 count=1 | od -Ax -tx1z" ?

---

### Post by moody7890 on 2009-03-23
ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Error: Cannot have overlapping partitions.                                
Information: Don't forget to update /etc/fstab, if necessary.             

ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=512 count=1 | od -Ax -tx1z
000000 33 c0 8e d0 bc 00 7c 8e c0 8e d8 be 00 7c bf 00  >3.....|......|..<
1+0 records in
1+0 records out
512 bytes (512 B) copied, 4.3088e-05 s, 11.9 MB/s
000010 06 b9 00 02 fc f3 a4 50 68 1c 06 cb fb b9 04 00  >.......Ph.......<
000020 bd be 07 80 7e 00 00 7c 0b 0f 85 10 01 83 c5 10  >....~..|........<
000030 e2 f1 cd 18 88 56 00 55 c6 46 11 05 c6 46 10 00  >.....V.U.F...F..<
000040 b4 41 bb aa 55 cd 13 5d 72 0f 81 fb 55 aa 75 09  >.A..U..]r...U.u.<
000050 f7 c1 01 00 74 03 fe 46 10 66 60 80 7e 10 00 74  >....t..F.f`.~..t<
000060 26 66 68 00 00 00 00 66 ff 76 08 68 00 00 68 00  >&fh....f.v.h..h.<
000070 7c 68 01 00 68 10 00 b4 42 8a 56 00 8b f4 cd 13  >|h..h...B.V.....<
000080 9f 83 c4 10 9e eb 14 b8 01 02 bb 00 7c 8a 56 00  >............|.V.<
000090 8a 76 01 8a 4e 02 8a 6e 03 cd 13 66 61 73 1e fe  >.v..N..n...fas..<
0000a0 4e 11 0f 85 0c 00 80 7e 00 80 0f 84 8a 00 b2 80  >N......~........<
0000b0 eb 82 55 32 e4 8a 56 00 cd 13 5d eb 9c 81 3e fe  >..U2..V...]...>.<
0000c0 7d 55 aa 75 6e ff 76 00 e8 8a 00 0f 85 15 00 b0  >}U.un.v.........<
0000d0 d1 e6 64 e8 7f 00 b0 df e6 60 e8 78 00 b0 ff e6  >..d......`.x....<
0000e0 64 e8 71 00 b8 00 bb cd 1a 66 23 c0 75 3b 66 81  >d.q......f#.u;f.<
0000f0 fb 54 43 50 41 75 32 81 f9 02 01 72 2c 66 68 07  >.TCPAu2....r,fh.<
000100 bb 00 00 66 68 00 02 00 00 66 68 08 00 00 00 66  >...fh....fh....f<
000110 53 66 53 66 55 66 68 00 00 00 00 66 68 00 7c 00  >SfSfUfh....fh.|.<
000120 00 66 61 68 00 00 07 cd 1a 5a 32 f6 ea 00 7c 00  >.fah.....Z2...|.<
000130 00 cd 18 a0 b7 07 eb 08 a0 b6 07 eb 03 a0 b5 07  >................<
000140 32 e4 05 00 07 8b f0 ac 3c 00 74 fc bb 07 00 b4  >2.......<.t.....<
000150 0e cd 10 eb f2 2b c9 e4 64 eb 00 24 02 e0 f8 24  >.....+..d..$...$<
000160 02 c3 49 6e 76 61 6c 69 64 20 70 61 72 74 69 74  >..Invalid partit<
000170 69 6f 6e 20 74 61 62 6c 65 00 45 72 72 6f 72 20  >ion table.Error <
000180 6c 6f 61 64 69 6e 67 20 6f 70 65 72 61 74 69 6e  >loading operatin<
000190 67 20 73 79 73 74 65 6d 00 4d 69 73 73 69 6e 67  >g system.Missing<
0001a0 20 6f 70 65 72 61 74 69 6e 67 20 73 79 73 74 65  > operating syste<
0001b0 6d 00 00 00 00 62 7a 99 cc b2 ba b7 00 00 80 01  >m....bz.........<
0001c0 01 00 07 fe ff ff 3f 00 00 00 41 29 54 02 00 fe  >......?...A)T...<
0001d0 ff ff 0f fe ff ff 80 29 54 02 41 61 4d 10 00 fe  >.......)T.AaM...<
0001e0 ff ff 07 fe ff ff 00 f0 ff 0f 00 68 52 01 00 00  >...........hR...<
0001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa  >..............U.<
000200
ubuntu@ubuntu:~$

---

### Post by hexanol on 2009-03-25
Hey, sorry for the late answer, I actually forgot I had post something on those forums... hehe.

Well, you have a classic case of "overlapping partitions", where you have a primary partition located inside your "extended partition". Some partition editor (like parted and gparted, the latter is the one used when you install Ubuntu in "manual" partitioning mode) doesn't like those situation and won't let you do anything in these situations.

So, how can you repair that ? Well, I know two way to do so. First, you can use "sfdisk"; I have some knowledge on what to do but since I have never done it, I can't really help you right now. Second, you can manually edit your partition (i.e. rewrite raw sectors), I already done it 3 times in the past (I actually did it for someone on this forum once), but it's time consuming (and error-prone) and right now I don't have the time.

One day I might write some utility who would automatically repair those kind of situation... if it does not already exist...

---

### Post by moody7890 on 2009-03-29
i can't understand what you mean but pclinuxos reads the partitions fine and can be installed what's the problem with ubuntu then?

---

### Post by moody7890 on 2009-03-30
does anyone have a suggestion

---

### Post by hexanol on 2009-04-01
Well, I guess that pclinux doesn't use libparted to read your partition table (or use a more recent version -- don't know) and tolerate overlapping partition (and this is ok since it's only a what I would call "logical overlapping").

The problem is really in your primary partition table. You can fix this either by hand, with sfdisk or with a application who might not exist yet. To prove you I'm right, in pclinux, open a console/terminal window and type "sudo parted -l" (does pclinux use sudo? if not, then log on with root). It will tell you you have overlapping partition (if parted is installed, of course).

---

