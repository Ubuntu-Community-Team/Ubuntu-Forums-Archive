---
title: "x server down, apt-get broekm perl problem"
date: 2006-12-15
forum: Hardware &amp; Laptops
---

### Post by stabface on 2006-12-15
i started my machine up today and X wouldn't start. 
i am not sure why but it told me something about the nvidia kernel  being broken so i moved over to my old nv driver and got x running again, but only one monitor instead of two. 

also so when i tried to update the drivers i keep seeing this come up in terminal 

```
The following packages have unmet dependencies:
  libevent-execflow-perl: Depends: libanyevent-perl but it is not installed
```

this comes up when i use apt-get for the drivers, or even just apt-get upgrade. 

so then i try to apt-get install libanyevent-perl 


```
The following packages were automatically installed and are no longer required:
  libwxgtk2.4-1 cfv libevent-rpc-perl anyevent-perl kompare libnss3-0d
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libanyevent-perl
0 upgraded, 1 newly installed, 0 to remove and 21 not upgraded.
1 not fully installed or removed.
Need to get 0B/17.4kB of archives.
After unpacking 53.2kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  libanyevent-perl
Install these packages without verification [y/N]? y
(Reading database ... 137236 files and directories currently installed.)
Unpacking libanyevent-perl (from .../libanyevent-perl_1.02-1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libanyevent-perl_1.02-1_all.deb (--unpack):
 trying to overwrite `/usr/share/man/man3/AnyEvent.3pm.gz', which is also in package anyevent-perl
Errors were encountered while processing:
 /var/cache/apt/archives/libanyevent-perl_1.02-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

i really need to get my drivers back, and my system back up thisis my pc at the office where i am trying t convince then to move over the whole office to ubuntu.

---

### Post by La muerte del DIos on 2007-06-05
I hope this will work for you too.

[http://ubuntuforums.org/showthread.php?p=2788351#post2788351](http://ubuntuforums.org/showthread.php?p=2788351#post2788351)

---

