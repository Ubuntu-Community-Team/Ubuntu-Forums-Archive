---
title: "Something wrong with Update Manager!"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by HellKing on 2009-07-26
hey guys, I can't seem to be updating my system now......I upgraded from 8.10(Ultimate Editoon) to 9.04(via automatic update)


when I do update from the terminal, I get this
```
hellking@hellking-desktop:~$ sudo apt-get update
[sudo] password for hellking: 
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_IN               
Hit http://archive.ubuntu.com jaunty Release.gpg                               
Ign http://archive.ubuntu.com jaunty/main Translation-en_IN                    
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_IN     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_IN       
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_IN    
Ign http://repoubuntusoftware.info harty Release.gpg                           
Ign http://repoubuntusoftware.info harty/all Translation-en_IN                 
Hit http://archive.canonical.com hardy Release                                 
Ign http://archive.ubuntu.com jaunty/restricted Translation-en_IN              
Ign http://archive.ubuntu.com jaunty/universe Translation-en_IN      
Ign http://archive.ubuntu.com jaunty/multiverse Translation-en_IN    
Hit http://archive.ubuntu.com jaunty-updates Release.gpg             
Ign http://archive.ubuntu.com jaunty-updates/main Translation-en_IN  
Ign http://archive.ubuntu.com jaunty-updates/restricted Translation-en_IN
Ign http://archive.ubuntu.com jaunty-updates/universe Translation-en_IN
Ign http://archive.ubuntu.com jaunty-updates/multiverse Translation-en_IN
Hit http://archive.ubuntu.com jaunty-security Release.gpg            
Ign http://security.ubuntu.com hardy-security/main Translation-en_IN           
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_IN     
Hit http://security.ubuntu.com hardy-security Release                          
Hit http://us.archive.ubuntu.com hardy Release.gpg                             
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_IN            
Hit http://us.archive.ubuntu.com hardy-updates Release                         
Ign http://repoubuntusoftware.info harty Release                               
Hit http://archive.canonical.com hardy/partner Sources                         
Ign http://archive.ubuntu.com jaunty-security/main Translation-en_IN           
Ign http://archive.ubuntu.com jaunty-security/restricted Translation-en_IN     
Hit http://us.archive.ubuntu.com hardy Release                                 
Hit http://security.ubuntu.com hardy-security/multiverse Sources               
Hit http://archive.canonical.com hardy/partner Packages                        
Ign http://repoubuntusoftware.info harty/all Packages                          
Ign http://archive.ubuntu.com jaunty-security/universe Translation-en_IN       
Ign http://archive.ubuntu.com jaunty-security/multiverse Translation-en_IN     
Hit http://archive.ubuntu.com jaunty Release                                   
Hit http://archive.ubuntu.com jaunty-updates Release                           
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources              
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages             
Hit http://security.ubuntu.com hardy-security/multiverse Packages              
Hit http://security.ubuntu.com hardy-security/universe Sources                 
Hit http://security.ubuntu.com hardy-security/universe Packages                
Hit http://security.ubuntu.com hardy-security/main Sources                     
Hit http://archive.ubuntu.com jaunty-security Release                          
Ign http://repoubuntusoftware.info harty/all Packages                          
Hit http://us.archive.ubuntu.com hardy/multiverse Sources                      
Hit http://us.archive.ubuntu.com hardy/multiverse Packages                     
Hit http://security.ubuntu.com hardy-security/restricted Sources               
Hit http://security.ubuntu.com hardy-security/main Packages          
Hit http://archive.ubuntu.com jaunty/main Packages                   
Hit http://archive.ubuntu.com jaunty/restricted Packages             
Hit http://archive.ubuntu.com jaunty/restricted Sources              
Hit http://archive.ubuntu.com jaunty/main Sources                    
Hit http://archive.ubuntu.com jaunty/multiverse Sources              
Hit http://archive.ubuntu.com jaunty/universe Sources                
Err http://repoubuntusoftware.info harty/all Packages                
  404 Not Found
Hit http://archive.ubuntu.com jaunty/universe Packages               
Hit http://archive.ubuntu.com jaunty/multiverse Packages
Hit http://archive.ubuntu.com jaunty-updates/main Packages
Hit http://archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://archive.ubuntu.com jaunty-updates/main Sources
Hit http://archive.ubuntu.com jaunty-updates/multiverse Sources
Hit http://archive.ubuntu.com jaunty-updates/universe Sources
Hit http://archive.ubuntu.com jaunty-updates/universe Packages
Hit http://archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://archive.ubuntu.com jaunty-security/main Packages
Hit http://archive.ubuntu.com jaunty-security/restricted Packages
Hit http://archive.ubuntu.com jaunty-security/restricted Sources
Hit http://archive.ubuntu.com jaunty-security/main Sources
Hit http://archive.ubuntu.com jaunty-security/multiverse Sources
Hit http://archive.ubuntu.com jaunty-security/universe Sources
Hit http://archive.ubuntu.com jaunty-security/universe Packages
Hit http://archive.ubuntu.com jaunty-security/multiverse Packages
W: Failed to fetch http://repoubuntusoftware.info/dists/harty/all/binary-amd64/Packages  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```


I guess the probjem lies in the software sources.....can anyone help me out here??

PS. I guess updatimg from Ultimate edition was the problem here?

---

