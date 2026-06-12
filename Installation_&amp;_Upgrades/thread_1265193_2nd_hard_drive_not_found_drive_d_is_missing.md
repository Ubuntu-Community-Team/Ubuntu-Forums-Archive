---
title: "2nd hard drive not found drive d is missing"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by ongandrew on 2009-09-13
hi am new here and just installed ubuntu on my workstation and i have installed it fine but one things not right i can't seem to find my drive d: or my 2nd hd i have formatted my windows xp and created a partition for c and d but i can't find d i'm using ubuntu as my main os hope you could help me out

---

### Post by x33a on 2009-09-13
how many hard drives have you got?

open a terminal -> alt+f2, type gnome-terminal.

in the terminal type
```
sudo fdisk -l
```
and post the output here.

note: the command contains small L, not 1 (one).

---

### Post by ongandrew on 2009-09-13
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8440de0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x06dc0f19

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10336    78140128+   7  HPFS/NTFS

how do i enable my sdb1 caus i can't seem to access it atm

---

### Post by newsoft on 2009-09-13
How many hard drives do u have?

---

### Post by Moop on 2009-09-13
If your 2nd harddrive was plugged in when you installed ubuntu it should show up in the Places menu as 80GB File System. If you still have trouble check out the mounting windows tutorial here.  [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by ongandrew on 2009-09-13
have 2 drives and one is missing

---

### Post by louieb on 2009-09-13
have you looked in Places>Removable media? 
Know it sounds odd but thats where it should be listed.

---

### Post by ongandrew on 2009-09-13
its listed alright but i can't seem to put files into it i have used the ntfs config but it still doesn't work and the enable write to internal drives aren't clickable

---

### Post by louieb on 2009-09-13
I have a stock install of Jaunty on the my laptop. Don't remember doing anything special to be able to read and write to the partition XP is installed in.  Just click on it, it opens in the file browser (Nautilus) - can do anything I want - even delete files I should not.    

Maybe the partition is is flagged as dirty. Might what to boot windows and run chkdsk on it.

---

### Post by ongandrew on 2009-09-13
it has nothing in it it was just a formatted before i installed linux on my workstation..i see it but can't write on it even if i have the ntfs...

here is the updated fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8440de0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06dc0f19

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9728    78140128+   7  HPFS/NTFS

---

### Post by ongandrew on 2009-09-14
could anyone help me out on my problem

---

### Post by louieb on 2009-09-14
How did you partition and format the drive? What have you been doing? Have you been into the BIOS setup? 

For some reason the geometry of the drive has changed now I'm wondering if the drive is in good condition.  The 2nd one does looks like what I would expect.

first fdisk 
```

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
[COLOR=Red]240 heads, 63 sectors/track, 10337 cylinders[/COLOR]
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x06dc0f19

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10336    78140128+   7  HPFS/NTFS

```
2nd fdisk
```

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
[COLOR=Red]255 heads, 63 sectors/track, 9729 cylinders[/COLOR]
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06dc0f19

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9728    78140128+   7  HPFS/NTFS 	

```

What happens when you click on it in the Places menu?

Lest see what is going on: right after trying to open it please post the output of: 
```
dmesg | tail
```
and
```
mount
```
and 
```
sudo blkid -c /dev/null
```

---

### Post by ongandrew on 2009-09-14
for dmesg

[61596.009833] psmouse.c: bad data from KBC - timeout
[61596.603280] psmouse.c: Explorer Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
[61596.838442] psmouse.c: resync failed, issuing reconnect request
[61597.147516] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[61599.075610] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[61599.537649] psmouse serio1: ID: 10 00 64<4>logips2pp: Detected unknown logitech mouse model 103
[61600.073336] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input6
[62176.506919] psmouse.c: Explorer Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
[62454.847755] psmouse.c: Explorer Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
[62937.051261] psmouse.c: Explorer Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.

for mount 

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/andrew/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=andrew)
/dev/sdb1 on /media/disk type ext2 (rw,nosuid,nodev,uhelper=hal)

and sudo blkid

/dev/sda1: UUID="9e6ae540-72b0-4a56-9029-fba54f081fe2" TYPE="ext3" 
/dev/sda5: UUID="0b5ed2f4-929b-483d-b7eb-0b07c48a0295" TYPE="swap" 
/dev/sdb1: UUID="3987018e-df00-470e-9298-785a0a963309" TYPE="ext2" 

that's it hope you could help me out...

the reason why the geometry has changed because i have formatted my workstation again i thought i have done something wrong that is why the 2nd drive can't be accessible i have found the 2nd drive but the problem is i can't write on it i can't put files and stuff on it

---

### Post by ongandrew on 2009-09-14
I have fixed the problem :D i have formatted my pc and made my 160 gb my /home and 80 gb to the / :D and am happy with it hope theres no problem with what i did

---

### Post by louieb on 2009-09-14
Glad you got it working. Way you did it will be  just fine. 

Think I found why you had a problem in the first place. Just a guess the cause for that was an incorrect entry for sdb1 in file /etc/fstab.  

Looks like -  Linux was confused fdisk showed it to be NTFS  

```
/dev/sdb1               1        9728    78140128+   7  [COLOR=Red]HPFS/NTFS[/COLOR]
```but mount and blkid showed it to be ext2
```
/dev/sdb1 on /media/disk type [COLOR=Red]ext2[/COLOR] (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1: UUID="3987018e-df00-470e-9298-785a0a963309" TYPE="[COLOR=Red]ext2[/COLOR]" 
```

---

### Post by ongandrew on 2009-09-14
oh ok but anyway thnx for the help :D

---

