---
title: "unable to install some softwares"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by kask1984 on 2009-03-07
hi every body 
when i am trying to install some softwares like octave ,scilab i am geeting the following error

"[I] Cannot install 'octave3.0'

This application conflicts with other installed software. To install 'octave3.0' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict."
[/I]
and i switched to synaptic and i tried to istall then i got this message

[I]"octave3.0:
 Depends: libblas3gf but it is not going to be installed or
	libblas.so.3gf or
 	libatlas3gf-base but it is not going to be installed
 Depends: libgfortran3 but it is not going to be installed
 Depends: liblapack3gf but it is not going to be installed or
	liblapack.so.3gf or
 	libatlas3gf-base but it is not going to be installed
 Depends: libsuitesparse-3.1.0 but it is not going to be installed
 Recommends: libatlas3gf-base but it is not going to be installed"[/I]


how to find conflicting softwares 

thanks a lot

---

### Post by taurus on 2009-03-07
Close synaptic.  Then, open a terminal and post the outputs of these two commands.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install octave3.0
```

---

### Post by kask1984 on 2009-03-07
after executing first command i got this 
[I]
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) intrepid Release.gpg
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) intrepid/main Translation-en_IN
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) intrepid/universe Translation-en_IN
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) intrepid/restricted Translation-en_IN
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) intrepid/multiverse Translation-en_IN
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) intrepid Release
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) intrepid/main Packages
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) intrepid/universe Packages
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) intrepid/multiverse Packages
Reading package lists... Done[/I]

and after second one

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  octave3.0: Depends: libblas3gf but it is not going to be installed or
                      libblas.so.3gf or
                      libatlas3gf-base but it is not going to be installed
             Depends: libgfortran3 (>= 4.3) but it is not going to be installed
             Depends: liblapack3gf but it is not going to be installed or
                      liblapack.so.3gf or
                      libatlas3gf-base but it is not going to be installed
             Depends: libsuitesparse-3.1.0 but it is not going to be installed
             Recommends: libatlas3gf-base but it is not going to be installed
E: Broken packages[/I]

---

### Post by taurus on 2009-03-07
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by kask1984 on 2009-03-07
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
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
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

# deb cdrom:[APTonCD for ubuntu intrepid - i386 (2009-03-03 09:54) CD1]/ /
# deb file:/var/cache/apt/archives ./



deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) intrepid main universe restricted multiverse
# deb cdrom:[APTonCD for ubuntu intrepid - i386 (2009-03-06 10:16) CD1]/ /

---

### Post by taurus on 2009-03-07
> **kask1984 said:**
> # deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
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
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

# deb cdrom:[APTonCD for ubuntu intrepid - i386 (2009-03-03 09:54) CD1]/ /
# deb file:/var/cache/apt/archives ./



**[COLOR="Blue"]deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) intrepid main universe restricted multiverse[/COLOR]**
# deb cdrom:[APTonCD for ubuntu intrepid - i386 (2009-03-06 10:16) CD1]/ /

That's all you have, one line?  Is your machine connected to the net?

---

### Post by kask1984 on 2009-03-07
yes but not fast

---

### Post by taurus on 2009-03-07
Yes to both questions?

Make a copy of your current /etc/apt/sources.list (even though it's useless).

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig
```
Then, edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and delete everything in there.  Now, post these new repos in there.

```

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted

deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

```
Save it and close down gedit window.  Now run

```
sudo apt-get update
sudo apt-get install octave3.0
```

---

### Post by kask1984 on 2009-03-08
after executing sudo apt-get update i got this

Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg [189B]         
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg [189B]        
Get:3 [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg [189B]                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_IN        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_IN                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_IN  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_IN            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_IN    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_IN              
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_IN            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_IN  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_IN            
Get:4 [http://archive.canonical.com](http://archive.canonical.com) intrepid Release [7007B]                    
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg                     
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_IN     
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_IN
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources   
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages        
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages  
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources         
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                     
  
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages            
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_IN      
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Translation-en_IN    
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release                                 
  
Err [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages                           
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources            
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages                     
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources              
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages           
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources                            
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources            
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Sources
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Fetched 567B in 1min10s (8B/s)            
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_IN.bz2)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_IN.bz2)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_IN.bz2)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_IN.bz2)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/Release](http://archive.ubuntu.com/ubuntu/dists/intrepid/Release)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release](http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/intrepid/Release](http://archive.canonical.com/ubuntu/dists/intrepid/Release)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/intrepid/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/intrepid/partner/binary-i386/Packages.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/intrepid/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/intrepid/partner/source/Sources.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


after executing sudo apt-get install octave3.0  i got this


Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package octave3.0

---

### Post by taurus on 2009-03-08
Do you have to set up some kind of proxy to get into the net?

---

### Post by kask1984 on 2009-03-08
yes i am behind proxy

---

### Post by taurus on 2009-03-08
Then you need to go into System -> Administration -> Synaptic Package Manager -> Settings -> Preferences -> Network and configure your proxy.

---

### Post by kask1984 on 2009-03-08
after cofiguring setting i did sudo apt-get updte i got this

[sudo] password for shiva: 
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg [189B]         
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                   
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg [189B]          
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_IN            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_IN        
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_IN            
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_IN    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_IN
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_IN  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_IN
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Translation-en_IN
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release [65.9kB]        
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release [51.2kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release [51.2kB]              
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages [1256kB]                
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages [83.9kB]      
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages [3491B] 
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources [24.0kB]      
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources [1154B] 
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages [30.0kB] 
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources [5746B]   
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages [6406B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources [1860B] 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Sources                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Sources                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Sources              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Sources                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Packages             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Sources              
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages                           
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages                     
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources                            
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources                      
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages                       
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources                        
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages                     
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Sources                      
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages                   
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages             
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Sources                    
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Sources              
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages               
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Sources                
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Packages             
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Sources              
  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)
Fetched 279kB in 4min49s (966B/s)                                              
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz)  Could not connect to 10.10.30.2:3128 (10.10.30.2). - connect (111 Connection refused)

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

