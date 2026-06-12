---
title: "Broken package -Help"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by lordbux on 2009-08-05
I have a broken package ==> BITTORRENT
when i tried to reinstall or remove this package from Synaptic using "broken filter"
**i get this error **
> E: bittorrent: subprocess pre-removal script returned error exit status 134:confused:

**then i ran apt-get -f install and ended up with an error.**:(
```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  bittorrent
Suggested packages:
  bittorrent-gui
The following packages will be upgraded:
  bittorrent
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/53.4kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package bittorrent.
(Reading database ... 158793 files and directories currently installed.)
Preparing to replace bittorrent 3.4.2-11ubuntu2 (using .../bittorrent_3.4.2-11ubuntu5_all.deb) ...
xargs: xargs.c:443: main: Assertion `bc_ctl.arg_max <= (131072-2048)' failed.
Aborted
dpkg: warning - old pre-removal script returned error exit status 134
dpkg - trying script from the new package instead ...
xargs: xargs.c:443: main: Assertion `bc_ctl.arg_max <= (131072-2048)' failed.
Aborted
dpkg: error processing /var/cache/apt/archives/bittorrent_3.4.2-11ubuntu5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 134
Errors were encountered while processing:
 /var/cache/apt/archives/bittorrent_3.4.2-11ubuntu5_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
:confused:
i cant use apt-get as it gives USE **apt-get -f install ** output
please help:(
thanks in advance:popcorn:

---

### Post by aesis05401 on 2009-08-05
What version of Ubuntu are you using?  These error messages used to be attributed to a buggy findutils package in older versions of Ubuntu.

---

### Post by lordbux on 2009-08-05
> **aesis05401 said:**
> What version of Ubuntu are you using?  These error messages used to be attributed to a buggy findutils package in older versions of Ubuntu.


i am using Hardy:KS

---

### Post by aesis05401 on 2009-08-05
K, I no longer have a Hardy install, so I can't test this out for you.  Long story short, you want to try installing the Intrepid version of findutils first - see if it solves the issue.

A quick google search turned up instructions by some blogger:[http://blog.loxal.net/2008/09/xargs-xargsc443-main-assertion.html]("http://blog.loxal.net/2008/09/xargs-xargsc443-main-assertion.html")

Please post back to let us know if this solves your issue.

---

### Post by lordbux on 2009-08-06
Ya tried it............

now i get this whenb trying to reinstall bittorrent

```
~: sudo dpkg -i bittorrent_3.4.2-11ubuntu5_all.deb 
(Reading database ... 158769 files and directories currently installed.)
Preparing to replace bittorrent 3.4.2-11ubuntu2 (using bittorrent_3.4.2-11ubuntu5_all.deb) ...
xargs: xargs.c:443: main: Assertion `bc_ctl.arg_max <= (131072-2048)' failed.
Aborted
dpkg: warning - old pre-removal script returned error exit status 134
dpkg - trying script from the new package instead ...
xargs: xargs.c:443: main: Assertion `bc_ctl.arg_max <= (131072-2048)' failed.
Aborted
dpkg: error processing bittorrent_3.4.2-11ubuntu5_all.deb (--install):
 subprocess new pre-removal script returned error exit status 134
Errors were encountered while processing:
 bittorrent_3.4.2-11ubuntu5_all.deb
illuminatus@iluminati:/var/cache/apt/archives$ bitmap
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 5383 requests (5383 known processed) with 0 events remaining.

```

---

### Post by aesis05401 on 2009-08-06
Can you do 'xargs --version' just to make sure you are at or above 4.3.5-1.

If so, I'm afraid I don't know the answer to this.  I know these error messages in general were being thrown by xargs, but perhaps your situation is different.

---

### Post by konqui on 2009-08-06
sudo apt-get install -f
then
sudo dpkg -reconfigure -a

---

### Post by Soul-Sing on 2009-08-06
Maybe this will be helpfull: [http://ubuntuforums.org/archive/index.php/t-835632.html](http://ubuntuforums.org/archive/index.php/t-835632.html)

---

### Post by lordbux on 2009-08-07
OK SOLVED 

THANK YOU aesis05401
the trouble was with findutils just as you said ..but it could be solved without therepository editing.
thanks for the idea aesis05401.

just download the updated version (interpid) for findutils fromthe below link.
ORIGINAL UBUNTU PACKAGE DATABASE.
[http://packages.ubuntu.com/tr/intrepid/findutils](http://packages.ubuntu.com/tr/intrepid/findutils)

NOW INSTALL USING SHELL COMAND 
```
 sudo dpkg -i ./findutils_4.4.0-2ubuntu3_i386.deb
```

now run

```
sudo apt-get -f install
```

thanks everyone for all your help and specialy to aesis05401
opensource rules................

---

### Post by aesis05401 on 2009-08-08
Thank you for following up with the right method.  Now we know for next time. Open source rules.

---

