---
title: "reinstalling/creating a new /home"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by ToFue on 2009-03-24
Hey guys!
 I've managed to overwrite my /home partition with windows MBR crap, and have restored grub to functionality ( / partition remained untouched), and need to reinstall the /home directory after reformatting to get rid of the MBR stuff..  can someone point me to a thread please?

Many thanks!

---

### Post by ToFue on 2009-03-24
my Ubuntu install is the only disk I have plugged in right now (I'll tackle xp later)
/home should be on /dev/sda2, but is now blank

so here's what I had to do:

1) I booted from liveCD & opened terminal

in terminal, as sudo su - (or sudo every command, whatever you're comfy with)

```

fdisk -l

```

which gave me.. 

```

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a6885bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1945    15623181    f  W95 Ext'd (LBA)
/dev/sda2            1946        9349    59472630   83  Linux
/dev/sda3   *        9350       14946    44957902+  83  Linux
/dev/sda5               1        1945    15623149+  82  Linux swap / Solaris

```

2. I created a mount point for root, using /dev/sda3 which had my system files & existing /root directory on it..

```

mkdir /mnt/root

mount -t ext3 /dev/sda3 /mnt/root

```

3. then I made a mount point for proc so I can open dialog between utilities and the kernel for interfacing w/ the new filesystem (not sure that this was required)


```

mount -t proc none /mnt/root/proc

```

4. then I had to bind the devices(/dev) from the hard drive with a working mount point


```

mount -o bind /dev /mnt/root/dev

```

5. at this point I created a new user from the liveCD's menu system>administration>users&groups with identical username & pwd from my old account (i didn't put my 'real name' like i did on the first account, though) and then moved the account to the space that would be /home

```

mv /home/tofue /media/disk

```

where 'tofue' is the new username and 'disk' is what the liveCD recognized as the partition when mounted through nautilus.

6. I unmounted /media/disk and after reading a little more from my Red Hat Linux Bible, I found the following steps to set up a new file system on the partition that would become /home (/dev/sda2)

```

mkfs -t ext3 /dev/sda2

```

for whatever reason I rebooted.

during boot, I received errors telling me that there were broken links, and the boot process defaulted me to a terminal. I could have probably finished these next steps without the reboot, but oh well. now I was working directly from my install.

I didn't have to change /etc/passwd at all as the uid of the account defaulted to be the same as the old one. I would have probably had to alter it if I had more than one account, and this one was down the list, or other weird stuff

at this point all I really had to do next was to change the uuid value in /etc/fstab to the new partition/filesys uuid by:


A: acquiring the new uuid
```

vol_id -u

```

and

B: change the value in fstab:
```

vim /etc/fstab

```

not familiar w/ vim? press <Esc> to get into edit mode, make sure <Ins> is turned on, edit what needs to be, then <Esc> again to exit edit mode, and write to disk by using <:w!> then <:q!> to quit

###. so I found a command in the good book that lets me see and verify what filesystems are mounted to what devices, bound to what, and all..

```

df -h

```

which gave me..

```

root@ectotron:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              43G  6.2G   34G  16% /
tmpfs                 4.0G     0  4.0G   0% /lib/init/rw
varrun                4.0G  224K  4.0G   1% /var/run
varlock               4.0G     0  4.0G   0% /var/lock
udev                  4.0G  3.4M  3.9G   1% /dev
tmpfs                 4.0G  628K  4.0G   1% /dev/shm
lrm                   4.0G  2.4M  3.9G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda2              57G  181M   54G   1% /home
/dev/scd0             695M  695M     0 100% /media/cdrom0

```

so again, I rebooted. This time it was into my old environment- barren, but there (like comeing home after Katrina hit!)

and, Eureka, I was done.. though I still haven't cold-booted again to be certain, but I'm sure it's all cured! hehe (watch me eat my words!)

Thanks to all for all the suggestions (I'll be posting this in other forums where I opened a thread), and I hope this helps someone that finds themselves in a similar bind!  

:guitar:

---

