---
title: "update manger error ??"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by NawafLol on 2009-09-27
when i run my update manger i got this :

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/sa.archive.ubuntu.com_ubuntu_dists_jaunty_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

it happans to my Add/remove manger and anything else got to to do with ubuntu date base i think !


i tried sudo apt-get update and it tells me :

Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US    
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty Release.gpg                            
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty/main Translation-en_US                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty/universe Translation-en_US             
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty/multiverse Translation-en_US           
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates Release.gpg                    
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates/universe Translation-en_US     
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US   
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release.gpg                         
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Translation-en_US              
Hit [http://repository.cairo-dock.org](http://repository.cairo-dock.org) jaunty Release.gpg                        
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) jaunty/cairo-dock Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty Release                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates Release                        
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty/restricted Packages                    
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty/main Sources                           
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty/restricted Sources                     
Hit [http://repository.cairo-dock.org](http://repository.cairo-dock.org) jaunty Release                            
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) jaunty/ Release.gpg                                  
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                       
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) jaunty/ Translation-en_US                            
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty/universe Packages                      
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty/universe Sources                       
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty/multiverse Packages                    
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty/multiverse Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources              
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates/main Packages                  
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates/restricted Packages            
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates/main Sources                   
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates/restricted Sources             
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates/universe Packages              
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates/universe Sources               
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates/multiverse Packages            
Hit [http://repository.cairo-dock.org](http://repository.cairo-dock.org) jaunty/cairo-dock Packages                
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                       
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates/multiverse Sources   
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) jaunty/ Release      
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) jaunty/ Packages
Hit [http://ftp.osuosl.org](http://ftp.osuosl.org) jaunty/ Packages
Reading package lists... Error! 
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/sa.archive.ubuntu.com_ubuntu_dists_jaunty_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.



 and with the sudo apt-get install -f : 

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/sa.archive.ubuntu.com_ubuntu_dists_jaunty_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

HELP ME !

---

### Post by Partyboi2 on 2009-09-27
Hi, open a terminal and remove the file with
```
sudo rm  /var/lib/apt/lists/sa.archive.ubuntu.com_ubuntu_dists_jaunty_restrict  ed_binary-i386_Packages
```
then download it again with
```
suso apt-get update
```

---

### Post by NawafLol on 2009-09-27
couldn't it says :

rm: cannot remove `/var/lib/apt/lists/sa.archive.ubuntu.com_ubuntu_dists_jaunty_restrict': No such file or directory
rm: cannot remove `ed_binary-i386_Packages': No such file or directory

---

### Post by nathan726 on 2009-09-27
He meant this:

```
sudo rm /var/lib/apt/lists/sa.archive.ubuntu.com_ubuntu_dists_jaunty_restricted_binary-i386_Packages

sudo apt-get update
```

---

### Post by NawafLol on 2009-09-27
still no go :

it [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US    
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release.gpg                         
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Translation-en_US              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) jaunty/ Release.gpg                                  
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) jaunty/ Translation-en_US                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release                             
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty Release.gpg                            
Hit [http://repository.cairo-dock.org](http://repository.cairo-dock.org) jaunty Release.gpg                        
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty/main Translation-en_US                 
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) jaunty/cairo-dock Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty/universe Translation-en_US             
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty/multiverse Translation-en_US           
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) jaunty/ Release                                      
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates Release.gpg                    
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates/main Translation-en_US         
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US   
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates/universe Translation-en_US     
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US   
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                       
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty Release                                
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources              
Hit [http://repository.cairo-dock.org](http://repository.cairo-dock.org) jaunty Release                            
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) jaunty/ Packages                                     
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages             
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty/main Packages                
Get:1 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty/restricted Packages [8848B]
Hit [http://ftp.osuosl.org](http://ftp.osuosl.org) jaunty/ Packages                                 
Hit [http://repository.cairo-dock.org](http://repository.cairo-dock.org) jaunty/cairo-dock Packages            
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty/main Sources 
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty/universe Packages
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty/universe Sources
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) jaunty-updates/multiverse Sources
Fetched 8848B in 1s (6132B/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/sa.archive.ubuntu.com_ubuntu_dists_jaunty_multiverse_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by cleggton on 2009-09-27
Try [this]("http://ubuntuforums.org/showthread.php?t=863742&highlight=Encountered+a+section+with+no+Package%3A+header") thread

---

### Post by NawafLol on 2009-09-27
Thanks that did the trick !

---

