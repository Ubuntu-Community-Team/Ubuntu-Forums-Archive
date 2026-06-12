---
title: "Update Problem"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by Naz_Farooq on 2009-04-14
Hi guys,
I have been facing a big problem for last few days but now after a hard struggle I have fixed it. The Problem was that, through a LAN Cable, I could access to main server and internet when using Ubuntu 8.10 but when I started WindowsXP, it started working well. But now I have fixed it. There is an other problem for me now. My system was last updated 38 days ago. Now when I start update manager and press "check" button for updates, it gives me errors. Some errors are of signature & some are others. I have attached a picture of the errors.
Please help me in this regard. What should I do to fix this problem.
Thanks in advance.

This comes in terminal when i start updates
```
 nazfarooq@nazfarooq-laptop:~$ gksudo gedit /etc/apt/sources.list
nazfarooq@nazfarooq-laptop:~$ sudo apt-get update
Ign http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Get:1 http://ppa.launchpad.net hardy Release.gpg [307B]                        
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Hit http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Hit http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://archive.ubuntu.org.cn intrepid Release.gpg                          
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Hit http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Hit http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Ign http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://archive.ubuntu.org.cn intrepid/main Translation-en_US               
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Get:2 http://ppa.launchpad.net intrepid Release [27.6kB]                       
Get:3 http://ppa.launchpad.net hardy Release [46.7kB]                          
Ign http://ppa.launchpad.net hardy Release                                     
Hit http://ppa.launchpad.net intrepid Release                                  
Hit http://ppa.launchpad.net intrepid Release                                  
Hit http://ppa.launchpad.net intrepid Release                                  
Get:4 http://ppa.launchpad.net intrepid Release [46.7kB]                       
Ign http://archive.ubuntu.org.cn intrepid/restricted Translation-en_US         
Ign http://ppa.launchpad.net intrepid Release                                  
Get:5 http://ppa.launchpad.net intrepid Release [27.6kB]                       
Ign http://ppa.launchpad.net intrepid/main Packages                            
Ign http://ppa.launchpad.net hardy/main Packages                               
Ign http://download.skype.com stable Release.gpg                               
Ign http://download.skype.com stable/non-free Translation-en_US                
Ign http://ppa.launchpad.net hardy/main Sources                                
Ign http://download.skype.com stable Release                                   
Ign http://download.skype.com stable/non-free Packages                         
Err http://download.skype.com stable/non-free Packages                         
  403 Forbidden [IP: 212.72.53.130 80]
Get:6 http://security.ubuntu.com intrepid-security Release.gpg [189B]          
Ign http://ppa.launchpad.net intrepid/main Packages                            
Hit http://deb.opera.com lenny Release.gpg                                     
Hit http://ae.archive.ubuntu.com intrepid Release.gpg                          
Ign http://ae.archive.ubuntu.com intrepid/main Translation-en_US               
Hit http://wine.budgetdedicated.com intrepid Release.gpg                       
Ign http://deb.opera.com lenny/non-free Translation-en_US                      
Hit http://deb.opera.com lenny Release                                         
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US        
Ign http://ae.archive.ubuntu.com intrepid/restricted Translation-en_US         
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US  
Ign http://ae.archive.ubuntu.com intrepid/universe Translation-en_US           
Ign http://deb.opera.com lenny/non-free Packages                               
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US    
Hit http://deb.opera.com lenny/non-free Packages                               
Ign http://ae.archive.ubuntu.com intrepid/multiverse Translation-en_US         
Get:7 http://ae.archive.ubuntu.com intrepid-updates Release.gpg [189B]         
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US                                                                                              
Ign http://ae.archive.ubuntu.com intrepid-updates/main Translation-en_US                                                                                                   
Get:8 http://security.ubuntu.com intrepid-security Release [51.2kB]                                                                                                        
Err http://security.ubuntu.com intrepid-security Release                                                                                                                   
  
Ign http://ae.archive.ubuntu.com intrepid-updates/restricted Translation-en_US                                                                                             
Ign http://wine.budgetdedicated.com intrepid/main Translation-en_US                                                                                                        
Ign http://ae.archive.ubuntu.com intrepid-updates/universe Translation-en_US                                                                                               
Hit http://wine.budgetdedicated.com intrepid Release                                                                                                                       
Ign http://ae.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US                                                                                             
Hit http://ae.archive.ubuntu.com intrepid Release                                                                                                                          
Hit http://apt.wicd.net hardy Release.gpg                                                                                                                                  
Get:9 http://ae.archive.ubuntu.com intrepid-updates Release [51.2kB]                                                                                                       
Err http://ae.archive.ubuntu.com intrepid-updates Release                                                                                                                  
  
Hit http://ae.archive.ubuntu.com intrepid/main Packages                                                                                                                    
Ign http://apt.wicd.net hardy/extras Translation-en_US                                                                                                                     
Ign http://ppa.launchpad.net intrepid/main Packages                                                                                                                        
Hit http://apt.wicd.net hardy Release                                                                                                                                      
Hit http://ae.archive.ubuntu.com intrepid/restricted Packages                                                                                                              
Ign http://wine.budgetdedicated.com intrepid/main Packages                                                                                                                 
Hit http://ae.archive.ubuntu.com intrepid/main Sources                                                                                                                     
Ign http://ppa.launchpad.net intrepid/main Packages                                                                                                                        
Hit http://ae.archive.ubuntu.com intrepid/restricted Sources                                                                                                               
Hit http://ae.archive.ubuntu.com intrepid/universe Packages                                                                                                                
Hit http://ae.archive.ubuntu.com intrepid/universe Sources                                                                                                            
Ign http://ppa.launchpad.net intrepid/main Packages                                                                                                                        
Ign http://ppa.launchpad.net intrepid/main Packages                                                                                                                        
Hit http://wine.budgetdedicated.com intrepid/main Packages                                                                                                            
Hit http://ppa.launchpad.net intrepid/main Packages                                                                                                                        
Ign http://apt.wicd.net hardy/extras Packages                                                                                                                              
Hit http://apt.wicd.net hardy/extras Packages                                                                                                                              
Hit http://ppa.launchpad.net hardy/main Packages                                                                                                                           
Hit http://ppa.launchpad.net hardy/main Sources                                                                                                                            
Hit http://ppa.launchpad.net intrepid/main Packages                                                                                                                        
Hit http://ppa.launchpad.net intrepid/main Packages                                                                                                                        
Hit http://ppa.launchpad.net intrepid/main Packages                                                                                                                        
Get:10 http://ppa.launchpad.net intrepid/main Packages [8896B]                                                                                                             
Hit http://ppa.launchpad.net intrepid/main Packages                                                                                                                        
Ign http://www.getdropbox.com intrepid Release.gpg                                                                                                                         
Ign http://www.getdropbox.com intrepid/main Translation-en_US                                                                                                              
Ign http://www.getdropbox.com intrepid Release                                                                                                                             
Ign http://www.getdropbox.com intrepid/main Packages                                                                                                                       
Hit http://www.getdropbox.com intrepid/main Packages                                                                                                                       
Ign http://archive.ubuntu.org.cn intrepid/universe Translation-en_US                                                                                                       
Ign http://archive.ubuntu.org.cn intrepid/multiverse Translation-en_US        
Ign http://archive.ubuntu.org.cn intrepid Release                             
Ign http://archive.ubuntu.org.cn intrepid/main Packages                       
Ign http://archive.ubuntu.org.cn intrepid/restricted Packages                 
Ign http://archive.ubuntu.org.cn intrepid/universe Packages                   
Ign http://archive.ubuntu.org.cn intrepid/multiverse Packages                 
Get:11 http://archive.ubuntu.org.cn intrepid/main Packages [85.0kB]           
Hit http://archive.ubuntu.org.cn intrepid/restricted Packages                     
Hit http://archive.ubuntu.org.cn intrepid/universe Packages                                                  
Hit http://archive.ubuntu.org.cn intrepid/multiverse Packages                                                
Hit http://ae.archive.ubuntu.com intrepid/multiverse Packages                                                                                                              
Hit http://ae.archive.ubuntu.com intrepid/multiverse Sources
Fetched 141kB in 2min13s (1062B/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures were invalid: BADSIG 778978B00F7992B0 Launchpad PPA for Project Neon
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com intrepid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://ae.archive.ubuntu.com intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-i386/Packages.gz  403 Forbidden [IP: 212.72.53.130 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release  

W: Failed to fetch http://ae.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
nazfarooq@nazfarooq-laptop:~$ 
```

---

