---
title: "sudo apt-get update not working???"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by SweatyBanana on 2009-08-10
well rather not workin correctly. One of the web servers down maybe???


Re-installed ubuntu (needed a clean start) on a 200gb sata drive. Running a HP Pavilion a1600n.

```
matt@matt-desktop:~$ sudo apt-get update
Hit http://archive.ubuntu.com dapper Release.gpg                               
Ign http://archive.ubuntu.com dapper/main Translation-en_US                    
Ign http://archive.ubuntu.com dapper/restricted Translation-en_US              
Hit http://security.ubuntu.com dapper-security Release.gpg                     
Ign http://security.ubuntu.com dapper-security/main Translation-en_US          
Ign http://security.ubuntu.com dapper-security/restricted Translation-en_US    
Ign http://archive.ubuntu.com dapper/universe Translation-en_US                
Ign http://archive.ubuntu.com dapper/multiverse Translation-en_US              
Hit http://archive.ubuntu.com dapper-updates Release.gpg                       
Ign http://archive.ubuntu.com dapper-updates/main Translation-en_US            
Ign http://archive.ubuntu.com dapper-updates/restricted Translation-en_US      
Ign http://archive.ubuntu.com dapper-updates/universe Translation-en_US        
Ign http://archive.ubuntu.com dapper-updates/multiverse Translation-en_US      
Hit http://archive.ubuntu.com dapper-backports Release.gpg                     
Ign http://archive.ubuntu.com dapper-backports/main Translation-en_US          
Ign http://security.ubuntu.com dapper-security/universe Translation-en_US      
Ign http://security.ubuntu.com dapper-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com dapper-security Release                         
Ign http://archive.ubuntu.com dapper-backports/restricted Translation-en_US    
Ign http://archive.ubuntu.com dapper-backports/universe Translation-en_US      
Ign http://archive.ubuntu.com dapper-backports/multiverse Translation-en_US    
Hit http://archive.ubuntu.com dapper Release                                   
Hit http://archive.ubuntu.com dapper-updates Release                           
Hit http://security.ubuntu.com dapper-security/main Packages                   
Hit http://archive.ubuntu.com dapper-backports Release                         
Hit http://archive.ubuntu.com dapper/main Packages                             
Hit http://archive.ubuntu.com dapper/restricted Packages                       
Hit http://archive.ubuntu.com dapper/universe Packages                         
Hit http://archive.ubuntu.com dapper/multiverse Packages                       
Hit http://archive.ubuntu.com dapper/main Sources                              
Hit http://security.ubuntu.com dapper-security/restricted Packages             
Hit http://security.ubuntu.com dapper-security/universe Packages               
Hit http://security.ubuntu.com dapper-security/multiverse Packages             
Hit http://security.ubuntu.com dapper-security/main Sources                    
Hit http://archive.ubuntu.com dapper/restricted Sources                        
Hit http://archive.ubuntu.com dapper/universe Sources                          
Hit http://archive.ubuntu.com dapper/multiverse Sources                        
Hit http://security.ubuntu.com dapper-security/restricted Sources              
Hit http://security.ubuntu.com dapper-security/universe Sources                
Hit http://security.ubuntu.com dapper-security/multiverse Sources              
Hit http://archive.ubuntu.com dapper-updates/main Packages                     
Hit http://archive.ubuntu.com dapper-updates/restricted Packages               
Hit http://archive.ubuntu.com dapper-updates/universe Packages                 
Hit http://archive.ubuntu.com dapper-updates/multiverse Packages               
Hit http://archive.ubuntu.com dapper-updates/main Sources                      
Hit http://archive.ubuntu.com dapper-updates/restricted Sources                
Hit http://archive.ubuntu.com dapper-updates/universe Sources                  
Hit http://archive.ubuntu.com dapper-updates/multiverse Sources                
Hit http://archive.ubuntu.com dapper-backports/main Packages                   
Hit http://archive.ubuntu.com dapper-backports/restricted Packages             
Hit http://archive.ubuntu.com dapper-backports/universe Packages               
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages             
Hit http://archive.ubuntu.com dapper-backports/main Sources                    
Hit http://archive.ubuntu.com dapper-backports/restricted Sources              
Hit http://archive.ubuntu.com dapper-backports/universe Sources                
Hit http://archive.ubuntu.com dapper-backports/multiverse Sources              
Err http://packages.freecontrib.org dapper Release.gpg                         
  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out
Err http://packages.freecontrib.org dapper/free Translation-en_US
  Unable to connect to packages.freecontrib.org http:
Err http://packages.freecontrib.org dapper/non-free Translation-en_US
  Unable to connect to packages.freecontrib.org http:
Reading package lists... Done
W: Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out

W: Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_US.bz2  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_US.bz2  Unable to connect to packages.freecontrib.org http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

---

### Post by slakkie on 2009-08-10
Remove the failing repo's (the packages.freecontrib.org ones). and retry.

---

### Post by LowSky on 2009-08-10
Dapper isn't a new release, far from it.  try 8.04 (Hardy) or 9.04 (Jaunty)

to edit

```
 sudo gedit /etc/apt/sources.list
```

remove 
```

http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg  
http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_US.bz2  
 
http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_US.bz2  
```

---

### Post by SweatyBanana on 2009-08-10
> **LowSky said:**
> Dapper isn't a new release, far from it.  try 8.04 (Hardy) or 9.04 (Jaunty)

to edit

```
 sudo gedit /etc/apt/sources.list
```remove 
```

http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg  
http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_US.bz2  
 
http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_US.bz2  
```


It seems as if one of my roomates edited my source list. Can someone post up the original???

---

### Post by slakkie on 2009-08-11
> **SweatyBanana said:**
> It seems as if one of my roomates edited my source list. Can someone post up the original???

Remove the freecontrib url's and you are good to go.

---

### Post by zkriesse on 2009-08-11
Or you could do the synaptic update[SIZE=6] FIRST [SIZE=1]and then do sudo apt-get update and sudo apt-get upgrade...[/SIZE][/SIZE]

---

### Post by SweatyBanana on 2009-08-11
> **Zachk18 said:**
> Or you could do the synaptic update[SIZE=6] FIRST [SIZE=1]and then do sudo apt-get update and sudo apt-get upgrade...[/SIZE][/SIZE]


The synaptic update only gives me the option to remove some of my programs when I select updates and hit apply. is this normal?



Removed the freecontrib updates and apt-get update works fine now... I am going to go read the docs on ubuntu over the next few days and learn a bit about this os.

Sorry for my somewhat stupid questions... Just haven't had time between work, sleep, and school to read over the docs.

---

