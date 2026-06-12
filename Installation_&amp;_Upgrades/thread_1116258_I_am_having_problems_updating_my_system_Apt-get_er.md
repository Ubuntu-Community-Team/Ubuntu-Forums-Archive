---
title: "I am having problems updating my system Apt-get errors"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by thrasher6900 on 2009-04-04
This is what's happens when I try to update.  I've not a clue as to what's wrong with it

I've tried 
```

sudo apt-get autoclean
```and then

```
sudo apt-get -f update
```and still no luck



```
nicholas@nicholas-laptop:~$ sudo apt-get -f update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US  
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid Release.gpg                      
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid/cairo-dock Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid Release.gpg                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid/security Translation-en_US             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid/main Translation-en_US                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid/restricted Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid/universe Translation-en_US             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid/multiverse Translation-en_US           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid Release                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources              
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid/cairo-dock Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Hit [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid/cairo-dock Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_US            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release.gpg                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Translation-en_US   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed Release.gpg                    
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg                               
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Translation-en_US                
Ign [http://download.skype.com](http://download.skype.com) stable Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US            
Hit [http://download.skype.com](http://download.skype.com) stable/non-free Packages                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US              
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release.gpg                       
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Translation-en_US            
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US          
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release                           
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                             
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Sources                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Sources                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/restricted Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/main Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/multiverse Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Sources 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/restricted Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Sources
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) intrepid Release.gpg  
  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) intrepid/free Translation-en_US
  Unable to connect to packages.freecontrib.org http:
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) intrepid/non-free Translation-en_US
  Unable to connect to packages.freecontrib.org http:
Reading package lists... Done
W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/intrepid/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/intrepid/Release.gpg)  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/intrepid/free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/intrepid/free/i18n/Translation-en_US.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/intrepid/non-free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/intrepid/non-free/i18n/Translation-en_US.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid/Release](http://security.ubuntu.com/ubuntu/dists/intrepid/Release)  Unable to find expected entry  security/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
```

---

### Post by zvacet on 2009-04-04
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by taurus on 2009-04-04
Looks to me like [http://packages.freecontrib.org/](http://packages.freecontrib.org/) is either down or dead.  So, edit /etc/apt/sources.list and place a # in front of that repo(s) to comment it/them out.

---

