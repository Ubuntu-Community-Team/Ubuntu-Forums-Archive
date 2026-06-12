---
title: "package list update not completing."
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by rolandixor on 2009-02-28
This strangely started after my internet connection got 3x faster, but I don't think they're related.

Anyway, here is the problem, it get's to 36* out of 400, and then just sticks there. I tried to apply updates since then, but some packages could not be found. Any ideas what this could be?

---

### Post by taurus on 2009-02-28
If you have update manager, add/remove, or synaptic open, close it.  Then open a terminal and post the outputs of these two commands, running one at a time.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by rolandixor on 2009-02-28
okay... I was going to do that, but I felt lazy lol.

---

### Post by rolandixor on 2009-02-28
rolandixor@KINDOMSYS-LT:~/Desktop$ sudo apt-get update
[sudo] password for rolandixor: 
Ign [http://www.getdropbox.com](http://www.getdropbox.com) intrepid Release.gpg                             
Ign [http://www.getdropbox.com](http://www.getdropbox.com) intrepid/main Translation-en_US                  
Hit [http://download.virtualbox.org](http://download.virtualbox.org) intrepid Release.gpg                        
Ign [http://download.virtualbox.org](http://download.virtualbox.org) intrepid/non-free Translation-en_US         
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:2 [http://directhex.mfgames.com](http://directhex.mfgames.com) hardy Release.gpg [189B]                    
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US  
Ign [http://directhex.mfgames.com](http://directhex.mfgames.com) hardy/main Translation-en_US                  
Ign [http://unicap-imaging.org](http://unicap-imaging.org) intrepid Release.gpg                             
Hit [http://apt.jenslody.de](http://apt.jenslody.de) any Release.gpg                                     
Ign [http://apt.jenslody.de](http://apt.jenslody.de) any/main Translation-en_US                          
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid Release.gpg                      
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid/cairo-dock Translation-en_US     
Hit [http://deb.opera.com](http://deb.opera.com) lenny Release.gpg                                     
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free Translation-en_US                      
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg                            
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Translation-en_US                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg                         
Get:3 [http://debian.scribus.net](http://debian.scribus.net) intrepid Release.gpg [189B]                    
Ign [http://debian.scribus.net](http://debian.scribus.net) intrepid/main Translation-en_US                  
Ign [http://debian.scribus.net](http://debian.scribus.net) intrepid/non-free Translation-en_US              
Ign [http://www.getdropbox.com](http://www.getdropbox.com) intrepid Release                                 
Ign [http://dominique.corbex.net](http://dominique.corbex.net) intrepid Release.gpg                           
Ign [http://dominique.corbex.net](http://dominique.corbex.net) intrepid/main Translation-en_US                
Get:4 [http://debian.tagancha.org](http://debian.tagancha.org) intrepid Release.gpg [189B]                   
Ign [http://debian.tagancha.org](http://debian.tagancha.org) intrepid/main Translation-en_US                 
Ign [http://debian.tagancha.org](http://debian.tagancha.org) intrepid/non-free Translation-en_US             
Err [http://playonlinux.botux.net](http://playonlinux.botux.net) intrepid Release.gpg                          
  Could not resolve 'playonlinux.botux.net'
Err [http://playonlinux.botux.net](http://playonlinux.botux.net) intrepid/main Translation-en_US               
  Could not resolve 'playonlinux.botux.net'
Ign [http://apt.wxwidgets.org](http://apt.wxwidgets.org) any Release.gpg                                   
Ign [http://apt.wxwidgets.org](http://apt.wxwidgets.org) any/main Translation-en_US                        
Hit [http://download.virtualbox.org](http://download.virtualbox.org) intrepid Release                            
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                     
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) intrepid Release.gpg                         
Get:9 [http://directhex.mfgames.com](http://directhex.mfgames.com) hardy Release [3660B]                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US    
Ign [http://directhex.mfgames.com](http://directhex.mfgames.com) hardy Release                                 
Ign [http://unicap-imaging.org](http://unicap-imaging.org) intrepid/main Translation-en_US                  
Ign [http://unicap-imaging.org](http://unicap-imaging.org) intrepid/contrib Translation-en_US               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Get:10 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release.gpg [191B]             
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Translation-en_US            
Hit [http://apt.jenslody.de](http://apt.jenslody.de) any Release                                         
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg                          
Get:11 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US               
Hit [http://deb.opera.com](http://deb.opera.com) lenny Release                                         
Get:12 [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release [110B]                      
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US                     
Ign [http://www.getdropbox.com](http://www.getdropbox.com) intrepid/main Packages                           
Get:13 [http://debian.scribus.net](http://debian.scribus.net) intrepid Release [5589B]                      
Get:14 [http://debian.tagancha.org](http://debian.tagancha.org) intrepid Release [5589B]                     
Ign [http://debian.scribus.net](http://debian.scribus.net) intrepid Release                                 
Ign [http://debian.tagancha.org](http://debian.tagancha.org) intrepid Release                                
Ign [http://dominique.corbex.net](http://dominique.corbex.net) intrepid Release                               
Hit [http://download.virtualbox.org](http://download.virtualbox.org) intrepid/non-free Packages                  
Get:15 [http://apt.wxwidgets.org](http://apt.wxwidgets.org) hardy-wx Release.gpg [189B]                    
Ign [http://apt.wxwidgets.org](http://apt.wxwidgets.org) hardy-wx/main Translation-en_US                   
Ign [http://apt.wxwidgets.org](http://apt.wxwidgets.org) any Release                                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Ign [http://directhex.mfgames.com](http://directhex.mfgames.com) hardy/main Packages                           
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) intrepid/multiverse Translation-en_US        
Get:18 [http://download.tuxfamily.org](http://download.tuxfamily.org) ./ Release.gpg [197B]                     
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) ./ Translation-en_US                         
Ign [http://unicap-imaging.org](http://unicap-imaging.org) intrepid Release                                 
Get:19 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release [1025B]                
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US              
Get:20 [http://dl.google.com](http://dl.google.com) testing Release.gpg [189B]                         
Ign [http://dl.google.com](http://dl.google.com) testing/non-free Translation-en_US                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US       
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid/cairo-dock Packages              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US 
Ign [http://apt.jenslody.de](http://apt.jenslody.de) any/main Packages                                   
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages                               
Get:21 [http://dl.google.com](http://dl.google.com) stable Release [1300B]                             
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free Packages                               
Hit [http://www.getdropbox.com](http://www.getdropbox.com) intrepid/main Packages                           
Hit [http://debian.tagancha.org](http://debian.tagancha.org) intrepid/main Packages                          
Ign [http://dominique.corbex.net](http://dominique.corbex.net) intrepid/main Packages                         
Hit [http://debian.scribus.net](http://debian.scribus.net) intrepid/main Packages                           
Get:22 [http://apt.wxwidgets.org](http://apt.wxwidgets.org) hardy-wx Release [3420B]                       
Ign [http://apt.wxwidgets.org](http://apt.wxwidgets.org) hardy-wx Release                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:23 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:24 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Hit [http://directhex.mfgames.com](http://directhex.mfgames.com) hardy/main Packages                           
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Ign [http://unicap-imaging.org](http://unicap-imaging.org) intrepid/main Packages                           
Get:25 [http://download.tuxfamily.org](http://download.tuxfamily.org) intrepid Release [1046B]                  
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release.gpg                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Translation-en_US     
Hit [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid/cairo-dock Packages              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security Release.gpg                 
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages                               
Ign [http://apt.jenslody.de](http://apt.jenslody.de) any/main Sources                                    
Get:26 [http://dl.google.com](http://dl.google.com) testing Release [772B]                             
Hit [http://deb.opera.com](http://deb.opera.com) lenny/non-free Packages                               
Hit [http://debian.tagancha.org](http://debian.tagancha.org) intrepid/non-free Packages                      
Ign [http://apt.wxwidgets.org](http://apt.wxwidgets.org) any/main Packages                                 
Err [http://dominique.corbex.net](http://dominique.corbex.net) intrepid/main Packages                         
  404 Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:27 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Hit [http://debian.scribus.net](http://debian.scribus.net) intrepid/non-free Packages                       
Ign [http://unicap-imaging.org](http://unicap-imaging.org) intrepid/contrib Packages                        
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US          
Get:28 [http://download.tuxfamily.org](http://download.tuxfamily.org) ./ Release [956B]                         
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) ./ Release                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/main Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/universe Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                              
Hit [http://apt.jenslody.de](http://apt.jenslody.de) any/main Packages                                   
Get:29 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [966B]                    
Hit [http://apt.wxwidgets.org](http://apt.wxwidgets.org) hardy-wx/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:30 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:31 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Err [http://unicap-imaging.org](http://unicap-imaging.org) intrepid/main Packages                           
  404 Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release                    
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) intrepid/multiverse Packages                 
Hit [http://apt.jenslody.de](http://apt.jenslody.de) any/main Sources                                    
Get:32 [http://dl.google.com](http://dl.google.com) testing/non-free Packages [734B]                   
Err [http://apt.wxwidgets.org](http://apt.wxwidgets.org) any/main Packages                                 
  404 Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:33 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:34 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Err [http://unicap-imaging.org](http://unicap-imaging.org) intrepid/contrib Packages                        
  404 Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security Release                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources                   
Get:35 [http://download.tuxfamily.org](http://download.tuxfamily.org) ./ Packages [9839B]                       
Ign [https://launchpad.net](https://launchpad.net) intrepid Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources                     
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages [192kB]       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:37 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                    
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources [95.8kB]       
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages [302kB]     
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages [8073B]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources [95.6kB]     
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources [2474B]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages [72.7kB]
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources [17.0kB] 
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages [10.4kB]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:46 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:47 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:48 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                    
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources [3839B]
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Packages [14B]
Get:51 [http://download.tuxfamily.org](http://download.tuxfamily.org) intrepid/multiverse Packages [983B]       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg    
Get:52 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Packages [79.9kB]  
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Packages [14B]
Get:55 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Packages [36.8kB]
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Sources [15.8kB]   
Get:57 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Sources [14B]
Get:58 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Sources [12.2kB]
Get:59 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Sources [14B]
Get:60 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/main Packages [80.3kB] 
Get:61 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/restricted Packages [3504B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Get:62 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/main Sources [22.4kB]
Get:63 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/restricted Sources [1154B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Get:64 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/universe Packages [29.2kB]
Get:65 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/universe Sources [5440B] 
Get:66 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/multiverse Packages [6449B]
Get:67 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/multiverse Sources [1860B]
Get:68 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:69 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:70 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:71 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Get:72 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46.7kB]                      
Get:73 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Get:74 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                    
Get:75 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46.7kB]                    
Get:76 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                    
Get:77 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46.7kB]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Get:78 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46.7kB]                      
Get:79 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                      
Get:80 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Get:81 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46.7kB]                      
Get:82 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Get:83 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46.7kB]                      
Get:84 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                      
Get:85 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                      
Get:86 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Get:87 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46.7kB]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Get:88 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                      
Get:89 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Get:90 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Get:91 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Get:92 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Get:93 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                      
Get:94 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Get:95 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Get:96 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                      
Get:97 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                      
Get:98 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Get:99 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46.7kB]                      
Get:100 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Get:101 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                     
Get:102 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                     
Get:103 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                     
Get:104 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                        
Get:105 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Get:106 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                     
Get:107 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46.7kB]                     
Get:108 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46.7kB]                     
Get:109 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
  404 Not Found
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
  404 Not Found
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
99% [Translation-en_US bzip2

---

### Post by taurus on 2009-02-28
Obviously, you are running intrepid but how come you have a bunch of hardy repos in /etc/apt/sources.list?  You need to edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove those hardy repos and that **playonlinux.botux.net** since it's a dead site!  Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```

Otherwise, post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by rolandixor on 2009-02-28
lol I can asure you most of the hardy repos work. The reason I use those ones is since they don't support intrepid, I have to use the backwards compatible ones.

I should point out, that it seems not to be accessing ubuntu's supported updates as well.

---

### Post by taurus on 2009-02-28
If you want to mix hardy and intrepid in /etc/apt/sources.list, all I can say is good luck.

---

### Post by rolandixor on 2009-02-28
problem solved. I removed playonlinux and a few others, as well as the hardy repos (some of them are useless now)!

Thank!
:-)

---

### Post by rolandixor on 2009-02-28
why can't we mark threads as solved?

---

### Post by Riba1122 on 2009-03-02
Because threads aren't (always) ment to solved :)

---

