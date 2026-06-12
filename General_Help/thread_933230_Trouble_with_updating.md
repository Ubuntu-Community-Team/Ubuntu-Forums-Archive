---
title: "Trouble with updating"
date: 2008-09-29
forum: General Help
---

### Post by thibeaz on 2008-09-29
Ok this is a first time for me having this kind of problem since I've been using ubuntu since 5.10 but in 8.04.1 I compiled madwifi for my Athero's 5007eg card, since it's now working I decided to do some updates... 
Enter Problem.
Problem is when I do updates with ubuntu I get this error from Terminal
```
sudo apt-get update
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_CA
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_CA
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701) hardy/main Translation-en_CA
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701) hardy/restricted Translation-en_CA
Get:1 http://ca.archive.ubuntu.com hardy Release.gpg [189B]                    
Get:2 http://ca.archive.ubuntu.com hardy Release.gpg [189B]                    
Get:3 http://ca.archive.ubuntu.com hardy Release.gpg [189B]                    
Ign http://ca.archive.ubuntu.com hardy/main Translation-en_CA                  
Err http://ca.archive.ubuntu.com hardy/restricted Translation-en_CA            
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.45 80]
Ign http://ca.archive.ubuntu.com hardy/universe Translation-en_CA              
Err http://ca.archive.ubuntu.com hardy/multiverse Translation-en_CA            
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.45 80]
Hit http://ca.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://ca.archive.ubuntu.com hardy-updates/main Translation-en_CA          
Err http://ca.archive.ubuntu.com hardy-updates/restricted Translation-en_CA    
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.45 80]
Ign http://repository.cairo-dock.org hardy Release.gpg                         
Err http://repository.cairo-dock.org hardy/cairo-dock Translation-en_CA        
  Error reading from server - read (104 Connection reset by peer)
Ign http://repository.cairo-dock.org hardy Release                             
Ign http://repository.cairo-dock.org hardy/cairo-dock Packages                 
Ign http://ca.archive.ubuntu.com hardy-updates/universe Translation-en_CA      
Err http://ca.archive.ubuntu.com hardy-updates/multiverse Translation-en_CA    
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.45 80]
Hit http://ca.archive.ubuntu.com hardy-security Release.gpg                    
Ign http://ca.archive.ubuntu.com hardy-security/main Translation-en_CA         
Err http://ca.archive.ubuntu.com hardy-security/restricted Translation-en_CA   
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.45 80]
Ign http://ca.archive.ubuntu.com hardy-security/universe Translation-en_CA     
Ign http://ca.archive.ubuntu.com hardy Release                                 
Hit http://repository.cairo-dock.org hardy/cairo-dock Packages                 
Hit http://ca.archive.ubuntu.com hardy-updates Release                         
Hit http://packages.medibuntu.org hardy Release.gpg                            
Ign http://packages.medibuntu.org hardy/free Translation-en_CA                 
Err http://packages.medibuntu.org hardy/non-free Translation-en_CA             
  Error reading from server - read (104 Connection reset by peer)
Hit http://ca.archive.ubuntu.com hardy-security Release                        
Hit http://ca.archive.ubuntu.com hardy/main Packages                           
Hit http://packages.medibuntu.org hardy Release                                
Hit http://ca.archive.ubuntu.com hardy/restricted Packages                     
Ign mirror://www.getdeb.net hardy/ Release.gpg                                 
Hit http://ca.archive.ubuntu.com hardy/main Sources                            
Hit http://packages.medibuntu.org hardy/free Packages                          
Hit http://ca.archive.ubuntu.com hardy/restricted Sources                      
Hit http://ca.archive.ubuntu.com hardy/universe Packages                       
Hit http://packages.medibuntu.org hardy/non-free Packages                      
Hit http://ca.archive.ubuntu.com hardy/universe Sources                        
Ign mirror://www.getdeb.net hardy/ Translation-en_CA                          
Hit http://ca.archive.ubuntu.com hardy/multiverse Packages                    
Hit http://ca.archive.ubuntu.com hardy/multiverse Sources                     
Hit http://ca.archive.ubuntu.com hardy-updates/main Packages                  
Hit http://ca.archive.ubuntu.com hardy-updates/restricted Packages            
Hit http://ca.archive.ubuntu.com hardy-updates/main Sources                   
Hit http://ca.archive.ubuntu.com hardy-updates/restricted Sources             
Ign mirror://www.getdeb.net hardy/ Release                                    
Hit mirror://www.getdeb.net hardy/ Packages                                   
Hit http://ca.archive.ubuntu.com hardy-updates/universe Packages
Hit http://ca.archive.ubuntu.com hardy-updates/universe Sources
Hit http://ca.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://ca.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://ca.archive.ubuntu.com hardy-security/main Packages
Hit http://ca.archive.ubuntu.com hardy-security/restricted Packages
Hit http://ca.archive.ubuntu.com hardy-security/universe Packages
Hit http://ca.archive.ubuntu.com hardy-security/main Sources
Hit http://ca.archive.ubuntu.com hardy-security/restricted Sources
Fetched 189B in 3s (52B/s)                              
W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_CA.bz2  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.45 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_CA.bz2  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.45 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_CA.bz2  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.45 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_CA.bz2  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.45 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_CA.bz2  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.45 80]

W: Failed to fetch http://packages.medibuntu.org/dists/hardy/non-free/i18n/Translation-en_CA.bz2  Error reading from server - read (104 Connection reset by peer)

W: Failed to fetch http://repository.cairo-dock.org/ubuntu/dists/hardy/cairo-dock/i18n/Translation-en_CA.bz2  Error reading from server - read (104 Connection reset by peer)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```
Now since I got this I took from my desktop running the same Version of Ubuntu as my laptop and copied the /etc/apt/sources.list file and I still get the same error.
So I was wondering if some of you guys have any insight what the case maybe

---

### Post by Kevbert on 2008-09-29
You have your CDROM ticked in Software Sources which you shouldn't need so you can deselect it and the other problem may be the server. Try selecting a different server in the 'Download from:' box.

---

### Post by thibeaz on 2008-09-29
hmm I thought I did so already...
Anyways it's still not updating even after I unticked the option for the cd, running the software sources application I get issues with downloading translations for en_ca specific. I'm serious this is really something new for me :P
EDIT: I also forgot to include this
```
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release: The following signatures were invalid: NODATA 2
W: You may want to run apt-get update to correct these problems
```
and thats from running sudo apt-get update

---

### Post by thibeaz on 2008-09-30
Problem was resolved when I got to a steady ethernet connection, I guess Ubuntu doesn't like updating through my Atheros Wifi Card :P

---

