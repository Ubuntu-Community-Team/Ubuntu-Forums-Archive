---
title: "[SOLVED] Problems installing or updating programs/updates"
date: 2008-07-20
forum: General Help
---

### Post by Newuser1111 on 2008-07-20
I get this kind of an error,

```
W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.24-19-386_2.6.24-19.36_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
```(That one was from an update, but they all get the "Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused")

---

### Post by zvacet on 2008-07-21
```
cat /etc/apt/sources.list
```

Post it here.

---

### Post by iaculallad on 2008-07-21
On your terminal, try this:

```
unset http_proxy
sudo apt-get update
```

---

### Post by Newuser1111 on 2008-07-21
> **iaculallad said:**
> On your terminal, try this:

```
unset http_proxy
sudo apt-get update
```
```
djk@djk-desktop:~$ unset http_proxy
djk@djk-desktop:~$ sudo apt-get update
[sudo] password for djk: 
Hit http://us.archive.ubuntu.com hardy Release.gpg                             
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US                  
Hit http://security.ubuntu.com hardy-security Release.gpg            
Ign http://security.ubuntu.com hardy-security/main Translation-en_US 
Hit http://wine.budgetdedicated.com hardy Release.gpg                
Ign http://wine.budgetdedicated.com hardy/main Translation-en_US     
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg           
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Hit http://wine.budgetdedicated.com hardy Release
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release
Hit http://us.archive.ubuntu.com hardy-updates Release                         
Hit http://security.ubuntu.com hardy-security/main Packages                    
Ign http://wine.budgetdedicated.com hardy/main Packages              
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages           
Hit http://us.archive.ubuntu.com hardy/main Sources                  
Hit http://security.ubuntu.com hardy-security/restricted Packages    
Hit http://security.ubuntu.com hardy-security/main Sources           
Hit http://security.ubuntu.com hardy-security/restricted Sources     
Hit http://wine.budgetdedicated.com hardy/main Packages              
Hit http://us.archive.ubuntu.com hardy/restricted Sources            
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Reading package lists... Done
djk@djk-desktop:~$ 

```

> **zvacet said:**
> ```
cat /etc/apt/sources.list
```

Post it here.

```
djk@djk-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

---

### Post by iaculallad on 2008-07-21
With that output from:

```
unset http_proxy
sudo apt-get update
```

You're good to go. Try:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Newuser1111 on 2008-07-21
> **iaculallad said:**
> With that output from:

```
unset http_proxy
sudo apt-get update
```

You're good to go. Try:

```
sudo apt-get update && sudo apt-get upgrade
```
Still got some errors,
```
djk@djk-desktop:~$ sudo apt-get update && sudo apt-get upgrade
Err http://wine.budgetdedicated.com hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://wine.budgetdedicated.com hardy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com hardy-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com hardy-security/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com hardy-security/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com hardy-security/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com hardy-security/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done           
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/hardy/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/hardy/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bind9-host dnsutils libbind9-30 libisccfg30
The following packages will be upgraded:
  evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-plugins gtk2-engines-murrine
  gtk2-engines-ubuntulooks libcamel1.2-11 libebook1.2-9 libecal1.2-7
  libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9
  libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3
  libgdata-google1.2-1 libgdata1.2-1 libisc32 libisccc30 liblwres30
  libpango1.0-0 libpango1.0-common libpcre3 libpoppler-glib2 libpoppler2
  linux-headers-2.6.24-19 linux-headers-2.6.24-19-generic
  linux-image-2.6.24-19-386 linux-image-2.6.24-19-generic
  linux-image-2.6.24-19-openvz linux-image-2.6.24-19-rt
  linux-image-2.6.24-19-server linux-image-2.6.24-19-virtual linux-libc-dev
  linux-restricted-modules-2.6.24-19-generic linux-restricted-modules-common
  nvidia-glx-new nvidia-glx-new-dev nvidia-new-kernel-source poppler-utils
  wine
42 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 167MB/168MB of archives.
After this operation, 147kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err http://security.ubuntu.com hardy-security/main linux-image-2.6.24-19-386 2.6.24-19.36
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com hardy-security/main linux-image-2.6.24-19-generic 2.6.24-19.36
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com hardy-security/universe linux-image-2.6.24-19-openvz 2.6.24-19.36
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com hardy-security/universe linux-image-2.6.24-19-rt 2.6.24-19.36
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com hardy-security/main linux-image-2.6.24-19-server 2.6.24-19.36
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com hardy-security/main linux-image-2.6.24-19-virtual 2.6.24-19.36
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com hardy-security/main linux-headers-2.6.24-19 2.6.24-19.36
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com hardy-security/main linux-headers-2.6.24-19-generic 2.6.24-19.36
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com hardy-security/main linux-libc-dev 2.6.24-19.36
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://wine.budgetdedicated.com hardy/main wine 1.1.1~winehq0~ubuntu~8.04-0ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/main libecal1.2-7 2.22.3-0ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/main libedata-book1.2-2 2.22.3-0ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/main libedata-cal1.2-6 2.22.3-0ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/main libegroupwise1.2-13 2.22.3-0ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/main libgdata1.2-1 2.22.3-0ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/main libgdata-google1.2-1 2.22.3-0ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/main evolution 2.22.3.1-0ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/main evolution-common 2.22.3.1-0ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/main libpango1.0-common 1.20.5-0ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/main libpango1.0-0 1.20.5-0ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/main libedataserverui1.2-8 2.22.3-0ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/main libexchange-storage1.2-3 2.22.3-0ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/main evolution-plugins 2.22.3.1-0ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/main gtk2-engines-murrine 0.53.1-1ubuntu2
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/main gtk2-engines-ubuntulooks 0.9.12-12
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/main libpcre3 7.4-1ubuntu2.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/main libpoppler2 0.6.4-1ubuntu3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/main libpoppler-glib2 0.6.4-1ubuntu3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/main poppler-utils 0.6.4-1ubuntu3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com hardy-security/main libpcre3 7.4-1ubuntu2.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com hardy-security/restricted linux-restricted-modules-common 2.6.24.13-19.45
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com hardy-security/restricted linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com hardy-security/restricted nvidia-glx-new 169.12+2.6.24.13-19.45
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com hardy-security/restricted nvidia-glx-new-dev 169.12+2.6.24.13-19.45
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com hardy-security/restricted nvidia-new-kernel-source 169.12+2.6.24.13-19.45
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.24-19-386_2.6.24-19.36_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.24-19-generic_2.6.24-19.36_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/l/linux/linux-image-2.6.24-19-openvz_2.6.24-19.36_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/l/linux/linux-image-2.6.24-19-rt_2.6.24-19.36_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.24-19-server_2.6.24-19.36_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.24-19-virtual_2.6.24-19.36_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_1.1.1~winehq0~ubuntu~8.04-0ubuntu1_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libecal1.2-7_2.22.3-0ubuntu1_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-book1.2-2_2.22.3-0ubuntu1_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-cal1.2-6_2.22.3-0ubuntu1_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libegroupwise1.2-13_2.22.3-0ubuntu1_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libgdata1.2-1_2.22.3-0ubuntu1_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libgdata-google1.2-1_2.22.3-0ubuntu1_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.22.3.1-0ubuntu1_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.22.3.1-0ubuntu1_all.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-common_1.20.5-0ubuntu1_all.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.20.5-0ubuntu1_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserverui1.2-8_2.22.3-0ubuntu1_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libexchange-storage1.2-3_2.22.3-0ubuntu1_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-plugins_2.22.3.1-0ubuntu1_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines-murrine/gtk2-engines-murrine_0.53.1-1ubuntu2_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntulooks/gtk2-engines-ubuntulooks_0.9.12-12_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcre3_7.4-1ubuntu2.1_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler2_0.6.4-1ubuntu3_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler-glib2_0.6.4-1ubuntu3_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.24-19_2.6.24-19.36_all.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.24-19-generic_2.6.24-19.36_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.24-19.36_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/linux-restricted-modules-common_2.6.24.13-19.45_all.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/linux-restricted-modules-2.6.24-19-generic_2.6.24.13-19.45_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-19.45_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new-dev_169.12+2.6.24.13-19.45_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-new-kernel-source_169.12+2.6.24.13-19.45_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.6.4-1ubuntu3_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
djk@djk-desktop:~$ 

```

and I am not using a proxy.

---

### Post by iaculallad on 2008-07-21
Uuhh :confused: 
Try changing your Download Server to Main Server from System->Administration->Software Sources, under "Ubuntu Software" tab. Click on Close and select the Reload button on the next window.

Retry updating from terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Newuser1111 on 2008-07-21
> **iaculallad said:**
> Uuhh :confused: 
Try changing your Download Server to Main Server from System->Administration->Software Sources, under "Ubuntu Software" tab. Click on Close and select the Reload button on the next window.

Retry updating from terminal:

```
sudo apt-get update && sudo apt-get upgrade
```
After I clicked Reload,
```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/hardy/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/hardy/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

And "sudo apt-get update && sudo apt-get upgrade" did:
```
djk@djk-desktop:~$ sudo apt-get update && sudo apt-get upgrade
Err http://archive.ubuntu.com hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com hardy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com hardy/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com hardy/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com hardy/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com hardy-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com hardy-updates/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com hardy-updates/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com hardy-updates/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com hardy-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com hardy-security/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com hardy-security/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com hardy-security/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com hardy-security/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://wine.budgetdedicated.com hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://wine.budgetdedicated.com hardy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/hardy/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/hardy/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  wine
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 7480kB of archives.
After this operation, 115kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://wine.budgetdedicated.com hardy/main wine 1.1.1~winehq0~ubuntu~8.04-0ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_1.1.1~winehq0~ubuntu~8.04-0ubuntu1_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
djk@djk-desktop:~$ 

```

---

### Post by Newuser1111 on 2008-07-21
I got it working.
It might have been something wrong with the WiFi, because now it's working after I clicked on the "Fix WiFi.sh" icon on my desktop.

---

