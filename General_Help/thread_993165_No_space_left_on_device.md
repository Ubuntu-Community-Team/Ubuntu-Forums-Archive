---
title: "No space left on device"
date: 2008-11-25
forum: General Help
---

### Post by kzm. on 2008-11-25
Hey.

not sure what's going on.. i searched online and found million of entries but non seemed to provide a solution. 

i run a headless ubuntu server 6.06 LTS. last time i logged in through ssh i tried to install a hp printer for the network. when i try to do anything (download, edit files etc) now i get always: **No Space left on device**

and i dont get why? as you can see are inodes are fine.. though my Ubuntu-root is total filled up! but if i look with du and ignore my /mnt/ folder it all looks good... ?que?

$ df -i 
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/mapper/Ubuntu-root
                     4669440   98324 4571116    3% /
varrun                 63472      52   63420    1% /var/run
varlock                63472       4   63468    1% /var/lock
udev                   63472     875   62597    2% /dev
devshm                 63472       1   63471    1% /dev/shm
/dev/hda5             124496      30  124466    1% /boot
/dev/mapper/fuji     122109952 1907304 120202648    2% /mnt/fuji

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/Ubuntu-root
                       36G   35G     0 100% /
varrun                248M  128K  248M   1% /var/run
varlock               248M  4.0K  248M   1% /var/lock
udev                  248M  124K  248M   1% /dev
devshm                248M     0  248M   0% /dev/shm
/dev/hda5             228M   14M  203M   7% /boot
/dev/mapper/fuji      917G  632G  240G  73% /mnt/fuji

/$ sudo du -hc --max-depth=1
Password:
48K	./lost+found
796M	./var
9.5M	./boot
12M	./etc
12K	./media
77M	./lib
986M	./usr
3.1M	./bin
244K	./dev
28M	./home
664G	./mnt
505M	./proc
28K	./root
8.5M	./sbin
4.0K	./tmp
0	./sys
4.0K	./srv
4.0K	./opt
4.0K	./initrd
124K	./svn
666G	.
666G	total

---

### Post by scottkicksbutt on 2008-11-25
kzm
your root filesystem is full:
36G 35G 0 100% /
My guess is that most of that 36G root filesystem is being consumed by something in your /mnt directory otherwise the math just doesnt add up.  If you can provide the output from the mount command and an ls -al from the /mnt directory, that would help.  A du -sm /mnt/* would help too but that may take a while to run on a .6TB hunk hunk of data that is apparently mounted under /mnt.

---

### Post by kzm. on 2008-11-25
hey scott.

appreciate your quick response!

I see the line that indicates my root harddisk is full.. but i do not understand how mounted harddisks can be the cause for it? the du on my root directory seems to give no hint what eats up its resources. that in mount i have 600gb does not surprise me as i have two 1tb harddisks mounted. could you explain to me why you think a mount could be the cause?

anyway here is the info you asked for (not sure what you mean with mount output.. i see a lot of "No space left on device" in the syslog and find nothing in messages or dmesg):

```
/mnt$ ls -al
total 48
drwxr-xr-x 12 root root 4096 2008-09-07 14:28 .
drwxr-xr-x 22 root root 4096 2008-11-25 18:53 ..
drwxr-xr-x  2 root root 4096 2008-07-14 17:43 backup
drwxr-xr-x  2 root root 4096 2008-07-14 17:43 DATA
drwxr-xr-x  2 root root 4096 2008-07-14 16:16 disk
drwxr-sr-x  6 kzm  babo 4096 2008-06-29 22:09 fuji
drwxr-sr-x  3 kzm  babo 4096 2008-06-29 22:09 granny
drwxr-xr-x  2 root root 4096 2008-07-14 16:16 hda
drwxr-xr-x  2 root root 4096 2008-07-15 19:37 linux
drwxr-xr-x  2 root root 4096 2008-07-14 17:43 SOFT
drwxr-xr-x  2 root root 4096 2008-07-14 17:43 STORE
drwxr-xr-x  2 root root 4096 2008-07-14 17:44 WIN_LIN_EX
```


```
/$ nano /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0   $
/dev/hda5       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/mapper/fuji  /mnt/fuji  ext3  defaults,user,grpid,suid,dev,noexec  0  0
/dev/mapper/granny      /mnt/granny     ext3    defaults,user,grpid,suid,dev,no$
```

```
/$ sudo du -sm /mnt/*
1	/mnt/backup
1	/mnt/DATA
1	/mnt/disk
646261	/mnt/fuji
33223	/mnt/granny
1	/mnt/hda
1	/mnt/linux
1	/mnt/SOFT
1	/mnt/STORE
1	/mnt/WIN_LIN_EX
```

---

### Post by kzm. on 2008-11-25
hmm.. found something weird, based on scotss coment about my /mnt/ folder

```
$ sudo umount /mnt/fuji/
Password:
$ sudo umount /mnt/granny/
umount: /mnt/granny/: not mounted
/$ sudo du -sm /mnt/*
1	/mnt/backup
1	/mnt/DATA
1	/mnt/disk
1	/mnt/fuji
33223	/mnt/granny
1	/mnt/hda
1	/mnt/linux
1	/mnt/SOFT
1	/mnt/STORE
1	/mnt/WIN_LIN_EX
```

:confused:

---

### Post by kzm. on 2008-11-25
Solution found... after i had shutdown the computer and unplugged the harddisk the 33gb wont go from the /mnt/granny ... it appears that items got written into that map rather than onto the harddisk!!

I now have to find out how that could happen as granny is only a shadow disk for another one to keep copies of the files.

thanks scott...i had a blindspot.

---

### Post by scottkicksbutt on 2008-11-25
Hey - 
so the math still does not add up.  We have established that we are missing about 30G of disk from the root filesystem - give or take.

Disk used under /mnt/fuji is:
646261	/mnt/fuji

yet the df -h shows
/dev/mapper/fuji 917G 632G 240G 73% /mnt/fuji

so du says 646 is used but df says 632 is used (that's about 30G difference).  So I would guess that somebody or something copied 30G to the /mnt/fuji directory while the physical disk was not mounted thereby eating up the root filesystem rather than the fuji disk. That's my best guess.  

so I would unmount the fuji disk and see what is left in the /mnt/fuji directory or ....

I just saw the last post. Im glad it's fixed - I figured it had to be something along those lines.

---

### Post by teddks on 2008-11-25
In the future, you can use the -x argument to du to see only results from that one filesystem.

---

### Post by silverglade00 on 2008-11-25
I'm sorry to interrupt, but I am cracking up at /mnt/fuji! Funny!

---

### Post by scottkicksbutt on 2008-11-25
I guess you missed /mnt/granny

---

