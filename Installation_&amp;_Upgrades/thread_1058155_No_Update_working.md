---
title: "No Update working"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by lupas on 2009-02-02
Recently i encounter with the problem that when i do the update for the rep. some errors happens. Update failed to download. Check your internet connection or the rep are no longer supported. 
Can someone explain to me why? I'm using Ubuntu8.04 and 8.10, both the same problem

---

### Post by taurus on 2009-02-02
What is the whole output when you run this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
```
Make sure you have closed down update manager first before you run that command.

---

### Post by lupas on 2009-02-03
> **taurus said:**
> What is the whole output when you run this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
```
Make sure you have closed down update manager first before you run that command.


I did that too but same result. here is what it gave me with the terminal 

[IMG]http://img155.imageshack.us/img155/4255/61970195cw3.png[/IMG]

Any help ????

---

### Post by lupas on 2009-02-03
Pls can someone help me about this? I've been a Ubuntu user for almost a year by now.:)

---

### Post by taurus on 2009-02-03
I don't see any problem from your screenshot of sudo apt-get update!  Now run

```
sudo apt-get upgrade
```

---

### Post by ambidextrousone on 2009-02-03
this is what im getting.

Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_GB        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Translation-en_GB         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Translation-en_GB         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release.gpg                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Translation-en_GB       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Translation-en_GB 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Translation-en_GB   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_GB 
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release.gpg                       
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_GB  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_GB  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_GB              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_GB          
Hit [http://rowdy.dfreer.org](http://rowdy.dfreer.org) hardy Release.gpg                                  
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages                     
Ign [http://rowdy.dfreer.org](http://rowdy.dfreer.org) hardy/main Translation-en_GB                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Packages                  
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Sources                         
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                       
Hit [http://rowdy.dfreer.org](http://rowdy.dfreer.org) hardy Release                                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages                   
Hit [http://rowdy.dfreer.org](http://rowdy.dfreer.org) hardy/main Packages                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Sources         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Packages
Ign [http://packages.dfreer.org](http://packages.dfreer.org) gutsy Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Sources
Ign [http://packages.dfreer.org](http://packages.dfreer.org) gutsy/main Translation-en_GB                    
Ign [http://packages.dfreer.org](http://packages.dfreer.org) gutsy Release                                   
Ign [http://packages.dfreer.org](http://packages.dfreer.org) gutsy/main Packages
Ign mirror://www.getdeb.net intrepid/ Release.gpg
Err [http://packages.dfreer.org](http://packages.dfreer.org) gutsy/main Packages
  302 Found
Ign mirror://www.getdeb.net intrepid/ Translation-en_GB
Ign mirror://www.getdeb.net intrepid/ Release         
Hit mirror://www.getdeb.net intrepid/ Packages
W: Failed to fetch [http://packages.dfreer.org/dists/gutsy/main/binary-amd64/Packages.gz](http://packages.dfreer.org/dists/gutsy/main/binary-amd64/Packages.gz)  302 Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

do i need to be concerned? :P

---

### Post by taurus on 2009-02-03
> **ambidextrousone said:**
> this is what im getting.

Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_GB        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Translation-en_GB         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Translation-en_GB         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release.gpg                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Translation-en_GB       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Translation-en_GB 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Translation-en_GB   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_GB 
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release.gpg                       
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_GB  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_GB  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_GB              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_GB          
Hit [http://rowdy.dfreer.org](http://rowdy.dfreer.org) hardy Release.gpg                                  
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages                     
Ign [http://rowdy.dfreer.org](http://rowdy.dfreer.org) hardy/main Translation-en_GB                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Packages                  
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Sources                         
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                       
Hit [http://rowdy.dfreer.org](http://rowdy.dfreer.org) hardy Release                                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages                   
Hit [http://rowdy.dfreer.org](http://rowdy.dfreer.org) hardy/main Packages                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Sources         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Packages
Ign [http://packages.dfreer.org](http://packages.dfreer.org) gutsy Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Sources
Ign [http://packages.dfreer.org](http://packages.dfreer.org) gutsy/main Translation-en_GB                    
Ign [http://packages.dfreer.org](http://packages.dfreer.org) gutsy Release                                   
Ign [http://packages.dfreer.org](http://packages.dfreer.org) gutsy/main Packages
Ign mirror://www.getdeb.net intrepid/ Release.gpg
Err [http://packages.dfreer.org](http://packages.dfreer.org) gutsy/main Packages
  302 Found
Ign mirror://www.getdeb.net intrepid/ Translation-en_GB
Ign mirror://www.getdeb.net intrepid/ Release         
Hit mirror://www.getdeb.net intrepid/ Packages
W: Failed to fetch [http://packages.dfreer.org/dists/gutsy/main/binary-amd64/Packages.gz](http://packages.dfreer.org/dists/gutsy/main/binary-amd64/Packages.gz)  302 Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

do i need to be concerned? :P

Yes.  You definitely need to be concerned because you have some hardy and gutsy repos mixing in with your intrepid!  

Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by ambidextrousone on 2009-02-03
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

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
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"
deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main
deb [http://rowdy.dfreer.org:8080](http://rowdy.dfreer.org:8080) hardy main

im almost impressed that ive managed to break ubuntu, lol! thank for for taking a look at this for me btw taurus

---

### Post by taurus on 2009-02-03
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and either remove the last two entries or place a # in front of them to comment them out.

```

**[COLOR="Blue"]#[/COLOR]**deb http://packages.dfreer.org gutsy main
**[COLOR="Blue"]#[/COLOR]**deb http://rowdy.dfreer.org:8080 hardy main

```
Save it and close down gedit window.  Now run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ambidextrousone on 2009-02-03
followed your instructions, heres the new one!

Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release.gpg                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_GB  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Translation-en_GB         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Translation-en_GB 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release.gpg        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_GB
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release.gpg                       
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release                              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_GB          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages       
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release                           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Sources                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources            
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Packages      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages
Ign mirror://www.getdeb.net intrepid/ Release.gpg    
Ign mirror://www.getdeb.net intrepid/ Translation-en_GB
Ign mirror://www.getdeb.net intrepid/ Release
Get: 1 mirror://www.getdeb.net intrepid/ Packages [2748B]
Fetched 2748B in 3s (823B/s)    
Reading package lists... Done
W: Duplicate sources.list entry [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages (/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_intrepid_main_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems


i use run apt-get update ... 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

all set? :)

---

### Post by taurus on 2009-02-03
What's the output of this command from a terminal?

```
ls -la /etc/apt/sources.list.d
```

---

### Post by ambidextrousone on 2009-02-03
total 24
drwxr-xr-x 2 root root 4096 2008-12-22 03:15 .
drwxr-xr-x 4 root root 4096 2009-02-03 16:14 ..
-rw-r--r-- 1 root root  230 2008-08-18 21:13 medibuntu.list
-rw-r--r-- 1 root root   62 2008-12-22 03:15 playdeb.list
-rw-r--r-- 1 root root  189 2008-12-12 01:49 winehq.list
-rw-r--r-- 1 root root  191 2008-12-12 01:49 winehq.list.save

---

### Post by taurus on 2009-02-03
> **ambidextrousone said:**
> total 24
drwxr-xr-x 2 root root 4096 2008-12-22 03:15 .
drwxr-xr-x 4 root root 4096 2009-02-03 16:14 ..
-rw-r--r-- 1 root root  230 2008-08-18 21:13 medibuntu.list
-rw-r--r-- 1 root root   62 2008-12-22 03:15 playdeb.list
**-rw-r--r-- 1 root root  189 2008-12-12 01:49 winehq.list**
-rw-r--r-- 1 root root  191 2008-12-12 01:49 winehq.list.save

You already have a repo for wine in /etc/apt/sources.list.d so it's safe to remove the entry for wine in /etc/apt/sources.list.

Edit /etc/apt/sources.list again and remove this line from it.

```

deb http://wine.budgetdedicated.com/apt intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"

```
Save it and run these two commands again.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ambidextrousone on 2009-02-03
Nothing is coming up to suggest an issue, all packages appear to be in order now :) thank you taurus!!! is there anything i need to bare in mind to stop this happening again?

---

### Post by lupas on 2009-02-03
I'm a bit confuse by now. Regards the first post that i made, is there something wrong? During these 5 days i can't get any updates .

---

### Post by ambidextrousone on 2009-02-03
sorry lupas, i hijacked your thread, you might well be having the same problem as me.

ambi out!

---

### Post by taurus on 2009-02-03
> **ambidextrousone said:**
> Nothing is coming up to suggest an issue, all packages appear to be in order now :) thank you taurus!!! is there anything i need to bare in mind to stop this happening again?

Only add repos for intrepid (not hardy or gutsy).  And you don't have to do it twice, adding one in /etc/apt/sources.list and another in /etc/apt/sources.list.d.  Otherwise, you should be all good to go with the current repos.

---

### Post by taurus on 2009-02-03
> **lupas said:**
> I'm a bit confuse by now. Regards the first post that i made, is there something wrong? During these 5 days i can't get any updates .

Have you tried running these from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by lupas on 2009-02-03
These are the last lines i get from the terminal 

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/restricted Packages
Fetched 189B in 2s (80B/s)
Reading package lists... Done
jonathan@jonathan-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jonathan@jonathan-desktop:~$ 


Is this ok or not ?

---

### Post by taurus on 2009-02-03
> **lupas said:**
> These are the last lines i get from the terminal 

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/restricted Packages
Fetched 189B in 2s (80B/s)
Reading package lists... Done
jonathan@jonathan-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jonathan@jonathan-desktop:~$ 

Is this ok or not ?

What kernel version are you running?

```
uname -a
```
Also, post your /etc/apt/sources.list if you wish.

```
cat /etc/apt/sources.list
```

---

### Post by lupas on 2009-02-03
Linux jonathan-desktop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

---

### Post by lupas on 2009-02-03
Linux jonathan-desktop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux
jonathan@jonathan-desktop:~$ cat/etc/apt/sources.list
bash: cat/etc/apt/sources.list: No such file or directory
jonathan@jonathan-desktop:~$ cat/etc/apt/sources.list
bash: cat/etc/apt/sources.list: No such file or directory
jonathan@jonathan-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security restricted main multiverse universe #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security multiverse
jonathan@jonathan-desktop:~$

---

### Post by taurus on 2009-02-03
Looks like you are running the latest kernel which means your system is probably up-today.

---

### Post by lupas on 2009-02-03
Well, since it is the first time since that i don't have any updates i began to worry :) 

What are these who are not supported by Ubuntu team ?


Anyway, thanks for your patience !

---

