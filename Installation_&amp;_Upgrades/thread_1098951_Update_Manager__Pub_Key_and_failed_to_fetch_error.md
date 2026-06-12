---
title: "Update Manager:  Pub Key and failed to fetch error"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by AoA Linux on 2009-03-17
Hey guys, I keep having trouble updating my Ubuntu 8.10.  The following errors are what I am getting:


W: GPG error: [http://dl.google.com](http://dl.google.com) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

W: GPG error: [http://apt.debianchile.org](http://apt.debianchile.org) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2C392DFEEFD17969
W: Failed to fetch [http://packages.medibuntu.org/dists/intrepid/Release](http://packages.medibuntu.org/dists/intrepid/Release)  

W: Failed to fetch [http://ppa.launchpad.net/googlegadgets/ppa/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/googlegadgets/ppa/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: Duplicate sources.list entry [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages (/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_intrepid_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problemsW: GPG error: [http://dl.google.com](http://dl.google.com) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

W: GPG error: [http://apt.debianchile.org](http://apt.debianchile.org) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2C392DFEEFD17969
W: Failed to fetch [http://packages.medibuntu.org/dists/intrepid/Release](http://packages.medibuntu.org/dists/intrepid/Release)  

W: Failed to fetch [http://ppa.launchpad.net/googlegadgets/ppa/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/googlegadgets/ppa/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: Duplicate sources.list entry [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages (/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_intrepid_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

---

### Post by AoA Linux on 2009-03-17
Bump... anyone know how I can fix this?  Thanks

---

### Post by hatguy on 2009-03-17
Much the same with Ubuntu 8.04, followed by:

:~$ sudo apt-get clean
[sudo] password for user: 
:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                     
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                 
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages      
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Fetched 308B in 1s (268B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 726C32B538D04956
W: You may want to run apt-get update to correct these problems

Note that I've just run apt-get clean and apt-get update. The synaptic error occured yesterday and today.

HatGuy

---

### Post by Partyboi2 on 2009-03-17
Open a terminal and for 
> 
W: GPG error: [http://dl.google.com]("http://dl.google.com/") testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991 add the key
```
wget -q -O - [http://dl.google.com/linux/linux_signing_key.pub](http://dl.google.com/linux/linux_signing_key.pub) | sudo  apt-key add 
```For this one
> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://packages.medibuntu.org]("http://packages.medibuntu.org/") intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Add the key
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```Then  post the remaining W: message  results from sudo apt-get update. also can you post the out put to
```
cat /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
```


@ Hatguy

Open a terminal and add the key
```
gpg --keyserver keyserver.ubuntu.com --recv 726C32B538D04956
gpg --export --armor 726C32B538D04956  | sudo apt-key add -
```
then
```
sudo apt-get update
```

---

### Post by hatguy on 2009-03-17
Partiboi2,

Thanks! Worked perfectly!

HatGuy

---

### Post by AoA Linux on 2009-03-18
> **Partyboi2 said:**
> Open a terminal and for 
 add the key
```
wget -q -O - [http://dl.google.com/linux/linux_signing_key.pub](http://dl.google.com/linux/linux_signing_key.pub) | sudo  apt-key add 
```For this one
Add the key
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```Then  post the remaining W: message  results from sudo apt-get update. also can you post the out put to
```
cat /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
```


@ Hatguy

Open a terminal and add the key
```
gpg --keyserver keyserver.ubuntu.com --recv 726C32B538D04956
gpg --export --armor 726C32B538D04956  | sudo apt-key add -
```
then
```
sudo apt-get update
```



when I paste that into the terminal:  wget -q -O - [http://dl.google.com/linux/linux_signing_key.pub](http://dl.google.com/linux/linux_signing_key.pub) | sudo  apt-key add      , it says   
gpg: can't open `': No such file or directory

---

### Post by Partyboi2 on 2009-03-18
That was my mistake, make sure you add - at the end of the line after 'add'
[FONT=monospace]
[/FONT]```
wget -q -O - [http://dl.google.com/linux/linux_signing_key.pub](http://dl.google.com/linux/linux_signing_key.pub) | sudo  apt-key add -
```

---

