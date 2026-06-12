---
title: "Could not download all repository indexes"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by Muchuka on 2009-02-11
my machine cannot download anything from the repository after in had formated the machine then i installed in  again:-

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://nl.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://nl.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found
[http://nl.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:](http://nl.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://nl.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:](http://nl.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://nl.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://nl.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) 404 Not Found
[http://nl.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://nl.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found
[http://nl.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://nl.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) 404 Not Found

please help

---

### Post by Partyboi2 on 2009-02-11
Can you open a terminal (Applications>Accessories>Terminal) and post the output to
```
sudo apt-get update
```Also can you explain more on what is going wrong eg...any errors etc. 
Thanks

---

### Post by Muchuka on 2009-02-11
olives@olives-server:~$ sudo apt-get update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [189B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US    
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty Release.gpg                            
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty/main Translation-en_US       
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release               
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty/multiverse Translation-en_US
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty Release                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages   
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Translation-en_US
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [189B]  
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty/main Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release                         
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty/multiverse Packages                    
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty/restricted Packages                    
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty/universe Packages                      
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty/main Packages                          
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty/universe Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages                     
Err [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty/main Packages                          
  404 Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Packages                
Err [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty/multiverse Packages                    
  404 Not Found
Err [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty/restricted Packages                    
  404 Not Found
Err [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty/universe Packages                      
  404 Not Found
Err [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty/main Packages                          
  404 Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages               
Err [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) feisty/universe Packages                      
  404 Not Found
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages [137kB]       
99% [5 Packages gzip 0]                                              8547B/s 0s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages                 
  Sub-process gzip returned an error code (1)
Fetched 5B in 10s (0B/s)                                                       
Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://nl.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://nl.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://nl.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://nl.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://nl.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://nl.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Partyboi2 on 2009-02-11
Feisty has reached its end of life, that is why you are getting the 404 errors. You would be better of upgrading to a later release of ubuntu like hardy or intrepid.

---

### Post by Muchuka on 2009-02-11
Example i tried installing Banshee Music player and this was the reply

Banshee Music Player cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.

Thanking you in advance for your support

---

### Post by Partyboi2 on 2009-02-11
If you don't want to upgrade then you can add some other repositories 
to your sources.list so that you can still install programs.
Open a terminal and type
```
gksu gedit /etc/apt/sources.list
```
then add a #infront of all the lines that start with deb eg.
```
deb-src http://au.archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://au.archive.ubuntu.com/ubuntu/ jaunty-security multiverse
```
becomes
```
#deb-src http://au.archive.ubuntu.com/ubuntu/ jaunty-security universe
#deb http://au.archive.ubuntu.com/ubuntu/ jaunty-security multiverse
```
then after that add to the bottom of the file

```
deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse 
```
then save
and back in the terminal
```
sudo apt-get update
```

---

### Post by Muchuka on 2009-02-11
this is what i got after inserting the code " gksu gedit /etc/apt/sources.list"

olives@olives-server:~$ gksu gedit /etc/apt/sources.list
(gedit:7923): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-0/socket
This socket already exists indicating esd is already running.
Exiting...
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-0/socket
This socket already exists indicating esd is already running.
Exiting...

thank you

---

