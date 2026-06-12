---
title: "Free disk Space Issue"
date: 2015-08-27
forum: Hardware
---

### Post by brendon6 on 2015-08-27
Hi there,
Not sure if im in the right place, if not, mod please move me.

I am having an issue with my disk, and it has run out of space, however the disk says it isnt full

i ran df and this is what it returned

```
Filesystem                           1K-blocks       Used  Available Use% Mounted on
/dev/mapper/BICT--APPS--02--vg-root   14286320   13540196          0 100% /
none                                         4          0          4   0% /sys/fs/cgroup
udev                                    236808          4     236804   1% /dev
tmpfs                                    49608       1468      48140   3% /run
none                                      5120          0       5120   0% /run/lock
none                                    248040          4     248036   1% /run/shm
none                                    102400          0     102400   0% /run/user
/dev/xvda1                              240972      69361     159170  31% /boot
```


xvda1 is the main system disk (the system is hypervised on xen server 6)

as you can see the /boot partition is only 31% but the root is 100 and i cant seem to find an explanation why


any help is appreciated

regards,
Brendon

---

### Post by Skaperen on 2015-08-27
what does this command show?

```
sudo find / -type f -printf '%s %p\n' 2>/dev/null|grep -v /proc/|awk '{if($1>s){print $0;s=$1}}'

```
the last line is probably most critical.

---

### Post by brendon6 on 2015-08-27
This was the result


```
311 /lib/recovery-mode/options/grub350 /lib/recovery-mode/options/clean
914 /lib/recovery-mode/options/apt-snapshots
1053 /lib/recovery-mode/options/dpkg
2954 /lib/recovery-mode/options/system-summary
3130 /lib/recovery-mode/recovery-menu
71848 /lib/systemd/systemd-localed
252056 /lib/systemd/systemd-logind
281552 /lib/x86_64-linux-gnu/libdbus-1.so.3.7.6
282352 /lib/x86_64-linux-gnu/libreadline.so.6.3
1228552 /lib/x86_64-linux-gnu/libslang.so.2.2.4
1926432 /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
2510972 /lib/modules/3.13.0-35-generic/kernel/drivers/gpu/drm/radeon/radeon.ko
5660180 /lib/udev/hwdb.bin
219218330 /ftphttplog.txt



```

The ssh session disconnected after that?

---

### Post by weatherman2 on 2015-08-27
Your root partition is 100% full, so don't expect the OS to function at all.  Now you may need to boot a live USB session.

Or, try shutting down and rebooting and if you are able to login again, consider erasing that huge logfile:

```

219218330 /ftphttplog.txt

```

which may free up enough space to let you work and find any other causes of the filesystem filling up.  You might look into what program is creating that logfile and looking at options for curtailing or even getting rid of it.

And if you can login and erase that file, then try the find command again and see what the biggest files in / are.

---

### Post by Skaperen on 2015-08-28
and why is that huge file in the / directory?

---

### Post by dino99 on 2015-08-28
as long as you install new kernels without purging the oldest ones, then /boot  becomes full at some point

each kernel has: 2 headers & 2 images installed

usually the latest 2 kernels are enough: if the latest fail to boot for some reason, then you still have the previous one. Install 'synaptic' to get a userfriendly tool to deal with packages, and select the oldest kernels for purging (right click: complete removal )

---

### Post by yancek on 2015-08-28
> and why is that huge file in the / directory? 				

Log files in my experience are generally under /var/log.  I've never seen a file with that name but it looks like 'ftp', have you set up or tried to set up ftp.  I can't imagine deleting a log file causing a problem and I think the only one who can answer that is yourself.

---

