---
title: "Total user memory"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by brydong on 2007-06-19
I have a fairly new machine, under 3 months old. I was running 2 x 1GB of RAM. I just purchased and added 2 more giving me a total of 4x1GB or RAM. All that I've done to install is physically add the RAM.

If I run free -m, I see....

[~]$ free -m
             total       used       free     shared    buffers     cached
Mem:          3295       3151        144          0         24       2745
-/+ buffers/cache:        381       2914
Swap:            0          0          0

So it looks like I have 3.2GB of RAM. Does that make sense with 4GB?

It appears to be more than 3GB so I'm guessing the physical ram is functioning.

thanks,
brydon

---

### Post by steveneddy on 2007-06-19
Where is your swap partition? 

Do you have a swap partition?

It looks like you don't have swap, so this is why the OS is allocating some of the physical memory to swap. 

I may be off base here, maybe someone else knows more about this?

---

### Post by brydong on 2007-06-19
Oh right....well I have a separate issue where starting yesterday my swap doesn't show up when I start up.

I used to have swap, now I don't. No idea what that's about and haven't had time to look into that.

So if I get my swap back then I'll get all my ram? What's happening here is RAM is being reserved for swap?

thanks,
brydon

---

### Post by steveneddy on 2007-06-19
That's what it looks like to me.

---

### Post by CrispyFried on 2007-06-19
if youre running the 32 bit (i386) version the max memory + swap is 4 gigs, so if you want all your ram you have to run with no swap.

not sure why its not listing all 4 gigs as it seems you have no swap. does your video card use system ram?

what does "free -t" show?

---

### Post by brydong on 2007-06-20
free -t

             total       used       free     shared    buffers     cached
Mem:       3374968    3352828      22140          0     136372    2755992
-/+ buffers/cache:     460464    2914504
Swap:            0          0          0
Total:     3374968    3352828      22140

---

### Post by Rui Pais on 2007-06-20
> **brydong said:**
> Oh right....well I have a separate issue where starting yesterday my swap doesn't show up when I start up.

I used to have swap, now I don't. No idea what that's about and haven't had time to look into that.

So if I get my swap back then I'll get all my ram? What's happening here is RAM is being reserved for swap?

thanks,
brydon

check the UUID of your swap partition against the one is listed in /etc/fstab:
```
sudo vol_id -u /dev/XXX
```
XXX is the swap partition numeration
```
cat /etc/fstab | grep swap
```

---

### Post by CrispyFried on 2007-06-20
not really sure whats going on. how big was your swap when you had it? was it about the same size as the amount of missing ram?

---

### Post by brydong on 2007-06-20
Swap entry for fstab:

/dev/md1        none            swap    sw              0       0

Clearly there's something wrong here so vol_id was rather useless....

[~]$ sudo vol_id -u /dev/md1 

/dev/md1: unknown volume type

---

### Post by Rui Pais on 2007-06-20
> **brydong said:**
> Swap entry for fstab:

/dev/md1        none            swap    sw              0       0

Clearly there's something wrong here so vol_id was rather useless....

[~]$ sudo vol_id -u /dev/md1 

/dev/md1: unknown volume type

whats md1? sorry never head of that kind of device... whats the output of 
```
sudo mount
```

btw, relative to your main question. Is your Ubuntu a 32b version?
I'm not sure, but i think 32b are not able to mount full 4G (unless patched), like the old limitations for 1G to i386 kernels.
Again, not sure... maybe someone can confirm.

---

### Post by brydong on 2007-06-20
A bit more background....This was a fedora core 6 machine that I moved to ubuntu. As well, I'm running a raid array. I'm not sure if that's relevant.

sudo mount
/dev/md3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/md0 on /boot type ext3 (rw)
/dev/md4 on /home type ext3 (rw)
/dev/md2 on /opt type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)

---

### Post by Rui Pais on 2007-06-20
Ah ok, must be the raid designation.

Can you, please, post the output of :
```
sudo fdisk -l
```

---

### Post by brydong on 2007-06-20
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          19      152586   fd  Linux raid autodetect
/dev/sda2              20        3935    31455270   fd  Linux raid autodetect
/dev/sda3            3936        4457     4192965   fd  Linux raid autodetect
/dev/sda4            4458       30401   208395180    5  Extended
/dev/sda5            4458        4979     4192933+  fd  Linux raid autodetect
/dev/sda6            4980       30401   204202183+  fd  Linux raid autodetect

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          19      152586   fd  Linux raid autodetect
/dev/sdb2              20        3935    31455270   fd  Linux raid autodetect
/dev/sdb3            3936        4457     4192965   fd  Linux raid autodetect
/dev/sdb4            4458       30401   208395180    5  Extended
/dev/sdb5            4458        4976     4168836   fd  Linux raid autodetect
/dev/sdb6            4977       30401   204226281   fd  Linux raid autodetect

Disk /dev/md0: 156 MB, 156172288 bytes
2 heads, 4 sectors/track, 38128 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md3: 32.2 GB, 32210092032 bytes
2 heads, 4 sectors/track, 7863792 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md3 doesn't contain a valid partition table

Disk /dev/md2: 4293 MB, 4293525504 bytes
2 heads, 4 sectors/track, 1048224 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/md4: 209.1 GB, 209102962688 bytes
2 heads, 4 sectors/track, 51050528 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md4 doesn't contain a valid partition table

---

### Post by Rui Pais on 2007-06-20
sorry brydong,
don't have any experience with raid arrays :( 
can't give more help there. 
Just note that /dev/md1 is not listed by fdisk (but you have 2x5 partitions as raid, so you should have md0 ... till md4)

Have you tried to launch gparted and check if the partition is formated and to swap format?

if so did:
```
swapon /dev/md1
```

gives any output?

---

### Post by brydong on 2007-06-20
Never used gparted...

I can see the 4 GB swap I created in gparted but it obviously doesn't appear to be in use.

There's /dev/sd4 which is extended and contains /dev/sda5 (swap) and /dev/sda6 (home?).

Should I try swapon /dev/sda5?

---

### Post by brydong on 2007-06-20
Sorry that was dumb. That's just the one physical drive. So there's /dev/sdb5 as well, which is unused swap.

---

### Post by Rui Pais on 2007-06-20
As i said i'm not confortable at all with raid...

Maybe you can use swap not as raid (it will be empty for 99.99% of the time anyway) but path the 2 /dev/sdxx in fstab as swap. Or tried fist with swapon (it's harmless)

---
We are complicating anyway and get out of your question.

Linux can run normally without swap. It's an obsolete trick from times when RAM was small and expensive. You have 4G!! Your swaps are just waste of space. It will never be used. 
I have 1G and swap is hardly touched at all. 
(*Edit:* Unless you want to use Suspend function...)

And even if kernel reserved part of RAM to use as swap (a weird concept because swap it's exactly the opposite) free command should always give the total amount of memory existent, no matter the use kernel give to it. 
Check the first lines of dmesg it should have the output of the kernel mapping of ram, before it even mount partitions and swaps.

Google too for 4G RAM under 32bits Linux to see if you got something about the ability of kernel use the all or partial memory of that size. 

If i found something i post it here.

---

### Post by CrispyFried on 2007-06-20
check this thread for some info on 4 gigs of ram.

[http://ubuntuforums.org/showthread.php?t=471721&highlight=max+ram](http://ubuntuforums.org/showthread.php?t=471721&highlight=max+ram)

---

### Post by steveneddy on 2007-06-24
UM - does your swap come back if you go back to 2 GIG of RAM?

Just curious.

---

### Post by brydong on 2007-06-24
I haven't tried but I was seeing the swap issue prior to adding the 2GB of ram so I'm fairly certain no.

---

### Post by steveneddy on 2007-06-24
OK - I was thinking of installing 4 GIG of RAM in my laptop to see if it could actually see 4 GIG of RAM. 

Right now I am using 2 GIG of RAM.

I would like to try the 64 bit version of Ubuntu, but I'm going to wait until a few more bugs get worked out.

---

