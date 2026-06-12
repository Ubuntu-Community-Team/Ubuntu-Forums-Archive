---
title: "Cannot un-install a package"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by denarced on 2009-08-31
It would appear that this is a rather popular topic and I checked a few threads but they didn't help me at all.
Here's the deal: I installed something by mistake. A driver for my epson printer/driver .. the file's name is pips-snx100-debian4.0-3.3.0-CG.install.
I installed some packages and I was able to remove most of them but not all.
pips-snx100 will not go away, it's broken.
Some commands:
```
denarced@deskUbu:~/Desktop$ sudo apt-get remove pips-snx100
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  pips-snx100
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 3658kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 169243 files and directories currently installed.)
Removing pips-snx100 ...
Package `cupsys' is not installed.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
dpkg: error processing pips-snx100 (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 pips-snx100
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
```
denarced@deskUbu:~/Desktop$ sudo apt-get --force-yes purge pips-snx100
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  pips-snx100*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 3658kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 169243 files and directories currently installed.)
Removing pips-snx100 ...
Package `cupsys' is not installed.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
dpkg: error processing pips-snx100 (--purge):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 pips-snx100
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
```
denarced@deskUbu:~/Desktop$ sudo dpkg --info pips-snx100
dpkg-deb: failed to read archive `pips-snx100': No such file or directory
```

What to do?

---

### Post by zvacet on 2009-09-01
```
sudo dpkg --remove --force-remove-reinstreq pips-snx100
```

---

### Post by denarced on 2009-09-01
> **zvacet said:**
> ```
sudo dpkg --remove --force-remove-reinstreq pips-snx100
```denarced@deskUbu:~$ sudo dpkg --remove --force-remove-reinstreq pips-snx100
(Reading database ... 169243 files and directories currently installed.)
Removing pips-snx100 ...
Package `cupsys' is not installed.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
dpkg: error processing pips-snx100 (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 pips-snx100

no go

---

### Post by denarced on 2009-09-01
I did a little search and I found a bunch of file relating to this pips-snx100 package from the following directories
/var/crash/
/var/lib/dpkg/info/
/usr/share/doc/pips-snx100-3.3.0
/usr/share/doc/pips-snx100
/usr/share/locale/en/LC_MESSAGES/
/usr/lib/

Would it fix the problem if I just delete these ??
Cause I'm dying to solve this since I can't install packages anymore :(

---

### Post by denarced on 2009-09-01
Found something that might actually help
This is from /var/lib/dpkg/status
Maybe it'll help someone to figure out what's going on
```
Package: pips-snx100
Status: purge ok half-configured
Priority: optional
Section: graphics
Installed-Size: 3572
Maintainer: epson <pips@localdomain>
Architecture: i386
Version: 3.3.0-1
Provides: pips-printer
Depends: libstdc++6, libc6, pips-common (>= 3.3.0)
Description: Photo Image Print System - Easy Install System (i386)
 Photo Image Print System is a printer driver for Epson Inkjet Printers.
```

---

### Post by Partyboi2 on 2009-09-01
Have you got the cupsys package installed?
```
sudo apt-get install cupsys
```
Then try removing pips-snx100

---

### Post by denarced on 2009-09-01
> **Partyboi2 said:**
> Have you got the cupsys package installed?
```
sudo apt-get install cupsys
```
Then try removing pips-snx100

Can't install a thing..
Tried it anyway and no go

Any other ideas??
Getting desperate and I found an archived forum page which gives a fix but nothing too pretty
[http://ubuntuforums.org/archive/index.php/t-788820.html]("http://ubuntuforums.org/archive/index.php/t-788820.html")

---

### Post by jacksaff on 2009-09-01
sudo aptitude remove pips-snx100

Should give you some options if the package won't go cleanly.

---

### Post by jjgomera on 2009-09-01
go to /var/lib/dpkg/info and remove any entries about pips-snx100

---

### Post by denarced on 2009-09-01
> **jjgomera said:**
> go to /var/lib/dpkg/info and remove any entries about pips-snx100

this did the trick
I can once again use apt
It's not a pretty solution but it'll have to do

For reference, here's what I ultimately did

1) Check the pips-snx100 entries
```
denarced@deskUbu:/var/lib/dpkg/info$ ll | grep pips
-rw-r--r-- 1 root root      0 2009-08-31 20:53 pips-common.list
-rwxr-xr-x 1 root root   1055 2008-09-19 04:40 pips-common.postrm
-rw-r--r-- 1 root root   3606 2009-08-31 15:25 pips-snx100.list
-rw-r--r-- 1 root root   4534 2008-09-19 04:41 pips-snx100.md5sums
-rwxr-xr-x 1 root root   1832 2008-09-19 04:41 pips-snx100.postinst
-rwxr-xr-x 1 root root    978 2008-09-19 04:41 pips-snx100.postrm
-rwxr-xr-x 1 root root   1726 2008-09-19 04:41 pips-snx100.prerm
```
2) Move the stuff elsewhere ( rm later if no problemo )
```
denarced@deskUbu:/var/lib/dpkg/info$ sudo mv pips-snx100* /home/denarced/Desktop/pips
```
3) Let apt clear itself
```
denarced@deskUbu:~/Desktop/pips$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  pips-snx100
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 3658kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 
dpkg: serious warning: files list file for package `pips-snx100' missing, assuming package has no files currently installed.
169174 files and directories currently installed.)
Removing pips-snx100 ...
```
and I can once again use apt
hooray
I'd still like to know what really happened but small chance for that, right :)

I'll let you know if problems arise but I'd say this one's solved

---

