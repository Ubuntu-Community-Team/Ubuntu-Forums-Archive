---
title: "apt-get will not install ANYTHING"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Rex Regis on 2009-04-25
Ok, I'm really having trouble with installing stuff with apt-get.  I am pretty new to Linux.  I installed Ubuntu before and it worked fine, but I had a problem with my hard drive and have had to re-install.  I am running intrepid, as before, but now it refuses to install anything! No matter what I put in I get the same answer:

```
~$ sudo apt-get install compiz config-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
E: Couldn't find package config-settings-manager
```

And as I said, this happens no matter what program I try to download, except for the *compiz is already the newest version.* part.  Does anyone have any thoughts?

---

### Post by barney385 on 2009-04-25
sudo apt-get clean

then try it again...

---

### Post by ubuntunewb75 on 2009-04-25
Spank the computer and tell it it's been very naughty and if it doesn't shape up you're going to leave it for a nice new shiny Dell with Ubuntu pre-installed.  that'll larn it.

---

### Post by Viranh on 2009-04-25
Perhaps check your internet connection and run "sudo apt-get update." I seem to remember having this problem right after installation.

---

### Post by oldos2er on 2009-04-25
> **Rex Regis said:**
> Ok, I'm really having trouble with installing stuff with apt-get.  I am pretty new to Linux.  I installed Ubuntu before and it worked fine, but I had a problem with my hard drive and have had to re-install.  I am running intrepid, as before, but now it refuses to install anything! No matter what I put in I get the same answer:

```
~$ sudo apt-get install compiz config-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
E: Couldn't find package config-settings-manager
```And as I said, this happens no matter what program I try to download, except for the *compiz is already the newest version.* part.  Does anyone have any thoughts?

 The correct package name is compizconfig-settings-manager.

---

### Post by Rex Regis on 2009-04-25
Thanks for all your help, but nothing so far just the same thing.  Yes I see that the package name was wrong, but it doesn't change anything since even with the correct name I get the same result.

sudo apt-get clean didn't change anything.

My internet is fine, since I am using it now to write this message.

---

### Post by tommcd on 2009-04-25
Did you run:
```
sudo apt-get update
```
before trying to install packages?
Are all of your repositories enabled?
Post your /etc/apt/sources.list

---

### Post by Rex Regis on 2009-04-25
I have run the update.  This is what it returns:

```
Hit http://archive.canonical.com intrepid Release.gpg
Get:1 http://packages.medibuntu.org intrepid Release.gpg [197B]                
Ign http://archive.canonical.com intrepid/partner Translation-en_US            
Hit http://archive.canonical.com intrepid Release                              
Ign http://packages.medibuntu.org intrepid/free Translation-en_US  
Ign http://mirror.imbrandon.com intrepid Release.gpg               
Ign http://archive.canonical.com intrepid/partner Packages                     
Ign http://mirror.imbrandon.com intrepid/main Translation-en_US                
Ign http://archive.canonical.com intrepid/partner Sources                      
Hit http://archive.canonical.com intrepid/partner Packages                     
Hit http://archive.canonical.com intrepid/partner Sources
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_US
Get:2 http://packages.medibuntu.org intrepid Release [11.7kB]
Ign http://packages.medibuntu.org intrepid Release    
Ign http://mirror.imbrandon.com intrepid/restricted Translation-en_US
Hit http://packages.medibuntu.org intrepid/free Packages
Hit http://packages.medibuntu.org intrepid/non-free Packages
Ign http://mirror.imbrandon.com intrepid/universe Translation-en_US
Ign http://mirror.imbrandon.com intrepid/multiverse Translation-en_US
Ign http://mirror.imbrandon.com intrepid-updates Release.gpg
Ign http://mirror.imbrandon.com intrepid-updates/main Translation-en_US
Ign http://mirror.imbrandon.com intrepid-updates/restricted Translation-en_US
Ign http://mirror.imbrandon.com intrepid-updates/universe Translation-en_US
Ign http://mirror.imbrandon.com intrepid-updates/multiverse Translation-en_US
Ign http://mirror.imbrandon.com intrepid Release
Ign http://mirror.imbrandon.com intrepid-updates Release
Ign http://mirror.imbrandon.com intrepid/main Packages
Ign http://mirror.imbrandon.com intrepid/restricted Packages
Ign http://mirror.imbrandon.com intrepid/main Sources
Ign http://mirror.imbrandon.com intrepid/restricted Sources
Ign http://mirror.imbrandon.com intrepid/universe Packages
Ign http://mirror.imbrandon.com intrepid/universe Sources
Ign http://mirror.imbrandon.com intrepid/multiverse Packages
Ign http://mirror.imbrandon.com intrepid/multiverse Sources
Ign http://mirror.imbrandon.com intrepid-updates/main Packages
Ign http://mirror.imbrandon.com intrepid-updates/restricted Packages
Ign http://mirror.imbrandon.com intrepid-updates/main Sources
Ign http://mirror.imbrandon.com intrepid-updates/restricted Sources
Ign http://mirror.imbrandon.com intrepid-updates/universe Packages
Ign http://mirror.imbrandon.com intrepid-updates/universe Sources
Ign http://mirror.imbrandon.com intrepid-updates/multiverse Packages
Ign http://mirror.imbrandon.com intrepid-updates/multiverse Sources            
Err http://mirror.imbrandon.com intrepid/main Packages                         
  302 Moved Temporarily
Err http://mirror.imbrandon.com intrepid/restricted Packages                   
  302 Moved Temporarily
Err http://mirror.imbrandon.com intrepid/main Sources                          
  302 Moved Temporarily
Err http://mirror.imbrandon.com intrepid/restricted Sources                    
  302 Moved Temporarily
Err http://mirror.imbrandon.com intrepid/universe Packages                     
  302 Moved Temporarily
Err http://mirror.imbrandon.com intrepid/universe Sources                      
  302 Moved Temporarily
Err http://mirror.imbrandon.com intrepid/multiverse Packages                   
  302 Moved Temporarily
Err http://mirror.imbrandon.com intrepid/multiverse Sources                    
  302 Moved Temporarily
Err http://mirror.imbrandon.com intrepid-updates/main Packages                 
  302 Moved Temporarily
Err http://mirror.imbrandon.com intrepid-updates/restricted Packages           
  302 Moved Temporarily
Err http://mirror.imbrandon.com intrepid-updates/main Sources                  
  302 Moved Temporarily
Err http://mirror.imbrandon.com intrepid-updates/restricted Sources            
  302 Moved Temporarily
Err http://mirror.imbrandon.com intrepid-updates/universe Packages             
  302 Moved Temporarily
Err http://mirror.imbrandon.com intrepid-updates/universe Sources              
  302 Moved Temporarily
Err http://mirror.imbrandon.com intrepid-updates/multiverse Packages           
  302 Moved Temporarily
Err http://mirror.imbrandon.com intrepid-updates/multiverse Sources            
  302 Moved Temporarily
Fetched 198B in 9s (21B/s)                                                     
W: GPG error: http://packages.medibuntu.org intrepid Release: The following signatures were invalid: NODATA 2
W: Failed to fetch http://mirror.imbrandon.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://mirror.imbrandon.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://mirror.imbrandon.com/ubuntu/dists/intrepid/main/source/Sources.gz  302 Moved Temporarily

W: Failed to fetch http://mirror.imbrandon.com/ubuntu/dists/intrepid/restricted/source/Sources.gz  302 Moved Temporarily

W: Failed to fetch http://mirror.imbrandon.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://mirror.imbrandon.com/ubuntu/dists/intrepid/universe/source/Sources.gz  302 Moved Temporarily

W: Failed to fetch http://mirror.imbrandon.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://mirror.imbrandon.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz  302 Moved Temporarily

W: Failed to fetch http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz  302 Moved Temporarily

W: Failed to fetch http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz  302 Moved Temporarily

W: Failed to fetch http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz  302 Moved Temporarily

W: Failed to fetch http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz  302 Moved Temporarily

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

as far as I know I have the repositories enabled.

This is my sources list:

```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.imbrandon.com/ubuntu/ intrepid main restricted
deb-src http://mirror.imbrandon.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.imbrandon.com/ubuntu/ intrepid-updates main restricted
deb-src http://mirror.imbrandon.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.imbrandon.com/ubuntu/ intrepid universe
deb-src http://mirror.imbrandon.com/ubuntu/ intrepid universe
deb http://mirror.imbrandon.com/ubuntu/ intrepid-updates universe
deb-src http://mirror.imbrandon.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.imbrandon.com/ubuntu/ intrepid multiverse
deb-src http://mirror.imbrandon.com/ubuntu/ intrepid multiverse
deb http://mirror.imbrandon.com/ubuntu/ intrepid-updates multiverse
deb-src http://mirror.imbrandon.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://packages.medibuntu.org/ intrepid free non-free
```

---

### Post by cariboo on 2009-04-25
Why not try installing the package using Add/Remove Programs or Synaptic Package Manager?

---

### Post by Partyboi2 on 2009-04-25
The problem looks like it is caused by [FONT=monospace]the mirror you are using in you sources.list [/FONT]"http://mirror.imbrandon.com"

---

### Post by Rex Regis on 2009-04-25
For add/remove programs, when I check something to be installed, it starts running through the process of downloading packages, and then gives the following error:

> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures were invalid: NODATA 2Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid/main/source/Sources.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid/restricted/source/Sources.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid/universe/source/Sources.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid/universe/source/Sources.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz)  302 Moved Temporarily
Some index files failed to download, they have been ignored, or old ones used instead.

Then on clicking close, this error is displayed:

> Amarok cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type. 


The package manager works so long as the program I want is in the list (which for most of them it is not).  When I change the server in software sources, or just reload the package manager, it runs throught the process of downloading as above, and then gives this error (which I assume is also the same as above):

> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures were invalid: NODATA 2Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid/main/source/Sources.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid/restricted/source/Sources.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid/universe/source/Sources.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid/universe/source/Sources.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://mirror.imbrandon.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz)  302 Moved Temporarily
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by alphacrucis2 on 2009-04-25
As another poster said. Try changing the mirrors you are using.

---

### Post by Rex Regis on 2009-04-25
Sorry to be very n00by, but I assume that means shnging the Download From selection in the Software sources?  I have set it to Server for United States.  On refreshing I get the following:

> An error occurred

The following details are provided:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures were invalid: NODATA 2
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release: The following signatures were invalid: NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release: The following signatures were invalid: NODATA 2

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

The same error is shown when trying to reload the package manager.

---

### Post by tommcd on 2009-04-26
You are running Intrepid 8.10? Is that correct?
I just want to be sure. If you are running Intrepid, first backup your sources.list:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```
Then run **gksudo gedit /etc/apt/sources.list** and replace the contents of your sources.list with this:
```

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

#universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

#multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

#the partner repos that you had in your sources.list
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

```
See this for reference:
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
Then run: ```

sudo apt-get update

``` 
If it returns without errors, then run:
```
apt-cache policy compizconfig-settings-manager
```
The output should tell you whether compizconfig-settings-manager is installed or not, and what the candidate version for installation is. For Intrepid it is currently version 0.78:
[http://packages.ubuntu.com/search?keywords=compizconfig-settings-manager&searchon=names&suite=intrepid&section=all](http://packages.ubuntu.com/search?keywords=compizconfig-settings-manager&searchon=names&suite=intrepid&section=all)
If you get that then try to install it.
If this does not work you can always replace your new sources.list with the old one you backed up.

---

### Post by Rex Regis on 2009-04-26
Thanks for all that, but still nothing.  the apt-get update returned:

```
Get:1 http://us.archive.ubuntu.com intrepid Release.gpg [189B]
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US              
Hit http://archive.canonical.com intrepid Release.gpg                         
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US         
Ign http://archive.canonical.com intrepid/partner Translation-en_US            
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US
Hit http://archive.canonical.com intrepid Release
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US
Get:2 http://us.archive.ubuntu.com intrepid-updates Release.gpg [189B]        
Ign http://archive.canonical.com intrepid/partner Packages                    
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US      
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://archive.canonical.com intrepid/partner Sources                     
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US  
Hit http://archive.canonical.com intrepid/partner Packages                    
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://archive.canonical.com intrepid/partner Sources                     
Get:3 http://us.archive.ubuntu.com intrepid Release [65.9kB]                  
Err http://us.archive.ubuntu.com intrepid Release
  
Get:4 http://us.archive.ubuntu.com intrepid-updates Release [51.2kB]
Err http://us.archive.ubuntu.com intrepid-updates Release
  
Fetched 383B in 2s (177B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://us.archive.ubuntu.com intrepid Release: The following signatures were invalid: NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://us.archive.ubuntu.com intrepid-updates Release: The following signatures were invalid: NODATA 2

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
```

It doesn't look very good for me!:(  I can't think what's wrong with it?

---

### Post by Rex Regis on 2009-04-26
I was able to install Compizconfig-settings-manager by downloading the .deb package from the internet and then just installing it (and its dependecies) from the dektop, so that is working now.

---

### Post by Rex Regis on 2009-04-26
sorry for any confusion.  I mean that Compiz is working fine, but apt-get installs and updates etc are still not working

---

### Post by tommcd on 2009-04-26
It seems that APT is balking at the verification of your sources.list. This should not happen with the standard Ubuntu repos.
Try this:
1. Back up your sources.list again:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak2
```
Then run:
```
gksudo gedit /etc/apt/sources.list
```
and delete everything there, leaving the file empty. Don't delete the actual file, just leave it empty.
Then run: "sudo apt-get update". This will likely produce errors.
 Then open synaptic package manager and click on: settings > repositories. Put a check mark in front of all the repositories you want in each of the categories. Also, check the authentication tab. The authentication keys should be listed there. Then close the software repositories box and click reload on synaptic. This should rebuild your sources.list. Then see if you can install packages.

---

### Post by Rex Regis on 2009-04-26
WOOOOOOOOO!! so far so good!! Thanks so much! :guitar:  It seems to be working fine.  I will leave it till after a restart before I really party, but for the moment it's working.

---

### Post by tommcd on 2009-04-28
Well, I'm glad that worked!
That was the last card I had to play for this problem. 
Please backup your now working sources.list for safe keeping:
```
sudo cp /etc/apt/sorces.list /etc/apt/sources.list.good
```

After a fresh install of Ubuntu, I always backup these important files:
/boot/grub/menu.lst
/etc/fstab
/etc/apt/sources.list
/etc/X11/xorg.conf
I also backup *any* files that I edit for any reason before I edit them.

---

### Post by Rex Regis on 2009-04-28
Thanks so much for all your help.  Just one more thing I'm curious about.  How do you retrieve the back up?  I mean if I back up sources.list and then wreck it, how to I get the backup back in use?

---

### Post by tommcd on 2009-04-28
> **Rex Regis said:**
>   How do you retrieve the back up?  I mean if I back up sources.list and then wreck it, how to I get the backup back in use?
You just reverse the order of the files in the **cp** command. For example, to backup the file you might do:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```
Then suppose you edit the file that is in use, and you inadvertently mangle it beyond repair, and need to restore the original from the backup. Just do this:
```
sudo cp /etc/apt/sources.list.bak /etc/apt/sources.list
```
and the file is restored from the .bak file. For extra safety, to be sure you don't accidentally overwrite the wrong file, you can run the command with the "-i" switch like this:
```
sudo cp -i /etc/apt/sources.list.bak /etc/apt/sources.list
```
The -i is for interactive. Since /etc/apt/sources.list already exists, it will ask you to confirm the overwrite. Just answer "y" for yes.

---

### Post by networm1230 on 2009-04-28
do (sudo apt get) ?< name of apt

---

### Post by Rex Regis on 2009-04-28
Thanks tommcd, you've really been a lot of help.  This forum is great!!:P

---

