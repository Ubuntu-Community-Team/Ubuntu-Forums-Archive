---
title: "help in updating ...again argh =d"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by KEE on 2009-04-22
```
me@me-desktop:~$ echo 'deb http://ppa.launchpad.net/reacocard-awn/ubuntu intrepid main' echo 'deb http://ppa.launchpad.net/reacocard-awn/ubuntu intrepid main'  |  sudo tee -a /etc/apt/sources.list
[sudo] password for me: 
deb http://ppa.launchpad.net/reacocard-awn/ubuntu intrepid main echo deb http://ppa.launchpad.net/reacocard-awn/ubuntu intrepid main
me@me-desktop:~$ sudo apt-get update
Hit http://security.ubuntu.com intrepid-security Release.gpg
Ign http://security.ubuntu.com intrepid-security/main Translation-en_CA
Hit http://ca.archive.ubuntu.com intrepid Release.gpg
Ign http://ca.archive.ubuntu.com intrepid/main Translation-en_CA
Ign http://ppa.launchpad.net intrepid Release.gpg
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_CA
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_CA
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com intrepid/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com intrepid/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com intrepid/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com intrepid-updates Release.gpg        
Ign http://ppa.launchpad.net intrepid/main Translation-en_CA         
Ign http://ppa.launchpad.net intrepid/echo Translation-en_CA
Ign http://ppa.launchpad.net intrepid/deb Translation-en_CA
Ign http://ppa.launchpad.net intrepid/http://ppa.launchpad.net/reacocard-awn/ubuntu Translation-en_CA
Hit http://security.ubuntu.com intrepid-security Release
Hit http://ca.archive.ubuntu.com intrepid-updates/main Translation-en_CA
Hit http://ca.archive.ubuntu.com intrepid-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com intrepid-updates/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com intrepid-updates/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com intrepid Release
Ign http://ppa.launchpad.net intrepid/intrepid Translation-en_CA
Get:1 http://ppa.launchpad.net intrepid Release [27.6kB]            
Hit http://ca.archive.ubuntu.com intrepid-updates Release                      
Hit http://security.ubuntu.com intrepid-security/main Packages             
Hit http://ca.archive.ubuntu.com intrepid/main Packages                    
Hit http://ca.archive.ubuntu.com intrepid/restricted Packages
Hit http://ca.archive.ubuntu.com intrepid/main Sources
Hit http://ca.archive.ubuntu.com intrepid/restricted Sources
Hit http://ca.archive.ubuntu.com intrepid/universe Packages
Hit http://security.ubuntu.com intrepid-security/restricted Packages
Hit http://security.ubuntu.com intrepid-security/main Sources
Hit http://security.ubuntu.com intrepid-security/restricted Sources
Hit http://security.ubuntu.com intrepid-security/universe Packages
Hit http://security.ubuntu.com intrepid-security/universe Sources
Hit http://ca.archive.ubuntu.com intrepid/universe Sources
Hit http://ca.archive.ubuntu.com intrepid/multiverse Packages
Hit http://ca.archive.ubuntu.com intrepid/multiverse Sources
Hit http://ca.archive.ubuntu.com intrepid-updates/main Packages
Hit http://ca.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://ca.archive.ubuntu.com intrepid-updates/main Sources
Hit http://ca.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://ca.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Packages        
Hit http://security.ubuntu.com intrepid-security/multiverse Sources         
Hit http://ca.archive.ubuntu.com intrepid-updates/universe Sources          
Hit http://ca.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://ca.archive.ubuntu.com intrepid-updates/multiverse Sources
Ign http://ppa.launchpad.net intrepid/main Packages
Ign http://ppa.launchpad.net intrepid/echo Packages
Ign http://ppa.launchpad.net intrepid/deb Packages
Ign http://ppa.launchpad.net intrepid/http://ppa.launchpad.net/reacocard-awn/ubuntu Packages
Ign http://ppa.launchpad.net intrepid/intrepid Packages
Get:2 http://ppa.launchpad.net intrepid/main Packages [1733B]
Err http://ppa.launchpad.net intrepid/echo Packages
  404 Not Found
Err http://ppa.launchpad.net intrepid/deb Packages
  404 Not Found
Err http://ppa.launchpad.net intrepid/http://ppa.launchpad.net/reacocard-awn/ubuntu Packages
  404 Not Found
Err http://ppa.launchpad.net intrepid/intrepid Packages
  404 Not Found
Fetched 29.4kB in 2s (11.1kB/s)
W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/echo/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/deb/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/http://ppa.launchpad.net/reacocard-awn/ubuntu/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/intrepid/binary-i386/Packages.gz  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
me@me-desktop:~$ sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
me@me-desktop:~$ 

```

---

### Post by KEE on 2009-04-22
hmmm is this because i didnt set it to the main server?

---

### Post by KEE on 2009-04-22
man ubuntu sucks latly =( i just reinstalled in nothing works anymore > GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/echo/binary-i386/Packages.gz](http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/echo/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/deb/binary-i386/Packages.gz](http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/deb/binary-i386/Packages.gz)  404 Not Found

---

### Post by stumbleUpon on 2009-04-22
If you are using Hardy or Intrepid then awn is in the repositories. Install it from there.

```
sudo aptitude install avant-window-navigator
```



Also check your /etc/apt/sources.list file. There seem to be some incorrectly typed entries.

> Err [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/echo Packages
  404 Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/deb Packages
  404 Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/http://ppa.launchpad.net/reacocard-awn/ubuntu Packages
  404 Not Found


Next, it looks like you are either running synaptic, some apt-get or aptitude process.

> 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Kill all such processes that you might be running

---

### Post by Partyboi2 on 2009-04-22
Hi, looks like you have the cdrom set as your repo source. Open up Software Sources and on the first tab untick the box under "installable from CDROM/DVD"

---

### Post by KEE on 2009-04-22
> **Partyboi2 said:**
> Hi, looks like you have the cdrom set as your repo source. Open up Software Sources and on the first tab untick the box under "installable from CDROM/DVD"ok its unticked but I still get errors

```
GPG error: http://packages.medibuntu.org intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/echo/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/deb/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/http://ppa.launchpad.net/reacocard-awn/ubuntu/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/intrepid/binary-i386/Packages.gz  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by calrogman on 2009-04-22
> **KEE said:**
> ```
GPG error: http://packages.medibuntu.org intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/echo/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/deb/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/http://ppa.launchpad.net/reacocard-awn/ubuntu/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/intrepid/binary-i386/Packages.gz  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

4 of your repositories do not exist (hence the 404 errors) and the top one needs verified.

To verify the top one (the only working repo) use```
sudo apt-get update && sudo apt-get install medibuntu-keyring
```You will be asked if you want to install this package as it still needs to be verified, if you press yes it will add the medibuntu public PGP key to your keyring.

---

### Post by KEE on 2009-04-22
> **calrogman said:**
> 4 of your repositories do not exist (hence the 404 errors) and the top one needs verified.

To verify the top one (the only working repo) use```
sudo apt-get update && sudo apt-get install medibuntu-keyring
```You will be asked if you want to install this package as it still needs to be verified, if you press yes it will add the medibuntu public PGP key to your keyring.im getting errors there too =(

```
W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/echo/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/deb/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/http://ppa.launchpad.net/reacocard-awn/ubuntu/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/intrepid/binary-i386/Packages.gz  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by Partyboi2 on 2009-04-22
deleted

---

### Post by KEE on 2009-04-22
> **calrogman said:**
> 4 of your repositories do not exist (hence the 404 errors) and the top one needs verified.

To verify the top one (the only working repo) use```
sudo apt-get update && sudo apt-get install medibuntu-keyring
```You will be asked if you want to install this package as it still needs to be verified, if you press yes it will add the medibuntu public PGP key to your keyring.

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
``` i get ```
W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/echo/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/deb/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/http://ppa.launchpad.net/reacocard-awn/ubuntu/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/intrepid/binary-i386/Packages.gz  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```and for  ```
sudo apt-get update && sudo apt-get install medibuntu-keyring
``` i get ```
W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/echo/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/deb/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/http://ppa.launchpad.net/reacocard-awn/ubuntu/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/intrepid/binary-i386/Packages.gz  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by jpeddicord on 2009-04-22
Merged your threads together; please do not make duplicate posts. :)

---

### Post by KEE on 2009-04-22
> **jacobmp92 said:**
> Merged your threads together; please do not make duplicate posts. :)

ok, thank you=)  i didn't know they'd coexist.

---

### Post by KEE on 2009-04-24
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
``` i get ```
W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/echo/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/deb/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/http://ppa.launchpad.net/reacocard-awn/ubuntu/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/intrepid/binary-i386/Packages.gz  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```and for  ```
sudo apt-get update && sudo apt-get install medibuntu-keyring
``` i get ```
W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/echo/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/deb/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/http://ppa.launchpad.net/reacocard-awn/ubuntu/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/intrepid/intrepid/binary-i386/Packages.gz  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by Partyboi2 on 2009-04-24
Can you open a terminal and post your sources.list
```
cat /etc/apt/sources.list
```

---

### Post by KEE on 2009-04-24
> **Partyboi2 said:**
> Can you open a terminal and post your sources.list
```
cat /etc/apt/sources.list
```yes =) 
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb http://ppa.launchpad.net/reacocard-awn/ubuntu intrepid main echo deb http://ppa.launchpad.net/reacocard-awn/ubuntu intrepid main
deb http://ppa.launchpad.net/reacocard-awn/ubuntu intrepid main
deb http://ppa.launchpad.net/reacocard-awn/ubuntu intrepid main echo deb http://ppa.launchpad.net/reacocard-awn/ubuntu intrepid main

```

---

### Post by Partyboi2 on 2009-04-24
You need to fix up your sources.list file. Open a terminal and type
```
gksu gedit /etc/apt/sources.list
```then remove the the 5 lines  I have marked in red. Then add the 2 lines I have marked in blue, then save and close gedit, then run ```
sudo apt-get update
```
```

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse
[COLOR=Red][B]deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) intrepid main echo deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) intrepid main
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) intrepid main
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) intrepid main echo deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) intrepid main[/B][/COLOR]
[B][COLOR=Blue]deb [http://ppa.launchpad.net/reacocard-awn/ppa/ubuntu](http://ppa.launchpad.net/reacocard-awn/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/reacocard-awn/ppa/ubuntu](http://ppa.launchpad.net/reacocard-awn/ppa/ubuntu) intrepid main[/COLOR][/B]
```

---

### Post by KEE on 2009-04-25
it worked =) thanks Partyboi2

---

