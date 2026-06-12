---
title: "libGL.so.1 for new fglrx (8.476-0ubuntu1)"
date: 2008-04-26
forum: Hardware
---

### Post by puccaso on 2008-04-26
```
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
   xorg-driver-fglrx (7.1.0-8-3+2.6.24.12-16.34 => 8.476-0ubuntu1)
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 7450kB of archives.
After this operation, 5460kB disk space will be freed.
Do you want to continue [Y/n]? y
Get: 1 http://public.stangdude.com gutsy/main xorg-driver-fglrx 2:8.476-0ubuntu1 [7450kB]
Fetched 7450kB in 2min5s (59.2kB/s)                                            
Reading changelogs... Done
(Reading database ... 166984 files and directories currently installed.)
Preparing to replace xorg-driver-fglrx 1:7.1.0-8-3+2.6.24.12-16.34 (using .../xorg-driver-fglrx_2%3a8.476-0ubuntu1_i386.deb) ...
Stopping atieventsd:.
Unpacking replacement xorg-driver-fglrx ...
Setting up xorg-driver-fglrx (2:8.476-0ubuntu1) ...
Installing new version of config file /etc/ati/signature ...
Starting atieventsd:/usr/sbin/atieventsd: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
[COLOR=Red] failed![/COLOR]


```

so this is the first error i got since hardy came out
what is this about?

---

### Post by master_kernel on 2008-04-27
There is a bug in the new FGLRX 8-4 driver: something about it diverting a file that is already diverted to itself or something. Read more at [http://ubuntuforums.org/showthread.php?t=757298]("http://ubuntuforums.org/showthread.php?t=757298").

EDIT: The above may not solve your problem. Try linking libGL.so.1 to libGL.so.1.2 -- sorry I cannot provide the command -- I lost it somewhere...

---

### Post by gerben1 on 2008-04-27
I had that too, and solved it by making a link like this:
sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

as is "explained" here:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#libGL_error](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#libGL_error)

---

