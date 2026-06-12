---
title: "Authentication Issues"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by MT01Neo on 2009-02-05
I'm new to Linux and I'm using an Acer Aspire, running Ubuntu.
My machine is configured to look for system updates etc and informs me that there are 88 available, but when I go to install I am warned that they could not be authenticated and therefore advised not to install.
How can I tell the good from bad or only get authenticated upgrades.

Please advise.

Neo

---

### Post by taurus on 2009-02-05
Did you personally add some extra repos to your /etc/apt/sources.list (or /etc/apt/sources.list.d)?

Close the update manager.  Then, open a terminal and run this command.  Post the output here.

Applications -> Accessories -> Terminal
```
sudo apt-get update
```

---

### Post by MT01Neo on 2009-02-05
ok,
I've done that


Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_GB            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_GB          
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_GB                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release.gpg                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB               
Get: 1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                          
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_GB                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg                         
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Translation-en_GB         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Translation-en_GB         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security Release.gpg                 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/main Translation-en_GB      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/universe Translation-en_GB  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release.gpg                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Translation-en_GB                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/universe Translation-en_GB                  
Get: 2 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_GB                   
Get: 3 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_GB                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_GB      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Translation-en_GB                
Get: 4 [http://dl.google.com](http://dl.google.com) stable Release [1300B]                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Translation-en_GB 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Translation-en_GB       
Get: 5 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Get: 6 [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release [27.6kB]                         
Get: 7 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                      
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Get: 8 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                      
Ign [http://download.skype.com](http://download.skype.com) stable Release                                   
Ign [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_GB 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Translation-en_GB   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security Release                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://mentors.debian.net](http://mentors.debian.net) unstable Release.gpg                             
Hit [http://download.skype.com](http://download.skype.com) stable/non-free Packages                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/universe Packages                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Sources                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Sources                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Sources                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_GB              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_GB          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/main Packages               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/restricted Packages         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/main Sources                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                             
Get: 9 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [954B]                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/restricted Sources          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/universe Packages           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/universe Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/multiverse Packages         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/multiverse Sources          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Packages          
Ign [http://mentors.debian.net](http://mentors.debian.net) unstable Release                                 
Ign [http://mentors.debian.net](http://mentors.debian.net) unstable/main Sources                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/universe Packages                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Packages  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Get: 10 [http://mentors.debian.net](http://mentors.debian.net) unstable/main Sources [194kB]
Fetched 197kB in 4s (43.0kB/s)   
Reading package lists... Done
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7
W: You may want to run apt-get update to correct these problems

Neo

---

### Post by taurus on 2009-02-05
Nice!  You have feisty, gutsy, hardy, and intrepid repos all mix into one!  That's the best way to break your machine fast.

Which release are you running?

```
lsb_release -a
```
And why do you have others in your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by MT01Neo on 2009-02-05
I'm running intrepid 8.10

I've no idea why its got all those versions fiesty etc listed

Neo


No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid

## MAIN AND RESTRICTED REPOSITORIES
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security main restricted

## UNIVERSE REPOSITORY
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security universe

## MULTIVERSE REPOSITORY
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security multiverse

## CANONICAL REPOSITORY
## deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) intrepid partner

# Google software Repository
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
deb [http://ppa.launchpad.net/googlegadgets/ubuntu](http://ppa.launchpad.net/googlegadgets/ubuntu) hardy main
# ScreenLets Repository
deb [http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu) gutsy main universe
# wxDownload Repository
deb-src [http://mentors.debian.net/debian](http://mentors.debian.net/debian) unstable main
# Feisty Secuirty Repository
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main universe
# Skype Repository
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free



## CANONICAL REPOSITORY
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) intrepid partner

## MEDIBUNTU REPOSITORY
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) intrepid main
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe
deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) intrepid main

---

### Post by albinootje on 2009-02-05
> **MT01Neo said:**
> I'm running intrepid 8.10
-- cut --
# Feisty Secuirty Repository
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main universe

You should remove this (feisty) one, and make sure to add these :
```

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

```

For the rest, the PPA repositories didn't have gpg key signing for quite some time, not sure whether there's any right now.

---

