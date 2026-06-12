---
title: "sudo apt-get upgrade fails after fresh install of 8.04 ubuntu server"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by rasti121 on 2009-08-01
Hi,

have just install 8.04 server (LTS) and did as first 2 commands after logging in sudo apt-get update and sudo apt-get upgrade.
This doesn't work after downloads OK, install fails with dpkg: error porcessing /var/cache/apt/archives/dash_0.5.4-8ubuntu1.1_i386.deb (--unoack):
 files list file for package `libcurl3-gnutls' is missing final newline

...end then final abort due to too many errors.

I tried different options with dpkg but coudln't fix it.

Any help appreciated.

/Rasti.

---

### Post by rasti121 on 2009-08-01
I found this, small script with awk that recreates the .list file [http://finkproject.org/faq/usage-fink.php](http://finkproject.org/faq/usage-fink.php) (3/4 down the page), but there are more packages that don't work now, so I keep renaiming /var/lib/dpkg/info, installation with warnings works, and copy to old info directory and rename back, also I ran dpkg --configure -a just in case.

Very dirty workaround.

---

### Post by slakkie on 2009-08-01
What mirror are you using? 
Maybe post your sources.list?

---

### Post by rasti121 on 2009-08-01
Hi,

I don't think that's the issue because:

1. I started having problems with "vanilla" config
2. I changed (added) virtualbox repository apart of that it's still the original
3. Works with the same config when I "empty" /var/lib/dpkg/info (I rename the existing .../info to info.old, run the apt-get with warnings (but installs/upgrades all have worked) with same repositories: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)
[http://security.ubuntu.com](http://security.ubuntu.com)

Thanks for help.

sources.list:

# 
# deb cdrom:[Ubuntu-Server 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hard
y main restricted

#deb cdrom:[Ubuntu-Server 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy
 main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy non-free

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted unive
rse multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted u
niverse multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by slakkie on 2009-08-01
I do think there is a problem with that mirror:

```

Get:29 http://gb.archive.ubuntu.com hardy-updates/main Packages [457kB]
99% [27 Packages bzip2 0] [29 Packages 404144/457kB 88%]                                                                                                                752kB/s 0s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://gb.archive.ubuntu.com hardy/multiverse Packages
  Sub-process bzip2 returned an error code (2)
Get:30 http://gb.archive.ubuntu.com hardy-updates/restricted Packages [8409B]

```

I normally use the Dutch mirrors, and there the update works fine. Try a different mirror and see how that works (nl.archive/de.archive/be.archive) should be ok for you, or ireland, but don't know the prefix for that country ;)

Just run these command to check:

```

# to dutch archives
sudo perl -p -i -e 's/gb.archive/nl.archive/g' /etc/apt/sources.list
# back to british
sudo perl -p -i -e 's/nl.archive/gb.archive/g' /etc/apt/sources.list

```

---

### Post by rasti121 on 2009-08-02
Hi,

I have changed it, but I'm still getting the same error. Is there a way I can rebuild the whole isntalled database, that might fix it...
Thanks.


Get: 1 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) hardy-updates/main mysql-common 5.0.51a-3ubuntu5.4 [60.3kB]
Get: 2 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) hardy-updates/main libmysqlclient15off 5.0.51a-3ubuntu5.4 [1837kB]
Get: 3 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) hardy/universe mysql-gui-tools-common 5.0~rc12-2ubuntu1 [319kB]
Get: 4 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) hardy/universe mysql-admin 5.0~rc12-2ubuntu1 [1721kB]
Fetched 3937kB in 5s (750kB/s)              
(Reading database ... dpkg: error processing /var/cache/apt/archives/mysql-common_5.0.51a-3ubuntu5.4_all.deb (--unpack):
 files list file for package `bzip2' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-common_5.0.51a-3ubuntu5.4_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by slakkie on 2009-08-02
Run aptitude clean and try it again.
And see if you can reinstall the bzip2 package

---

### Post by Partyboi2 on 2009-08-02
> **rasti121 said:**
> Hi,

I have changed it, but I'm still getting the same error. Is there a way I can rebuild the whole isntalled database, that might fix it...
Thanks.


Get: 1 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) hardy-updates/main mysql-common 5.0.51a-3ubuntu5.4 [60.3kB]
Get: 2 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) hardy-updates/main libmysqlclient15off 5.0.51a-3ubuntu5.4 [1837kB]
Get: 3 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) hardy/universe mysql-gui-tools-common 5.0~rc12-2ubuntu1 [319kB]
Get: 4 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) hardy/universe mysql-admin 5.0~rc12-2ubuntu1 [1721kB]
Fetched 3937kB in 5s (750kB/s)              
(Reading database ... dpkg: error processing /var/cache/apt/archives/mysql-common_5.0.51a-3ubuntu5.4_all.deb (--unpack):
 files list file for package `bzip2' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-common_5.0.51a-3ubuntu5.4_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

Hi, open a terminal and try
```
echo -en '\n' | sudo tee -a /var/lib/dpkg/info/bzip2.list
```

---

### Post by rasti121 on 2009-08-02
Hi,

redone aptitude, delete all downloaded packages, nothing helped.

Adding EOL seems to do the trick, just now next package in the row (I expect) has the same problem - how could I loos EOL of all .list

Isn't there any other way then go through all .list files and addin \n ?


(Reading database ... dpkg: error processing /var/cache/apt/archives/mysql-common_5.0.51a-3ubuntu5.4_all.deb (--unpack):
 files list file for package `libcwidget3' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-common_5.0.51a-3ubuntu5.4_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done

---

### Post by slakkie on 2009-08-02
Just found this: [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189)

---

### Post by rasti121 on 2009-08-02
That's the one, thanks. Have to wait for a fix then.

Thanks everyone for help.

---

