---
title: "update issues fresh 9.04 install"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by lucasta on 2009-08-30
I am attempting to dual boot Vista/Jaunty on a Compaq Presario F767NR and I'm having issues that seem to be very uncommon, haven't found much in any forums.  I'm new to Ubuntu/Linux but it seems that I either get archive errors (bzip2 related) or unmet dependencies.  I am also having issues with my Nvidia 7000m and activating drivers.

output from sudo apt-get update
```
lucas@lucas-laptop:~$ sudo apt-get update
Hit http://archive.linux.duke.edu jaunty Release.gpg
Ign http://archive.linux.duke.edu jaunty/restricted Translation-en_US
Ign http://archive.linux.duke.edu jaunty/universe Translation-en_US
Ign http://archive.linux.duke.edu jaunty/main Translation-en_US
Ign http://archive.linux.duke.edu jaunty/multiverse Translation-en_US
Hit http://archive.linux.duke.edu jaunty-updates Release.gpg
Ign http://archive.linux.duke.edu jaunty-updates/restricted Translation-en_US
Ign http://archive.linux.duke.edu jaunty-updates/universe Translation-en_US
Ign http://archive.linux.duke.edu jaunty-updates/main Translation-en_US
Ign http://archive.linux.duke.edu jaunty-updates/multiverse Translation-en_US
Hit http://archive.linux.duke.edu jaunty-security Release.gpg
Ign http://archive.linux.duke.edu jaunty-security/restricted Translation-en_US
Ign http://archive.linux.duke.edu jaunty-security/universe Translation-en_US
Ign http://archive.linux.duke.edu jaunty-security/main Translation-en_US
Ign http://archive.linux.duke.edu jaunty-security/multiverse Translation-en_US
Hit http://archive.linux.duke.edu jaunty Release
Hit http://archive.linux.duke.edu jaunty-updates Release                      
Hit http://archive.linux.duke.edu jaunty-security Release                     
Hit http://archive.linux.duke.edu jaunty/restricted Packages
Get:1 http://archive.linux.duke.edu jaunty/universe Packages [4757kB]
Hit http://archive.linux.duke.edu jaunty/main Packages                         
Hit http://archive.linux.duke.edu jaunty/multiverse Packages                   
Hit http://archive.linux.duke.edu jaunty-updates/restricted Packages           
Hit http://archive.linux.duke.edu jaunty-updates/universe Packages             
Hit http://archive.linux.duke.edu jaunty-updates/main Packages                 
Hit http://archive.linux.duke.edu jaunty-updates/multiverse Packages           
99% [1 Packages bzip2 10784768] [Connecting to archive.linux.duke.edu (152.3.10
bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://archive.linux.duke.edu jaunty/universe Packages                     
  Sub-process bzip2 returned an error code (2)
Hit http://archive.linux.duke.edu jaunty-security/restricted Packages          
Hit http://archive.linux.duke.edu jaunty-security/universe Packages            
Hit http://archive.linux.duke.edu jaunty-security/main Packages                
Hit http://archive.linux.duke.edu jaunty-security/multiverse Packages          
Fetched 2386kB in 13s (174kB/s)                                                
W: Failed to fetch http://archive.linux.duke.edu/ubuntu/dists/jaunty/universe/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.
lucas@lucas-laptop:~$ 
```output from 'sudo apt-get -f install'
```
lucas@lucas-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgl1-mesa-dri linux-image-2.6.28-15-generic perl-modules
Suggested packages:
  libglide3 fdutils linux-doc-2.6.28 linux-source-2.6.28
The following NEW packages will be installed:
  linux-image-2.6.28-15-generic
The following packages will be upgraded:
  libgl1-mesa-dri perl-modules
2 upgraded, 1 newly installed, 0 to remove and 188 not upgraded.
3 not fully installed or removed.
Need to get 0B/30.5MB of archives.
After this operation, 95.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 102056 files and directories currently installed.)
Preparing to replace perl-modules 5.10.0-19ubuntu1 (using .../perl-modules_5.10.0-19ubuntu1.1_all.deb) ...
Unpacking replacement perl-modules ...
dpkg: error processing /var/cache/apt/archives/perl-modules_5.10.0-19ubuntu1.1_all.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking linux-image-2.6.28-15-generic (from .../linux-image-2.6.28-15-generic_2.6.28-15.49_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.28-15-generic_2.6.28-15.49_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Preparing to replace libgl1-mesa-dri 7.4-0ubuntu3 (using .../libgl1-mesa-dri_7.4-0ubuntu3.2_i386.deb) ...
Unpacking replacement libgl1-mesa-dri ...
lzma: Decoder error
dpkg-deb: subprocess <decompress> returned error exit status 1
dpkg: error processing /var/cache/apt/archives/libgl1-mesa-dri_7.4-0ubuntu3.2_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/dri/i810_dri.so')
Errors were encountered while processing:
 /var/cache/apt/archives/perl-modules_5.10.0-19ubuntu1.1_all.deb
 /var/cache/apt/archives/linux-image-2.6.28-15-generic_2.6.28-15.49_i386.deb
 /var/cache/apt/archives/libgl1-mesa-dri_7.4-0ubuntu3.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
lucas@lucas-laptop:~$ 

```

---

### Post by raymondh on 2009-08-31
Try changing servers (system > administration > software sources > ubuntu software > download > choose OTHER)

Also, kindly review or copy/paste output of

```
cat /etc/apt/sources.list
```

---

### Post by lucasta on 2009-09-02
thanks for the reply raymond*, *i have already tried 10+ servers to see if that was the problem, but none seemed to remove the error. some even added more. but here is the output of the cat command, as i have no idea what i'm looking for in it. 

```
lucas@lucas-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner
deb http://mirrors.rit.edu/ubuntu/ jaunty restricted main universe
deb http://security.ubuntu.com/ubuntu/ jaunty-security restricted main universe
deb http://mirrors.rit.edu/ubuntu/ jaunty-updates restricted main universe

lucas@lucas-laptop:~$ 

```

---

### Post by lucasta on 2009-09-05
bump

---

