---
title: "mono upgrade woes"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by jenkinbr on 2009-09-01
The other day, I tried to do a normal routine system update, so I ran

```
sudo apt-get update
sudo apt-get upgrade
```
There were a bunch of upgrades, including a bunch of mono packages, everything but the mono packages completely installed.  I've tried several things to solve this, none of which worked.

sudo apt-get upgrade
```
sujenkinbr@jenkinbr:/usr/share/man$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
20 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up mono-common (2.0.1-4ubuntu0.1) ...
update-binfmts: /var/lib/binfmts/python2.5 corrupt: out of binfmt data reading
package 
dpkg: error processing mono-common (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of mono-jit:
 mono-jit depends on mono-common (= 2.0.1-4ubuntu0.1); however:
  Package mono-common is not configured yet.
dpkg: error processing mono-jit (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of libmono-corlib2.0-cil:
 libmono-corlib2.0-cil depends on mono-jit (>= 2.0.1); however:
  Package mono-jit is not configured yet.
 libmono-corlib2.0-cil depends on mono-jit (<< 2.0.2); however:
  Package mono-jit is not configured yet.
dpkg: error processing libmono-corlib2.0-cil (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of libmono-cairo2.0-cil:
 libmono-cairo2.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
dpkg: error processing libmono-cairo2.0-cil (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libmono-security2.0-cil:
 libmono-security2.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
dpkg: error processing libmono-security2.0-cil (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libmono-system2.0-cil:
 libmono-system2.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
 libmono-system2.0-cil depends on libmono-security2.0-cil (>= 2.0); however:
  Package libmono-security2.0-cil is not configured yet.
 libmono-system2.0-cil depends on mono-jit (>= 2.0.1); however:
  Package mono-jit is not configured yet.
 libmono-system2.0-cil depends on mono-jit (<< 2.0.2); however:
  Package mono-jit is not configured yet.
dpkg: error processing libmono-system2.0-cil (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libmono-data-tds2.0-cil:
 libmono-data-tds2.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
 libmono-data-tds2.0-cil depends on libmono-security2.0-cil (>= 2.0); however:
  Package libmono-security2.0-cil is not configured yet.
 libmono-data-tds2.0-cil depends on libmono-system2.0-cil (>= 2.0); however:
  Package libmono-system2.0-cil is not configured yet.
dpkg: error processing libmono-data-tds2.0-cil (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libmono-system-data2.0-cil:
 libmono-system-data2.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
 libmono-system-data2.0-cil depends on libmono-data-tds2.0-cil (>= 2.0); however:
  Package libmono-data-tds2.0-cil is not configured yet.
 libmono-system-data2.0-cil depends on libmono-system2.0-cil (>= 2.0); however:
  Package libmono-system2.0-cil is not configured yet.
dpkg: error processing libmono-system-data2.0-cil (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libmono-data2.0-cil:
 libmono-data2.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
 libmono-data2.0-cil depends on libmono-data-tds2.0-cil (>= 2.0); however:
  Package libmono-data-tds2.0-cil is not configured yet.
 libmono-data2.0-cil depends on libmono-system-data2.0-cil (>= 1.2.6); however:
  Package libmono-system-data2.0-cil is not configured yet.
 libmono-data2.0-cil depends on libmono-system2.0-cil (>= 2.0); however:
  Package libmono-system2.0-cil is not configured yet.
dpkg: error processing libmono-data2.0-cil (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libmono-getoptions2.0-cil:
 libmono-getoptions2.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
 libmono-getoptions2.0-cil depends on libmono-system2.0-cil (>= 2.0); however:
  Package libmono-system2.0-cil is not configured yet.
dpkg: error processing libmono-getoptions2.0-cil (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libmono-i18n2.0-cil:
 libmono-i18n2.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
dpkg: error processing libmono-i18n2.0-cil (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libmono-posix2.0-cil:
 libmono-posix2.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
 libmono-posix2.0-cil depends on libmono-system2.0-cil (>= 2.0); however:
  Package libmono-system2.0-cil is not configured yet.
dpkg: error processing libmono-posix2.0-cil (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libmono-sharpzip2.84-cil:
 libmono-sharpzip2.84-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
 libmono-sharpzip2.84-cil depends on libmono-system2.0-cil (>= 2.0); however:
  Package libmono-system2.0-cil is not configured yet.
dpkg: error processing libmono-sharpzip2.84-cil (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libmono-sqlite2.0-cil:
 libmono-sqlite2.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
 libmono-sqlite2.0-cil depends on libmono-system-data2.0-cil (>= 1.2.6); however:
  Package libmono-system-data2.0-cil is not configured yet.
 libmono-sqlite2.0-cil depends on libmono-system2.0-cil (>= 2.0); however:
  Package libmono-system2.0-cil is not configured yet.
dpkg: error processing libmono-sqlite2.0-cil (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mono-2.0-runtime:
 mono-2.0-runtime depends on mono-jit (= 2.0.1-4ubuntu0.1); however:
  Package mono-jit is not configured yet.
 mono-2.0-runtime depends on libmono-corlib2.0-cil (= 2.0.1-4ubuntu0.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
dpkg: error processing mono-2.0-runtime (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mono-runtime:
 mono-runtime depends on mono-2.0-runtime (= 2.0.1-4ubuntu0.1); however:
  Package mono-2.0-runtime is not configured yet.
dpkg: error processing mono-runtime (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mono-2.0-gac:
 mono-2.0-gac depends on mono-jit (>= 1.0); however:
  Package mono-jit is not configured yet.
 mono-2.0-gac depends on mono-runtime (>= 1.1.8.1); however:
  Package mono-runtime is not configured yet.
 mono-2.0-gac depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
 mono-2.0-gac depends on libmono-security2.0-cil (>= 2.0); however:
  Package libmono-security2.0-cil is not configured yet.
dpkg: error processing mono-2.0-gac (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmono-system-web2.0-cil:
 libmono-system-web2.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
 libmono-system-web2.0-cil depends on libmono-sqlite2.0-cil (>= 1.2.6); however:
  Package libmono-sqlite2.0-cil is not configured yet.
 libmono-system-web2.0-cil depends on libmono-system-data2.0-cil (>= 1.2.6); however:
  Package libmono-system-data2.0-cil is not configured yet.
 libmono-system-web2.0-cil depends on libmono-system2.0-cil (>= 2.0); however:
  Package libmono-system2.0-cil is not configured yet.
 libmono-system-web2.0-cil depends on mono-jit (>= 2.0.1); however:
  Package mono-jit is not configured yet.
 libmono-system-web2.0-cil depends on mono-jit (<< 2.0.2); however:
  Package mono-jit is not configured yet.
dpkg: error processing libmono-system-web2.0-cil (--configure)No apport report written because MaxReports is reached already
                                                                                                                            No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                                                                                                          No apport report written because MaxReports is reached already
                          :
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmono2.0-cil:
 libmono2.0-cil depends on mono-runtime (>= 1.1.8.1); however:
  Package mono-runtime is not configured yet.
 libmono2.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
 libmono2.0-cil depends on libmono-posix2.0-cil (= 2.0.1-4ubuntu0.1); however:
  Package libmono-posix2.0-cil is not configured yet.
 libmono2.0-cil depends on libmono-security2.0-cil (>= 2.0); however:
  Package libmono-security2.0-cil is not configured yet.
 libmono2.0-cil depends on libmono-sharpzip2.84-cil (>= 1.0); however:
  Package libmono-sharpzip2.84-cil is not configured yet.
 libmono2.0-cil depends on libmono-system-web2.0-cil (>= 1.9.1); however:
  Package libmono-system-web2.0-cil is not configured yet.
 libmono2.0-cil depends on libmono-system2.0-cil (>= 2.0); however:
  Package libmono-system2.0-cil is not configured yet.
 libmono2.0-cil depends on libmono-getoptions2.0-cil (= 2.0.1-4ubuntu0.1); however:
  Package libmono-getoptions2.0-cil is not configured yet.
 libmono2.0-cil depends on libmono-data2.0-cil (= 2.0.1-4ubuntu0.1); however:
  Package libmono-data2.0-cil is not configured yet.
dpkg: error processing libmono2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mono-gac:
 mono-gac depends on mono-2.0-gac (= 2.0.1-4ubuntu0.1); however:
  Package mono-2.0-gac is not configured yet.
dpkg: error processing mono-gac (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mono-common
 mono-jit
 libmono-corlib2.0-cil
 libmono-cairo2.0-cil
 libmono-security2.0-cil
 libmono-system2.0-cil
 libmono-data-tds2.0-cil
 libmono-system-data2.0-cil
 libmono-data2.0-cil
 libmono-getoptions2.0-cil
 libmono-i18n2.0-cil
 libmono-posix2.0-cil
 libmono-sharpzip2.84-cil
 libmono-sqlite2.0-cil
 mono-2.0-runtime
 mono-runtime
 mono-2.0-gac
 libmono-system-web2.0-cil
 libmono2.0-cil
 mono-gac
E: Sub-process /usr/bin/dpkg returned an error code (1)
jenkinbr@jenkinbr:/usr/share/man$ 

```

I've traced this output, and it seems that the problem is being caused by mono-common:```
dpkg: error processing mono-common (--configure):
 subprocess post-installation script returned error exit status 2
```

The only other thing I tried was to run (and this is NOT recommended)
```
sudo dpkg --force-breaks -P mono-common
```
With the intent to reinstall using a downloaded copy, but that didn't even work, and gave me
```
jenkinbr@jenkinbr:/usr/share/man$ sudo dpkg --force-breaks -P mono-common
[sudo] password for jenkinbr: 
(Reading database ... 274462 files and directories currently installed.)
Removing mono-common ...
update-binfmts: /var/lib/binfmts/python2.5 corrupt: out of binfmt data reading
package 
dpkg: error processing mono-common (--purge):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 mono-common
jenkinbr@jenkinbr:/usr/share/man$ 

```



I've only just realized that this is probably a problem due to:```
update-binfmts: /var/lib/binfmts/python2.5 corrupt: out of binfmt data reading
package 
```

I've checked the /var/lib/binfmts/python2.5 file and it is empty

```
-rw-r--r-- 1 root root 0 2009-06-08 12:32 /var/lib/binfmts/python2.5

```

Not sure at this point what to do to solve this...

---

### Post by directhex on 2009-09-01
> **jenkinbr said:**
> I've checked the /var/lib/binfmts/python2.5 file and it is empty

```
-rw-r--r-- 1 root root 0 2009-06-08 12:32 /var/lib/binfmts/python2.5

```

Not sure at this point what to do to solve this...

```
python2.5
magic
0
\xb3\xf2\x0d\x0a

/usr/bin/python2.5


```

---

### Post by jenkinbr on 2009-09-01
> **directhex said:**
> ```
python2.5
magic
0
\xb3\xf2\x0d\x0a

/usr/bin/python2.5


```
THANK YOU :)

Worked great :)

Added the above to the /var/lib/binfmts/python2.5 file (only obvious place to put it), and tryed again - worked :)

---

