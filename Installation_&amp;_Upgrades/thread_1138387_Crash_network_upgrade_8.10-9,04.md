---
title: "Crash: network upgrade 8.10-9,04"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by MikeB007 on 2009-04-26
Hi there.  Thanks for looking.  I've been using Ubuntu since 8.04 and this is my first upgrade via the web.  I got a crash with the error listed below.  It seems I have a problem with my package manager.  Is this correct or, if not, any advice would be welcome.

...
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg-query: parse error, in file `/var/lib/dpkg/available' near line 39536 package `libisccfg30':
 field name `
exim4-config.postinst: [WARN] Installed debconf version is broken. Aborting preconfigure.
dpkg: parse error, in file `/var/lib/dpkg/available' near line 39536 package `libisccfg30':
none
ge `libisccfg30':
onfigure.
bisccfg30':
s /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkgreturned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkgreturned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/
ERROR:root:SystemError from cache.commit(): installArchives() failed
WARNING:root:cache.commit() error and pkg_failures == 0, generate a report against update-manager to investigate
Traceback (most recent call last):
  File "/usr/share/apport/package_hook", line 58, in <module>
    pr.write(open(apport.fileutils.make_report_path(pr), 'w'))
  File "/usr/lib/python2.5/site-packages/problem_report.py", line 301, in write
    f = open(v[0]) # file name
IOError: [Errno 21] Is a directory

---

### Post by Triptol on 2009-04-26
Trying to save what can be saved :-)

This one will try and get the installation done:
```
aptitude dist-upgrade
```

You might need a dpkg-reconfigure, but the aptitude command will tell you when you need it. If it does, just copy and paste the dpkg-reconfigure line and run the update again.

Now I hope all the packages are on your system...

---

### Post by MikeB007 on 2009-04-26
When I run the suggested command, I get:

Preconfiguring packages ...                                                                                             
dpkg: parse error, in file `/var/lib/dpkg/available' near line 39536 package `libisccfg30':                             
 field name `                                                                                                           
dpkg-query: parse error, in file `/var/lib/dpkg/available' near line 39536 package `libisccfg30':                       
 field name `                                                                                                           
exim4-config.postinst: [WARN] Installed debconf version is broken. Aborting preconfigure.
dpkg: parse error, in file `/var/lib/dpkg/available' near line 39536 package `**libisccfg30**':
 field name `
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file `/var/lib/dpkg/available' near line 39536 package `libisccfg30':
 field name `
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done

Not sure which part is to be cut and pasted where.  Is it the bold item above and I put that in the file "/var/lib ...." ?
I believe all the packages downloaded successfully but would it change things if I tried the alternate install from the ISO?  Thanks.

---

### Post by MikeB007 on 2009-04-26
Also interesting:  I can open '/var/lib/.../available-old' from gedit but can't open '/var/lib/..../available' from gedit.  When I try the latter it says it cannot detect the character coding.  I _can_ open it with Openoffice though.  

Also: Error also suggested that I report the crash via Launchpad which I'm doing.

---

### Post by MikeB007 on 2009-04-26
From my last post it seemed the file was corrupted.  So:  

ran 'sudo dpkg --configure -a' which cleared the 'available' file; 

ran 'sudo aptitude dist-upgrade'

The upgrade proceeded as expected ... well longer than I expected but I have several third party apps so ....  HTH

---

### Post by Triptol on 2009-04-27
Good to see things worked out...

It was "dpkg --configure -a" not "dpkg-reconfigure". I always forget that one. But normally I get pointed in the right direction by aptitude.

---

