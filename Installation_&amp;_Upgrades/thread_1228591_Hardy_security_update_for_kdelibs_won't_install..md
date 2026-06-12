---
title: "Hardy: security update for kdelibs won't install."
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by AlanRick on 2009-08-01
I can't install the security update for kdelibs, kdelibsdata and kdelibs4c2a

```
Failed to fetch http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/hardy/Release  Unable to find expected entry  mai/source/Sources in Meta-index file (malformed Release file?)

Some index files failed to download, they have been ignored, or old ones used instead.
```

I'm not sure if that's my problem of if some file on launchpad is malformed.

I'm not even sure if I need kde (it came when I installed kcron).

This is what I got when I tried ```
sudo apt-get update -o Acquire::http::No-Cache=true

``` which was suggested in bug 24234.


```
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_GB               
Hit http://de.archive.ubuntu.com hardy Release.gpg                             
Hit http://de.archive.ubuntu.com hardy/main Translation-en_GB                  
Hit http://de.archive.ubuntu.com hardy/restricted Translation-en_GB            
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Ign http://security.ubuntu.com hardy-security/main Translation-en_GB           
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_GB     
Hit http://de.archive.ubuntu.com hardy/universe Translation-en_GB              
Hit http://de.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://de.archive.ubuntu.com hardy-updates/main Translation-en_GB          
Ign http://de.archive.ubuntu.com hardy-updates/restricted Translation-en_GB    
Ign http://de.archive.ubuntu.com hardy-updates/universe Translation-en_GB      
Hit http://de.archive.ubuntu.com hardy-backports Release.gpg         
Ign http://de.archive.ubuntu.com hardy-backports/main Translation-en_GB
Ign http://de.archive.ubuntu.com hardy-backports/restricted Translation-en_GB
Hit http://archive.canonical.com hardy Release                       
Ign http://security.ubuntu.com hardy-security/universe Translation-en_GB
Hit http://security.ubuntu.com hardy-security Release                          
Hit http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_GB            
Ign http://de.archive.ubuntu.com hardy-backports/universe Translation-en_GB
Hit http://de.archive.ubuntu.com hardy Release                       
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://security.ubuntu.com hardy-security/main Packages                    
Hit http://ppa.launchpad.net hardy Release                           
Hit http://de.archive.ubuntu.com hardy-updates Release                         
Hit http://de.archive.ubuntu.com hardy-backports Release                       
Hit http://archive.canonical.com hardy/partner Sources                         
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Hit http://security.ubuntu.com hardy-security/main Sources                     
Hit http://security.ubuntu.com hardy-security/restricted Sources               
Hit http://security.ubuntu.com hardy-security/universe Packages                
Hit http://de.archive.ubuntu.com hardy/main Packages                           
Hit http://ppa.launchpad.net hardy/main Packages                               
Hit http://security.ubuntu.com hardy-security/universe Sources       
Hit http://de.archive.ubuntu.com hardy/restricted Packages
Hit http://de.archive.ubuntu.com hardy/main Sources
Hit http://de.archive.ubuntu.com hardy/restricted Sources
Hit http://de.archive.ubuntu.com hardy/universe Packages
Hit http://de.archive.ubuntu.com hardy/universe Sources
Hit http://de.archive.ubuntu.com hardy-updates/main Packages
Hit http://de.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://de.archive.ubuntu.com hardy-updates/main Sources
Hit http://de.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://de.archive.ubuntu.com hardy-updates/universe Packages
Hit http://de.archive.ubuntu.com hardy-updates/universe Sources
Hit http://de.archive.ubuntu.com hardy-backports/main Packages
Hit http://de.archive.ubuntu.com hardy-backports/restricted Packages
Hit http://de.archive.ubuntu.com hardy-backports/universe Packages
W: Failed to fetch http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/hardy/Release  Unable to find expected entry  mai/source/Sources in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by AlanRick on 2009-08-01
looks like I had a typo in the repository path (mai instead of main).
The root of problem is
```
No change rebuild to satisfy build dependency for kdepim security update
```
(when I click the red-down arrow and look at the details of the security updates)
I removed kcron and the kde apps and then re-installed but it didn't help. There still seems to be a dependency problem.


*update* kdepim is not installed. 
So why this error message?
Alan

---

