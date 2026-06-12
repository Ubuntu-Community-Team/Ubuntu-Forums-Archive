---
title: "Upgrade from 8.10 To 9.04 Failed"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by ericinwisconsin on 2009-04-25
I left the computer running last night to do the upgrade, but it didn't complete. So I started again, using 'sudo apt-get update' first. I get the following:

```

Hit http://archive.canonical.com jaunty Release.gpg
Ign http://archive.canonical.com jaunty/partner Translation-en_US              
Hit http://security.ubuntu.com jaunty-security Release.gpg                     
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US          
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US    
Hit http://archive.canonical.com jaunty Release                                
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US      
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com jaunty-security Release                         
Ign http://archive.canonical.com jaunty/partner Packages                       
Hit http://security.ubuntu.com jaunty-security/main Packages                   
Ign http://archive.canonical.com jaunty/partner Sources                        
Hit http://security.ubuntu.com jaunty-security/restricted Packages             
Hit http://security.ubuntu.com jaunty-security/main Sources                    
Hit http://security.ubuntu.com jaunty-security/restricted Sources              
Hit http://security.ubuntu.com jaunty-security/universe Packages               
Hit http://archive.canonical.com jaunty/partner Packages                       
Hit http://security.ubuntu.com jaunty-security/universe Sources                
Hit http://security.ubuntu.com jaunty-security/multiverse Packages             
Hit http://security.ubuntu.com jaunty-security/multiverse Sources              
Hit http://archive.canonical.com jaunty/partner Sources                        
Hit http://us.archive.ubuntu.com jaunty Release.gpg                            
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US             
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US           
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg                    
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com jaunty Release
Hit http://us.archive.ubuntu.com jaunty-updates Release
Hit http://us.archive.ubuntu.com jaunty/main Packages
Hit http://us.archive.ubuntu.com jaunty/restricted Packages
Hit http://us.archive.ubuntu.com jaunty/main Sources
Hit http://us.archive.ubuntu.com jaunty/restricted Sources
Hit http://us.archive.ubuntu.com jaunty/universe Packages
Hit http://us.archive.ubuntu.com jaunty/universe Sources
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://us.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correctthe problem.

```

When I run 'sudo dpkg --configure -a', I get 

```

dpkg: parse error, in file `/var/lib/dpkg/status' near line 1:
 newline in field name `#!/bin/sh'

```

Any ides, gang?

Eric

---

### Post by Partyboi2 on 2009-04-26
Hi, try using the old status file. Open a terminal and backup your current
```
sudo cp /var/lib/dpkg/status  /var/lib/dpkg/status.broke
```then make the swap
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```
then 
```
sudo dpkg --configure -a
```

---

### Post by ericinwisconsin on 2009-04-28
That did it. Thanks, Partyboi2!

Eric

---

