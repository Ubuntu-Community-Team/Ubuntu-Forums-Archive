---
title: "cant upgrade"
date: 2008-10-30
forum: General Help
---

### Post by stupor on 2008-10-30
Leaves out some updates at bottom of the page.
A error occurred during the signature verification


bob@bob-desktop:~$ sudo apt-get update
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_NZ               
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_NZ         
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages              
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_NZ
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_NZ
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_NZ
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_NZ
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_NZ
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_NZ
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_NZ
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_NZ        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_NZ
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_NZ
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_NZ
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_NZ
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_NZ             
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [9335B]                  
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages [6322B]
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages [7934B] 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Sources                
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release [58.5kB]                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release                           
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                            
  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
Fetched 23.8kB in 12s (1843B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

---

### Post by zvacet on 2008-10-30
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by stupor on 2008-10-30
Still no luck



W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

