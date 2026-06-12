---
title: "Failed upgrade from 7.10"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by darkorical on 2009-03-10
I have decided to upgrade from 

```
dan@Linux:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"

```
to the newest version 
so I ran the following 

sudo apt-get update

Fetched 347kB in 5s (62.9kB/s)
Reading package lists... Done

sudo apt-get upgrade

dan@Linux:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  belocs-locales-bin bind9-host build-essential command-not-found cpp dnsutils
  freetds-dev g++ gcc gettext grub initscripts libapache2-mod-php5 libbind9-30 libcairo2
  libcurl3-gnutls libdns35 libgtk2.0-0 libgtk2.0-bin libisccc30 libisccfg30
  libpango1.0-0 libsybdb5 linux-image-server linux-server ntfs-3g ntpdate parted
  php5-common php5-gd php5-imap php5-mcrypt php5-mysql php5-sybase phpmyadmin pppoeconf
  proftpd samba samba-common smbfs sqsh tdsodbc w3m wpasupplicant
0 upgraded, 0 newly installed, 0 to remove and 44 not upgraded.

and finally 
sudo apt-get dist-upgrade

```
dan@Linux:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  belocs-locales-bin bind9-host build-essential command-not-found cpp dnsutils
  freetds-dev g++ gcc gettext grub initscripts libapache2-mod-php5 libbind9-30 libcairo2
  libcurl3-gnutls libdns35 libgtk2.0-0 libgtk2.0-bin libisccc30 libisccfg30
  libpango1.0-0 libsybdb5 linux-image-server linux-server ntfs-3g ntpdate parted
  php5-common php5-gd php5-imap php5-mcrypt php5-mysql php5-sybase phpmyadmin pppoeconf
  proftpd samba samba-common smbfs sqsh tdsodbc w3m wpasupplicant
0 upgraded, 0 newly installed, 0 to remove and 44 not upgraded.
dan@Linux:~$
dan@Linux:~$ sudo apt-get dist-update
E: Invalid operation dist-update
dan@Linux:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  startup-tasks system-services upstart upstart-compat-sysv upstart-logd
The following NEW packages will be installed:
  apt-file ca-certificates cpp-4.3 curl dbconfig-common freetds-common g++-4.3 gcc-4.3
  grub-common libapt-pkg-perl libbind9-40 libc-client2007b libcap2 libconfig-file-perl
  libcroco3 libct4 libcurl3 libdirectfb-1.0-0 libdns45 libgmp3c2 libgpm2 libisc35
  libisc45 libisccc40 libisccfg40 liblist-moreutils-perl liblwres40 libmpfr1ldbl
  libntfs-3g31 libparted1.8-10 libpcsclite1 libssh2-1 libstdc++6-4.3-dev libtalloc1
  libts-0.0-0 libwbclient0 linux-image-2.6.24-23-server
  linux-ubuntu-modules-2.6.24-23-server lockfile-progs menu modconf proftpd-basic
  proftpd-mod-ldap proftpd-mod-mysql proftpd-mod-pgsql sysvinit sysvinit-utils
The following packages have been kept back:
  belocs-locales-bin
The following packages will be upgraded:
  bind9-host build-essential command-not-found cpp dnsutils freetds-dev g++ gcc gettext
  grub initscripts libapache2-mod-php5 libbind9-30 libcairo2 libcurl3-gnutls libdns35
  libgtk2.0-0 libgtk2.0-bin libisccc30 libisccfg30 libpango1.0-0 libsybdb5
  linux-image-server linux-server ntfs-3g ntpdate parted php5-common php5-gd php5-imap
  php5-mcrypt php5-mysql php5-sybase phpmyadmin pppoeconf proftpd samba samba-common
  smbfs sqsh tdsodbc w3m wpasupplicant
43 upgraded, 47 newly installed, 5 to remove and 1 not upgraded.
Need to get 0B/70.9MB of archives.
After this operation, 144MB of additional disk space will be used.
Do you want to continue [Y/n]?

```

Y

```

Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 48002 files and directories currently installed.)
Removing startup-tasks ...
Removing system-services ...
Removing upstart-logd ...
dpkg: upstart-compat-sysv: dependency problems, but removing anyway as you request:
 apparmor depends on upstart-compat-sysv | sysvinit; however:
  Package upstart-compat-sysv is to be removed.
  Package sysvinit is not installed.
Removing upstart-compat-sysv ...
Removing upstart ...
Processing triggers for man-db ...
(Reading database ... 47964 files and directories currently installed.)
Unpacking sysvinit-utils (from .../sysvinit-utils_2.86.ds1-61_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/sysvinit-utils_2.86.ds1-61_i386.deb (--unpack):
 trying to overwrite `/sbin/sulogin', which is also in package sysvutils
Errors were encountered while processing:
 /var/cache/apt/archives/sysvinit-utils_2.86.ds1-61_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Ive been searching old forum posts for 2 days now and not finding anything that seems to help

can someone please help me with this

---

### Post by Neo_The_User on 2009-03-10
Wild guess:

```

sudp dpkg --configure sysvinit-utils && sudo apt-get install -f

```

Good luck.

---

### Post by scottuss on 2009-03-10
Someone correct me if I'm wrong, but you can't upgrade from 7.10 to the latest version. You have to be at 8.10? Again, I may be wrong as I don't do upgrades. I always recommend in all my posts regarding upgrades that they not be done. They tend to break things, and a clean install is often faster / less breakages. Don't take my word, do a search around the forums (which you've already done so I'm sure you know about it now!)

In your situation as it is, I personally would now back up my /home directory and do a clean install.

---

### Post by Neo_The_User on 2009-03-10
> **scottuss said:**
> Someone correct me if I'm wrong, but you can't upgrade from 7.10 to the latest version. You have to be at 8.10? Again, I may be wrong as I don't do upgrades. I always recommend in all my posts regarding upgrades that they not be done. They tend to break things, and a clean install is often faster / less breakages. Don't take my word, do a search around the forums (which you've already done so I'm sure you know about it now!)

In your situation as it is, I personally would now back up my /home directory and do a clean install.

Clean install FTW but I'm going to try and help him out best I can.

---

### Post by avtolle on 2009-03-10
Direct upgrade from 7.10 to 8.10 isn't supported; if you are going to do "network upgrades", need to move from 7.10 to 8.04 to 8.10 sequentially. If you want to go to 8.10 from 7.10, a fresh install is the way to do it, as set out *supra*.

---

### Post by Silent Warrior on 2009-03-10
[Well, never effin' mind. :p I'll leave the link, though.]

Here's a link to a how-to you might like: [Create a list of installed packages]("http://ubuntuforums.org/showthread.php?t=261366")

---

### Post by Neo_The_User on 2009-03-10
> **avtolle said:**
> Direct upgrade from 7.10 to 8.10 isn't supported; if you are going to do "network upgrades", need to move from 7.10 to 8.04 to 8.10 sequentially. If you want to go to 8.10 from 7.10, a fresh install is the way to do it, as set out *supra*.

Well I mean I could guide him through on nursing his computer along from 7.10 to 8.10. Not rocket science.

---

### Post by scottuss on 2009-03-10
@Neo_The_User, you may as well try it mate, it can't hurt anything :)

---

### Post by Neo_The_User on 2009-03-10
> **scottuss said:**
> @Neo_The_User, you may as well try it mate, it can't hurt anything :)

Exactly. It's already messed up. Can't get any worse. I would rather just do a clean install though.

---

### Post by darkorical on 2009-03-10
I guess I should have mentioned that this is server edition. This machine is a internal webserver that houses over 3000 records of current and past orders as well as our entire inventory database

while the database is backed up nightly having it down is not an option at this point and unfortunatly putting this together was a learning experiance and I am quite certain that I do not remember what I did to get it running with itself let alone our windows 2003 server.
its currently sitting at 239 days uptime due my companys reliance on this machine being up at all times

---

### Post by avtolle on 2009-03-10
See [http://www.ubuntu.com/getubuntu/upgrading-8.04#head-e059d5452a24b50d09c64df48058ef2d834eb197](http://www.ubuntu.com/getubuntu/upgrading-8.04#head-e059d5452a24b50d09c64df48058ef2d834eb197) for upgrading from 7.10 server to 8.04 server.

---

### Post by darkorical on 2009-03-10
thats what I tried first 
```
sudo aptitude install update-manager-core
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Reading task descriptions... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 40 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Reading task descriptions... Done

dan@Linux:~$ sudo do-release-upgrade
Checking for a new ubuntu release
current dist not found in meta-release file
No new release found

```

---

### Post by darkorical on 2009-03-10
and now my webmin tells me that im actually running generic linux

System hostname 	Linux
Operating system 	Generic Linux 2.6
Webmin version 	1.450
Time on system 	Tue Mar 10 16:19:31 2009
Kernel and CPU 	Linux 2.6.24-19-server on i686
System uptime 	238 days, 23 hours, 33 minutes
CPU load averages 	0.12 (1 min) 0.04 (5 mins) 0.01 (15 mins)
Real memory 	1.95 GB total, 272.77 MB used
	
Virtual memory 	5.71 GB total, 0 bytes used
	
Local disk space 	141.09 GB total, 11.17 GB used

---

### Post by scottuss on 2009-03-10
> **darkorical said:**
> I guess I should have mentioned that this is server edition. This machine is a internal webserver that houses over 3000 records of current and past orders as well as our entire inventory database

while the database is backed up nightly having it down is not an option at this point and unfortunatly putting this together was a learning experiance and I am quite certain that I do not remember what I did to get it running with itself let alone our windows 2003 server.
its currently sitting at 239 days uptime due my companys reliance on this machine being up at all times

With the greatest of respect: you have to be joking? I can't believe that you didn't research upgrading before attempting this on a production machine.

---

### Post by Neo_The_User on 2009-03-10
> **scottuss said:**
> With the greatest of respect: you have to be joking? I can't believe that you didn't research upgrading before attempting this on a production machine.

AGREED! hehehe

---

### Post by darkorical on 2009-03-11
> **scottuss said:**
> With the greatest of respect: you have to be joking? I can't believe that you didn't research upgrading before attempting this on a production machine.

I agree as well

again something I should point out the machine still works just fine. and I usually operate on the idea of if its not busted (and does the job you want it to) don't upgrade it. but word came down from higher up to make sure all software was up to date and to check for any hardware upgrade needs. So I admit I kinda jumped in hoping dist-upgrade would work

but like I said the machine does still work just fine and do its job very well I was just hoping to upgrade to the next version Before this one reaches the end of its lifespan

so if there is any help I could get doing this it would be greatly appreciated.

Alternativly I am tempted to set up a secondary machine and install the newest version on it and get it going fully then simply swap machines

---

### Post by darkorical on 2009-03-11
will it work (in theory) to upgrade to 8.04 by downloading the 8.04 image and mount it using 
```

sudo mkdir -p /mnt/disk
sudo mount -o loop disk1.iso /mnt/disk

``` 
*assuming proper name for iso

then run 

```

sudo /mnt/disk/cdromupgrade

```

---

### Post by avtolle on 2009-03-11
Yes, in theory that should work; however, I don't know that it will to your satisfaction. Obviously, I've never tried it or I would have a better answer.

As I understand it, the upgrade from CD option is limited to the alternate iso image. I'm also understanding that to do an upgrade from CD, the CD is to be placed in the drive (mounted) and a message then appears on the desktop offering the ability to upgrade from it. You will note I've stated that the alternate cd  iso image permits this capability; as you will be trying this (as I understand it) with the server iso, I do not know whether the server iso allows for an upgrade in this fashion. If you are willing to use the alternate install iso, I believe even if you specify a comman line only installation (if this is still possible with the alternate iso; I've not checked this for several releases), you will end up with a "desktop" vs. "server" kernel, which may or may not be desired. And, in reality, it may not be a problem for you; I just don't know.

The upgrade instructions clearly contemplate this (upgrade from cd), so it should work (in theory), but the result may not quite be what you want.

---

