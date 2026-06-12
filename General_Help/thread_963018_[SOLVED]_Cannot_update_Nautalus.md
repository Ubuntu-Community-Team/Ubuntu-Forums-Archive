---
title: "[SOLVED] Cannot update Nautalus"
date: 2008-10-29
forum: General Help
---

### Post by ajtaggs on 2008-10-29
Hey, I I have searched long and hard to resolve this issue and everything I've tried hasn't worked so far. I am running Ubuntu Hardy in VMWare and everything was going good until the day I tried to update Nautilus.

I've gotten many different errors while trying some things but I'll start with this one.

i run:

sudo aptitude install build-essential

and get:

sudo: unable to resolve host Programmer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  linux-headers-2.6.24-19 linux-headers-2.6.24-19-generic 
The following packages have been kept back:
  nautilus-data python-gtkhtml2 python-libxml2 
The following partially installed packages will be configured:
  apt-utils bind9-host compiz-fusion-plugins-main deskbar-applet dnsutils 
  jockey-common jockey-gtk libbind9-30 libdns35 libgtk2.0-bin libisc35 
  libisccc30 libisccfg30 liblwres30 linux-headers-2.6.24-21 
  linux-headers-2.6.24-21-generic linux-libc-dev nautilus pciutils 
  thunderbird-locale-en-gb xkb-data xserver-xorg-video-intel 
0 packages upgraded, 0 newly installed, 2 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 68.3MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Error!
E: I wasn't able to locate file for the nautilus-data package. This might mean you need to manually fix this package.

any Ideas?

thanks in advance!

---

### Post by plucky on 2008-10-30
> sudo: unable to resolve host Programmer

Not sure about VMware but that error usually means your hostname in "/etc/hosts" is different.

From a terminal ```
hostname
cat /etc/hosts
``` and make sure the line "127.0.1.1" has the same hostname.

Good Luck

---

### Post by ajtaggs on 2008-10-30
Thanks for the response!

> **plucky said:**
> 
From a terminal ```
hostname
cat /etc/hosts
``` and make sure the line "127.0.1.1" has the same hostname.


Alright, I managed to get rid of the "Cannot resolve host name" message by adding the line "127.0.0.1 Programmer" to the hosts file.

When I try build-essential again, I get the exact same error, just without the "Cannot resolve host name" line

---

### Post by plucky on 2008-10-30
> **ajtaggs said:**
> Thanks for the response!



Alright, I managed to get rid of the "Cannot resolve host name" message by adding the line [color=red]"127.0.0.1 Programmer"[/color] to the hosts file.

When I try build-essential again, I get the exact same error, just without the "Cannot resolve host name" line

Is "127.0.0.1 Programmer"  a typo?

Try ```
sudo apt-get update
sudo apt-get install -f
``` and post any errors.

Try installing the missing file ```
sudo apt-get install nautilus-data
``` and see what happens.


Good Luck

---

### Post by ajtaggs on 2008-10-30
Nope, it wasn't a typo. Apperantly that will tell my computer to resolve Programmer (the name of my computer) as a loopback address and that helped somehow lol.

Anyways, these commands aer some of those I tried before posting, here is the results:

```
ajtaggs@Programmer:~$ sudo apt-get update
[sudo] password for ajtaggs: 
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_CA           
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_CA     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_CA       
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_CA     
Hit http://security.ubuntu.com hardy-security Release                          
Hit http://mirrors.kernel.org hardy Release.gpg                                
Ign http://mirrors.kernel.org hardy/main Translation-en_CA     
Hit http://mirrors.kernel.org hardy Release                    
Hit http://security.ubuntu.com hardy-security/main Packages                    
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources                     
Hit http://security.ubuntu.com hardy-security/restricted Sources               
Hit http://mirrors.kernel.org hardy/main Packages                              
Hit http://security.ubuntu.com hardy-security/universe Packages                
Hit http://security.ubuntu.com hardy-security/universe Sources 
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://ca.archive.ubuntu.com hardy Release.gpg             
Ign http://ca.archive.ubuntu.com hardy/main Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com hardy-updates Release.gpg
Ign http://ca.archive.ubuntu.com hardy-updates/main Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy-updates/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy-updates/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com hardy Release
Hit http://ca.archive.ubuntu.com hardy-updates Release
Hit http://ca.archive.ubuntu.com hardy/main Packages
Hit http://ca.archive.ubuntu.com hardy/restricted Packages
Hit http://ca.archive.ubuntu.com hardy/main Sources
Hit http://ca.archive.ubuntu.com hardy/restricted Sources
Hit http://ca.archive.ubuntu.com hardy/universe Packages
Hit http://ca.archive.ubuntu.com hardy/universe Sources
Hit http://ca.archive.ubuntu.com hardy/multiverse Packages
Hit http://ca.archive.ubuntu.com hardy/multiverse Sources
Hit http://ca.archive.ubuntu.com hardy-updates/main Packages
Hit http://ca.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://ca.archive.ubuntu.com hardy-updates/main Sources
Hit http://ca.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://ca.archive.ubuntu.com hardy-updates/universe Packages
Hit http://ca.archive.ubuntu.com hardy-updates/universe Sources
Hit http://ca.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://ca.archive.ubuntu.com hardy-updates/multiverse Sources
Reading package lists... Done

```

Looks like it ran fine...

The next one had all the usual stuff but here are the errors that occured:

```
ajtaggs@Programmer:~$ sudo apt-get install -f
dpkg: error processing /var/cache/apt/archives/nautilus-data_1%3a2.22.5.1-0ubuntu1_all.deb (--unpack):
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
dpkg: error processing /var/cache/apt/archives/python-gtkhtml2_2.19.1-0ubuntu7_i386.deb (--unpack):
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
dpkg: error processing /var/cache/apt/archives/python-libxml2_2.6.31.dfsg-2ubuntu1.2_i386.deb (--unpack):
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/nautilus-data_1%3a2.22.5.1-0ubuntu1_all.deb
 /var/cache/apt/archives/python-gtkhtml2_2.19.1-0ubuntu7_i386.deb
 /var/cache/apt/archives/python-libxml2_2.6.31.dfsg-2ubuntu1.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

When trying the 
```
sudo apt-get install nautilus-data
```
I got the exact same errors as I just listed,

---

### Post by plucky on 2008-10-30
```
127.0.0.1 Localhost
127.0.1.1 Programmer

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

That is what your /etc/hosts file should look like,unless it is different in VMware.

Your problem seem to be with the three files[list]
nautilus-data_1%3a2.22.5.1-0ubuntu1_all.deb
python-gtkhtml2_2.19.1-0ubuntu7_i386.deb
python-libxml2_2.6.31.dfsg-2ubuntu1.2_i386.deb[/list]

It might be an idea to delete them for the **/var/cache/apt/archives/**
so the system has to download them again from the repository.

But before that try ```
sudo dpkg --configure -a
``` to see if that fixes it.

---

### Post by ajtaggs on 2008-10-31
I tried sudo dpkg --configure -a and ran into a few errors so I went ahead and deleted those files.

Then I tried:

```
ajtaggs@Programmer:~$ sudo apt-get install nautilus-data
[sudo] password for ajtaggs: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  python-libxml2
Suggested packages:
  python-libxml2-dbg
The following packages will be upgraded:
  nautilus-data python-libxml2
2 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
8 not fully installed or removed.
Need to get 290kB/1191kB of archives.
After this operation, 41.0kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://ca.archive.ubuntu.com hardy/main python-gtkhtml2 2.19.1-0ubuntu7 [26.6kB]
Get:2 http://ca.archive.ubuntu.com hardy-updates/main python-libxml2 2.6.31.dfsg-2ubuntu1.2 [263kB]
Fetched 290kB in 33s (8633B/s)                                                 
(Reading database ... 120294 files and directories currently installed.)
Preparing to replace nautilus-data 1:2.22.3-0ubuntu2 (using .../nautilus-data_1%3a2.22.5.1-0ubuntu1_all.deb) ...
Unpacking replacement nautilus-data ...
/var/lib/dpkg/info/nautilus-data.postrm: 6: update-gconf-defaults: not found
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 6: update-gconf-defaults: not found
dpkg: error processing /var/cache/apt/archives/nautilus-data_1%3a2.22.5.1-0ubuntu1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 6: update-gconf-defaults: not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Preparing to replace python-gtkhtml2 2.19.1-0ubuntu7 (using .../python-gtkhtml2_2.19.1-0ubuntu7_i386.deb) ...
/var/lib/dpkg/info/python-gtkhtml2.prerm: 6: update-python-modules: not found
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: update-python-modules: not found
dpkg: error processing /var/cache/apt/archives/python-gtkhtml2_2.19.1-0ubuntu7_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/python-gtkhtml2.postinst: 6: update-python-modules: not found
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Preparing to replace python-libxml2 2.6.31.dfsg-2ubuntu1.1 (using .../python-libxml2_2.6.31.dfsg-2ubuntu1.2_i386.deb) ...
/var/lib/dpkg/info/python-libxml2.prerm: 6: update-python-modules: not found
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: update-python-modules: not found
dpkg: error processing /var/cache/apt/archives/python-libxml2_2.6.31.dfsg-2ubuntu1.2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/python-libxml2.postinst: 6: update-python-modules: not found
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/nautilus-data_1%3a2.22.5.1-0ubuntu1_all.deb
 /var/cache/apt/archives/python-gtkhtml2_2.19.1-0ubuntu7_i386.deb
 /var/cache/apt/archives/python-libxml2_2.6.31.dfsg-2ubuntu1.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Hmm, might it be that my current install is currupt somehow? 

Thanks for the suggestions :)

---

### Post by ajtaggs on 2008-10-31
SOLVED !!!!!!!!!!

Ok, it was all caused by a broken symlink, I searched my /usr/bin directory and found the culprit. There was a broken link named *python*, and a file named *python25*.

This is how I fixed it for anyone having similar problems:

```
>>> cd /usr/bin
>>> sudo rm python
>>> sudo cp python25 python2.5
>>> sudo ln -s /usr/bin/python2.5 /usr/bin/python
```

You may need to change the code slightly depending upon what version of Python you are running. just make sure python points to a file named pythonX.X where X.X is your version number.

Thanks for the replies!!!

---

