---
title: "How to find, which process wake up my HDD?"
date: 2014-05-30
forum: Hardware
---

### Post by Roman_Sery on 2014-05-30
Hello, 

I've **/dev/sda** as system disc and **/dev/sdb** as storage disc.
Today I have first checked s.m.a.r.t. parameters of sdb disc. After 400 days of using is number of " *Load*/Unload Cycle Count" cca 595.000!!! It's a WD Caviar Green 2TB WD20EARX with garanted lifetime 300.000 cycles. 
Unfortunately, the manufacturer went mad and set parameters for head parking for 8 seconds. 

So, i've tried to change it with hdparm, but failed. 

hdparm -B (any number) can not be used. (Error)
hdparm -S (any number) no effect (ignored?)
hdparm -y quickly spin them down
(As a last resort I will try to use the program idle3-tools.)

It's a one side of Problem.

But! HDD is used as media storage and theoreticaly should not be used too frequently. So how to find which process wakes him every minute? I've tried "iotop" utility. I saw no disc activity (read/write), but after a few minutes was "Cycle Count" + 5.
Is it possible to find, why is disc so frequently waking up?

---

### Post by matt_symes on 2014-05-30
Hi

Post the output of 

```
cat /proc/mounts
```

See what processes are access the drive using

```
lsof +D /mount/point
```

It may be the fiiling system that is accessing the drive. Check your mount options.

Kind regards

---

### Post by Roman_Sery on 2014-05-30
serak@nas:/$ cat /proc/mounts
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
none /dev devtmpfs rw,relatime,size=503492k,nr_inodes=125873,mode=755 0 0
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
/dev/disk/by-uuid/6f4c58e9-5723-4963-bbad-18b8b164d5ea / ext3 rw,relatime,errors=remount-ro,commit=360,data=ordered 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0
none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0
none /lib/init/rw tmpfs rw,nosuid,relatime,mode=755 0 0
/dev/sdb1 /media/disk ext3 rw,relatime,errors=continue,commit=360,data=ordered 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
gvfs-fuse-daemon /home/serak/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0
serak@127.0.0.1:/cygdrive/C/Users/serak/X2GO~1/S-AF0F~1/spool /tmp/.x2go-serak/spool/C-serak-50-1401485000_stDGNOME_dp32 fuse.sshfs rw,nosuid,nodev,relatime,user_id=1000,group_id=1000,default_permissions,max_read=65536 0 0


serak@nas:/$ sudo lsof +D /media/disk
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/serak/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.sshfs file system /tmp/.x2go-serak/spool/C-serak-50-1401485000_stDGNOME_dp32
      Output information may be incomplete.
serak@nas:/$

---

### Post by tgalati4 on 2014-05-30
There is a WD utility that is used to change the spin-down.  Just do a web search:  Western Digital load cycle

You will get a lot of hits (more than 300,000) including:

[http://www.storagereview.com/how_to_stop_excessive_load_cycles_on_the_western_digital_2tb_caviar_green_wd20ears_with_wdidle3](http://www.storagereview.com/how_to_stop_excessive_load_cycles_on_the_western_digital_2tb_caviar_green_wd20ears_with_wdidle3)

---

### Post by Roman_Sery on 2014-05-31
Yes, I know. As I wrote, I will use idle3-tools, what is linux alternative for wdidle3. Actually, I already used it. Now is disc always on.
But it is a temporary solution. I want to use disc in green mode, so main problem is, to find process changing disc from sleep mode to idle.
Is it possible to use something like "lsof", but for a longer period of time? (>60sec)

---

### Post by Roman_Sery on 2014-06-02
OK. I know. RTFM. So "iotop --delay=1 --only" seems to be better. (But I don't see disc identification.)

---

### Post by matt_symes on 2014-06-02
Hi

Another option is to enable hard drive access dumping to syslog.

That may tell you what is accessing the particular drive. I used it myself may moons ago and found it useful.

To turn it on...

```
echo 1 | sudo tee /proc/sys/vm/block_dump
```

and to turn it off

```
echo 0 | sudo tee  /proc/sys/vm/block_dump
```

You can then check syslog to try to determine what is writing to the drive.

I will say that you may want to get syslog to write to a file in RAM using tmpfs otherwise each write to syslog on the drive may generate a write to syslog :)

EDIT:

Just thought i would add a link...

[https://access.redhat.com/site/documentation/en-US/Red_Hat_Enterprise_Linux/4/html/Reference_Guide/s3-proc-sys-vm.html](https://access.redhat.com/site/documentation/en-US/Red_Hat_Enterprise_Linux/4/html/Reference_Guide/s3-proc-sys-vm.html)

Kind regards

---

