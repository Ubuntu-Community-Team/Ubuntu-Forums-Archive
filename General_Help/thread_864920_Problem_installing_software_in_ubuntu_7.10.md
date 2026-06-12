---
title: "Problem installing software in ubuntu 7.10"
date: 2008-07-20
forum: General Help
---

### Post by lieja on 2008-07-20
im using ubuntu 7.10 i386 release on my AMDTurion64 laptop..im not sure if something goin wrong between the software and hardware but right now i cannot install any software in my system. thru sypnatic ..i got the message "the repo might not be longer available.could not be contact because of network problem". could anybody tell me what's the problem n how to fix it..thanks in advance

---

### Post by p_quarles on 2008-07-20
Could you post the output of this?:
```
cat /etc/apt/sources.list
```

---

### Post by lieja on 2008-07-23
thanks for ur reply:)
here's the source.list file

deb [http://fr.archieve.ubuntu.com/ubuntu](http://fr.archieve.ubuntu.com/ubuntu) gutsy main universe
deb-src [http://fr.archieve.ubuntu.com/ubuntu](http://fr.archieve.ubuntu.com/ubuntu) gutsy main universe
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://packages.medibuntu.org/gutsy](http://packages.medibuntu.org/gutsy) free nonfree

---

### Post by lieja on 2008-07-26
no reply?? hello...can anyone fix my prob here?

---

### Post by ProbablyX on 2008-07-26
What happens when you run

```

sudo aptitude update

```

---

### Post by lieja on 2008-07-26
this what i got

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US                      
Get:2 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy-backports Release.gpg [189B]           
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy-backports/main Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US                
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [189B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US        
Get:4 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                     
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US                
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy-backports/restricted Translation-en_US   
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy-backports/universe Translation-en_US     
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                             
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy-backports Release                        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) free Release.gpg                              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) free/nonfree Translation-en_US                
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                         
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy-backports/main Packages                  
Err [http://fr.archieve.ubuntu.com](http://fr.archieve.ubuntu.com) gutsy Release.gpg                             
  Could not resolve 'fr.archieve.ubuntu.com'
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) free Release                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages                 
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy-backports/restricted Packages            
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy-backports/universe Packages              
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy-backports/multiverse Packages            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) free/nonfree Packages                         
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                          
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) free/nonfree Packages         
  404 Not Found [IP: 87.98.249.30 80]
Err [http://fr.archieve.ubuntu.com](http://fr.archieve.ubuntu.com) gutsy/main Translation-en_US                  
  Could not resolve 'fr.archieve.ubuntu.com'
Err [http://fr.archieve.ubuntu.com](http://fr.archieve.ubuntu.com) gutsy/universe Translation-en_US              
  Could not resolve 'fr.archieve.ubuntu.com'
Ign [http://fr.archieve.ubuntu.com](http://fr.archieve.ubuntu.com) gutsy Release
Ign [http://fr.archieve.ubuntu.com](http://fr.archieve.ubuntu.com) gutsy/main Packages
Ign [http://fr.archieve.ubuntu.com](http://fr.archieve.ubuntu.com) gutsy/universe Packages
Ign [http://fr.archieve.ubuntu.com](http://fr.archieve.ubuntu.com) gutsy/main Sources
Ign [http://fr.archieve.ubuntu.com](http://fr.archieve.ubuntu.com) gutsy/universe Sources
Err [http://fr.archieve.ubuntu.com](http://fr.archieve.ubuntu.com) gutsy/main Packages
  Could not resolve 'fr.archieve.ubuntu.com'
Err [http://fr.archieve.ubuntu.com](http://fr.archieve.ubuntu.com) gutsy/universe Packages
  Could not resolve 'fr.archieve.ubuntu.com'
Err [http://fr.archieve.ubuntu.com](http://fr.archieve.ubuntu.com) gutsy/main Sources
  Could not resolve 'fr.archieve.ubuntu.com'
Err [http://fr.archieve.ubuntu.com](http://fr.archieve.ubuntu.com) gutsy/universe Sources
  Could not resolve 'fr.archieve.ubuntu.com'
Fetched 4B in 59s (0B/s)                  
Reading package lists... Done

---

### Post by ProbablyX on 2008-07-26
And have you tried
```

sudo aptitude upgrade

```

or just Synaptic?

---

### Post by ProbablyX on 2008-07-26
OK I think Ive found your error, you have sources that doesnt exist.

Move your /etc/apt/sources.list file to a backup place.

Then put this in that file:
> 
deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) gutsy main universe
deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) gutsy main universe
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# deb [http://packages.medibuntu.org/gutsy](http://packages.medibuntu.org/gutsy) free nonfree


Ive now moved your system to update from Sweden instead as France doesnt seem to work. Ive also removed the medubuntu repo as it doesnt work.

Now try to update.
```

sudo aptitude update
sudo aptutude upgrade

```

---

### Post by ProbablyX on 2008-07-26
I just noticed you had written "archieve.ubuntu.com" it should say "archive" I have updated my post above and corrected the error.

---

### Post by lieja on 2008-07-26
thanks..i'll try that n report to u soon:)

---

### Post by lieja on 2008-07-27
thanks probablyx..it's really fix the problem..but during upgraded,i've limited disk space prob..do u know how to deal with it..when updating using sypnatic..it mentioned to use sudo apt-get clean command but still doesnt do nothing.should i resize the partition so i'll get more space?

---

