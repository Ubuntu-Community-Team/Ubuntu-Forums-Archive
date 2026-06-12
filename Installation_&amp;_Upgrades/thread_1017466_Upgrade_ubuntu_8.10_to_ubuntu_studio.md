---
title: "Upgrade ubuntu 8.10 to ubuntu studio ???"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by cobalt69 on 2008-12-21
hey i have looked around for a while but all i can find is the repositories for ubuntu studio feisty and we dont have a dvd drive to install ubuntu studio from so what im asking you is how would i update ubuntu (intrepid) to ubuntu studio 8.10 or higher? 

Thanks a Bunch!,
 
           Cobalt69

---

### Post by Partyboi2 on 2008-12-21
You can upgrade to ubuntu studio by opening a terminal (Applications>Accessories>Terminal)
```
sudo aptitude update && sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

---

### Post by cobalt69 on 2008-12-21
OMG thank you so much we have been looking all over the place


Wait we got this error

gtfo@ubuntu:~$ sudo aptitude update && sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
[sudo] password for gtfo: 
Err [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) intrepid Release.gpg
  Could not resolve 'archive.ubuntustudio.org'
Err [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) intrepid/main Translation-en_US
  Could not resolve 'archive.ubuntustudio.org'
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US                
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                           
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources                             
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources            
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Reading package lists... Done

gtfo@ubuntu:~$

---

### Post by namdung on 2008-12-21
Search and  install from Synaptic Package Manager --> ubuntustudio-desktop. This will select all dependencies.

Try changing the software source if packages are not downloading in *System ---> Software Sources* OR by typing in terminal *sudo gedit /etc/apt/sources.list*.

---

### Post by _nate on 2009-01-08
Would this change the kernel to the low lateny kernel which comes with ubuntu studio?  if not is it possible to change the kernel?

---

### Post by _nate on 2009-01-09
What should I be adding to the sources.list file?  I clicked on update my system after changing from Ubuntu 8.04 to Ubuntu Studio 8.04 and once the computer rebooted it removed the real time kernel and replaced it with the generic kernel.

---

