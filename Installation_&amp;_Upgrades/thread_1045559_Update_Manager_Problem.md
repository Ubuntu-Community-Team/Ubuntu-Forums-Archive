---
title: "Update Manager Problem"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by Dagonus on 2009-01-20
Ubuntu 8.10 64bit.

So I let Rhythmbox download codecs on its own. Last time I do that. 

After that Synaptic is giving me a problem 

> **Could not initialize the package information**

An unresolvable problem occured while initializing the package information.

Please report this bug against the 'update-manager' package and include the
following error message:

'E:Read error - read (5 Input/output error), E: The Package lists or status file could not be parsed or opened'

So, I tried > sudo apt-get update

and got 

>                                               
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.


Which in retrospect makes sense. 

Thoughts?

---

### Post by Dagonus on 2009-01-20
Ran > cat /etc/apt/sources.list

Output was

> #deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse


I could try opening up the CD, but I don't see why it would see the CD but not the other repositories.

---

### Post by Dagonus on 2009-01-21
Nope, that didn't do anything. 

Any ideas? Anyone?

---

### Post by 2hot6ft2 on 2009-01-21
you can try

```
sudo dpkg --configure -a
```

this will fix any packages if it stopped during the install.
then try ```
sudo apt-get update
```again

Somehow I don't think it will help though. I take it you've rebooted since then.

---

### Post by 2hot6ft2 on 2009-01-21
> you might try to run the following commands in a terminal:
```
sudo rm /var/cache/apt/*.bin
sudo apt-get update
```
or:
```
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
```from here [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/115087](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/115087)

---

### Post by Dagonus on 2009-01-21
```
sudo dpkg --configure -a

```

results in:

```
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2) intrepid/main Translation-en_US
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2) intrepid/restricted Translation-en_US
Hit http://us.archive.ubuntu.com intrepid Release.gpg                          
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US               
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US         
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US           
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US      
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg               
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US    
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Get:1 http://packages.medibuntu.org intrepid Release.gpg [197B]             
Ign http://packages.medibuntu.org intrepid/free Translation-en_US              
Hit http://us.archive.ubuntu.com intrepid Release                              
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_US          
Get:2 http://packages.medibuntu.org intrepid Release [11.7kB]                  
Ign http://packages.medibuntu.org intrepid Release                          
Hit http://us.archive.ubuntu.com intrepid-updates Release             
Hit http://security.ubuntu.com intrepid-security Release.gpg         
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US
Hit http://packages.medibuntu.org intrepid/free Packages
Hit http://us.archive.ubuntu.com intrepid/main Packages
Hit http://us.archive.ubuntu.com intrepid/restricted Packages
Hit http://us.archive.ubuntu.com intrepid/main Sources
Hit http://us.archive.ubuntu.com intrepid/restricted Sources
Hit http://us.archive.ubuntu.com intrepid/universe Packages
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com intrepid-security Release
Hit http://packages.medibuntu.org intrepid/non-free Packages        
Hit http://us.archive.ubuntu.com intrepid/universe Sources
Hit http://us.archive.ubuntu.com intrepid/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid-updates/main Packages
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Packages          
Hit http://us.archive.ubuntu.com intrepid-updates/main Sources                 
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Sources           
Hit http://us.archive.ubuntu.com intrepid-updates/universe Packages            
Hit http://security.ubuntu.com intrepid-security/main Packages                 
Hit http://us.archive.ubuntu.com intrepid-updates/universe Sources             
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Packages          
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Sources           
Hit http://security.ubuntu.com intrepid-security/restricted Packages           
Hit http://security.ubuntu.com intrepid-security/main Sources                  
Hit http://security.ubuntu.com intrepid-security/restricted Sources            
Hit http://security.ubuntu.com intrepid-security/universe Packages             
Hit http://security.ubuntu.com intrepid-security/universe Sources              
Hit http://security.ubuntu.com intrepid-security/multiverse Packages           
Hit http://security.ubuntu.com intrepid-security/multiverse Sources            
Fetched 198B in 1min22s (2B/s)                                                 
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
dagonus@Alien4:~$ sudo dpkg --configure -a
dpkg: failed in buffer_read(fd): copy info file `/var/lib/dpkg/available': Input/output error

```

Update then fails with the previous error.


From apt-get install -f: 

```
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
```


When it's reading the package lists, it seems to fly through to 85% then bog down which is followed by it finishing with the error.

---

