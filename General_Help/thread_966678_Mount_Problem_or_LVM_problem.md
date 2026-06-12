---
title: "Mount Problem or LVM problem"
date: 2008-11-01
forum: General Help
---

### Post by rnelson0 on 2008-11-01
Background:
I have a Mythbuntu setup that has an LVM partition mounted to my /home directory. About a week ago the last hard drive in the LVM volume group started failing the S.M.A.R.T. tests. Then it died. Luckily, I lost no data and I was able to replace that failing drive with the exact model and add it to the LVM volume group. However that didn't fix my problem.
The symptoms that first showed up when the drive started failing was an input/output error when I tried to access anything in my /home directory. When I boot up, I can access everything fine, but after about a half hour to an hour, the home directory can't be found by the system. If I do an LS on the root directory, here is an example of what I get:
```

bob@bam:/$ ls -la
ls: cannot access home: Input/output error
total 101
drwxr-xr-x  23 root root    4096 2008-10-15 07:46 .
drwxr-xr-x  23 root root    4096 2008-10-15 07:46 ..
drwxr-xr-x   2 root root    4096 2008-08-23 12:52 bin
drwxr-xr-x   4 root root    1024 2008-10-15 07:46 boot
lrwxrwxrwx   1 root ubuntu    11 2008-07-18 23:22 cdrom -> media/cdrom
drwxr-xr-x  14 root root   14340 2008-11-01 02:20 dev
drwxr-xr-x 123 root root   12288 2008-11-01 02:20 etc
drwxr-xr-x   2 root ubuntu  4096 2008-07-18 23:22 extra_space
d?????????   ? ?    ?          ?                ? home
drwxr-xr-x   2 root root    4096 2008-07-04 22:20 initrd
drwx------   2 root root   16384 2008-07-18 23:22 lost+found
drwxr-xr-x   5 root root    4096 2008-11-01 02:20 media
drwxr-xr-x   2 root root    4096 2008-04-14 22:53 mnt

```

Anybody have any ideas where to go from here? I'm not even sure how to diagnose this...

Oh, and when the /home partion 'disappears', I am unable to start ANY programs... I can't even reboot via the GUI, I have to ssh in and tell it to reboot.

Thanks in advance for any help.

---

