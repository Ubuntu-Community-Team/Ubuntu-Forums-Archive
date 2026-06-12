---
title: "[ERROR] cant run apt-get update"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by dogafin on 2009-09-13
dogafin@dogafin-desktop:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                          
Get:1 [http://deb.opera.com](http://deb.opera.com) stable Release.gpg [189B]                           
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Get:2 [http://deb.opera.com](http://deb.opera.com) stable Release [1067B]                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages            
Ign [http://deb.opera.com](http://deb.opera.com) stable Release                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources   
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages
Fetched 190B in 1s (130B/s)
W: GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?:confused:



should i uninstall and reinstall opera?

---

### Post by tacantara on 2009-09-13
Did you have Synaptic, the Add/Remove, or the Update Manager running when you attempted to run sudo apt-get?

---

### Post by dogafin on 2009-09-13
i made sure nothing else was running..

also im getting this error alot when i try to install sometihng in add/remove

E: ttf-sazanami-mincho: subprocess post-installation script returned error exit status 1
E: ttf-kochi-gothic: subprocess post-installation script returned error exit status 1
E: ttf-kochi-mincho: subprocess post-installation script returned error exit status 1
E: ttf-liberation: subprocess post-installation script returned error exit status 1
E: ttf-thai-tlwg: subprocess post-installation script returned error exit status 1



like i cant even install cheese in the terminal


dogafin@dogafin-desktop:~$ sudo apt-get install cheese
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cheese is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ttf-sazanami-mincho (20040629-2ubuntu2) ...
E: /var/lib/defoma/locked exists.
E: Another defoma process seems running, or you aren't root.
E: If you are root and defoma process isn't running undoubtedly,
E: it is possible that defoma might have aborted.
E: Please run defoma-reconfigure -f to fix its broken status.
dpkg: error processing ttf-sazanami-mincho (--configure):
 subprocess post-installation script returned error exit status 1
Setting up ttf-kochi-gothic (1.0.20030809-8) ...
E: /var/lib/defoma/locked exists.
E: Another defoma process seems running, or you aren't root.
E: If you are root and defoma process isn't running undoubtedly,
E: it is possible that defoma might have aborted.
E: Please run defoma-reconfigure -f to fix its broken status.
dpkg: error processing ttf-kochi-gothic (--configure):
 subprocess post-installation script returned error exit status 1
Setting up ttf-kochi-mincho (1.0.20030809-8) ...
E: /var/lib/defoma/locked exists.
E: Another defoma process seems running, or you aren't root.
E: If you are root and defoma process isn't running undoubtedly,
E: it is possible that defoma might have aborted.
E: Please run defoma-reconfigure -f to fix its broken status.
dpkg: error processing ttf-kochi-mincho (--configure):
 subprocess post-installation script returned error exit status 1
Setting up ttf-liberation (1.04.93-1) ...
E: /var/lib/defoma/locked exists.
E: Another defoma process seems running, or you aren't root.
E: If you are root and defoma process isn't running undoubtedly,
E: it is possible that defoma might have aborted.
E: Please run defoma-reconfigure -f to fix its broken status.
dpkg: error processing ttf-liberation (--configure):
 subprocess post-installation script returned error exit status 1
Setting up ttf-thai-tlwg (1:0.4.11-2) ...
No apport report written because MaxReports is reached already
                                                              E: /var/lib/defoma/locked exists.
E: Another defoma process seems running, or you aren't root.
E: If you are root and defoma process isn't running undoubtedly,
E: it is possible that defoma might have aborted.
E: Please run defoma-reconfigure -f to fix its broken status.
dpkg: error processing ttf-thai-tlwg (--configure):
 subprocess post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 ttf-sazanami-mincho
 ttf-kochi-gothic
 ttf-kochi-mincho
 ttf-liberation
 ttf-thai-tlwg
E: Sub-process /usr/bin/dpkg returned an error code (1)
dogafin@dogafin-desktop:~$

---

### Post by tacantara on 2009-09-13
Hmm....this is a bit beyond my Ubuntu knowledge.  Have you tried running any (or all) of these error messages through Google?  When I get stumped I use Google, usually with great results.  Sorry I can't give you a better answer than that.

---

### Post by Partyboi2 on 2009-09-13
In the terminal type
```
sudo defoma-reconfigure -f
``` and see if that fixes the problem.


For the opera gpg key error, you will need to add the key
```
wget -O - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add -
sudo apt-get update
```

---

### Post by Soul-Sing on 2009-09-13
```
sudo rm /var/lib/dpkg/lock
```

if this doesn't work:

```
sudo killall apt-get
```

---

### Post by dogafin on 2009-09-13
> **Partyboi2 said:**
> In the terminal type
```
sudo defoma-reconfigure -f
``` and see if that fixes the problem.


For the opera gpg key error, you will need to add the key
```
wget -O - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add -
sudo apt-get update
```

thank you! i dont get any errors like i did before thank you so much! :popcorn:


and i was able to install cheese! :D

ur a genius!

---

### Post by Partyboi2 on 2009-09-13
> **dogafin said:**
> thank you! i dont get any errors like i did before thank you so much! :popcorn:


and i was able to install cheese! :D

ur a genius!
I don't think I am a genius, but happy to have helped :)

---

### Post by xodus1914 on 2009-09-17
Nah, you're a genius, it helped me too.

---

### Post by dip huda on 2009-09-17
I also got a problem at the time of updating. It shows:

[B]W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/Release.gpg](http://medibuntu.sos-sts.com/repo/dists/feisty/Release.gpg)  Could not resolve 'medibuntu.sos-sts.com'

W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/i18n/Translation-en_US.bz2](http://medibuntu.sos-sts.com/repo/dists/feisty/free/i18n/Translation-en_US.bz2)  Could not resolve 'medibuntu.sos-sts.com'

W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/i18n/Translation-en_US.bz2](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/i18n/Translation-en_US.bz2)  Could not resolve 'medibuntu.sos-sts.com'

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release](http://bd.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources.bz2)  Hash Sum mismatch

W: Some index files failed to download, they have been ignored, or old ones used instead.[/B]


Can any one help me please.

Thanks

---

### Post by Partyboi2 on 2009-09-17
> **dip huda said:**
> I also got a problem at the time of updating. It shows:

[B]W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/Release.gpg](http://medibuntu.sos-sts.com/repo/dists/feisty/Release.gpg)  Could not resolve 'medibuntu.sos-sts.com'

W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/i18n/Translation-en_US.bz2](http://medibuntu.sos-sts.com/repo/dists/feisty/free/i18n/Translation-en_US.bz2)  Could not resolve 'medibuntu.sos-sts.com'

W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/i18n/Translation-en_US.bz2](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/i18n/Translation-en_US.bz2)  Could not resolve 'medibuntu.sos-sts.com'

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release](http://bd.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources.bz2)  Hash Sum mismatch

W: Some index files failed to download, they have been ignored, or old ones used instead.[/B]


Can any one help me please.

Thanks
Looks like you have mixed your sources.list with Jaunty and Feisty repos. Can you open a terminal (Applications>Accessories>Terminal) and post the output to
```
cat /etc/apt/sources.list
``` and someone should be able to help you fix the entries.

---

### Post by mithun.kamath on 2009-09-21
Hey Partyboi2,

Try this
Go to System > Administration > Software Sources
Change Download From to main server


[http://ubuntuforums.org/showthread.php?t=1267690](http://ubuntuforums.org/showthread.php?t=1267690)

Regards,
Mithun

---

### Post by Partyboi2 on 2009-09-21
> **mithun.kamath said:**
> Hey Partyboi2,

Try this
Go to System > Administration > Software Sources
Change Download From to main server


[http://ubuntuforums.org/showthread.php?t=1267690](http://ubuntuforums.org/showthread.php?t=1267690)

Regards,
Mithun
Why do I need to change my download server? :P

---

