---
title: "update problem"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by bulls_eye on 2009-08-24
Hi all,

I have recently upgraded to ubuntu 9.04 and i am pretty happy with the way things are goin...

There is one problem though...
The update manager keeps showing the '!' mark, although I update my system quite frequently...
God I hate to see it...

To get rid of it when i type sudo apt-get update in the terminal i get the foll 404 error...

owner@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_US
Get:1 [http://mirror.noreply.org](http://mirror.noreply.org) jaunty Release.gpg [197B]                      
Get:2 [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg [189B]                 
Get:3 [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty Release.gpg [189B]                
Ign [http://mirror.noreply.org](http://mirror.noreply.org) jaunty/main Translation-en_US                    
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/main Translation-en_US              
Get:4 [http://mirror.noreply.org](http://mirror.noreply.org) jaunty Release [1930B]               
Ign [http://mirror.noreply.org](http://mirror.noreply.org) jaunty Release                             
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                      
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/restricted Translation-en_US        
Ign [http://mirror.noreply.org](http://mirror.noreply.org) jaunty/main Packages                   
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/universe Translation-en_US          
Ign [http://mirror.noreply.org](http://mirror.noreply.org) jaunty/main Sources                              
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources              
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/multiverse Translation-en_US        
Hit [http://mirror.noreply.org](http://mirror.noreply.org) jaunty/main Packages
Get:5 [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-updates Release.gpg [189B]
Hit [http://mirror.noreply.org](http://mirror.noreply.org) jaunty/main Sources                              
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-updates/main Translation-en_US                
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-updates/restricted Translation-en_US          
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-updates/universe Translation-en_US
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-updates/multiverse Translation-en_US
Get:6 [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-security Release.gpg [189B]
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-security/main Translation-en_US               
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-security/restricted Translation-en_US
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-security/universe Translation-en_US
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-security/multiverse Translation-en_US
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/main Release.gpg
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/main/Sources Translation-en_US
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/restricted Release.gpg
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/restricted/Sources Translation-en_US
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty Release
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-updates Release
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-security Release
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/main Release 
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/restricted Release
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/main Packages
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/restricted Packages
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/main Sources
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/restricted Sources
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/universe Packages
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/universe Sources
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/multiverse Packages
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/multiverse Sources
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-updates/main Packages
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-updates/restricted Packages
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-updates/main Sources
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-updates/restricted Sources
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-updates/universe Packages
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-updates/universe Sources
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-updates/multiverse Packages
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-updates/multiverse Sources
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-security/main Packages
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-security/restricted Packages
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-security/main Sources
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-security/restricted Sources
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-security/universe Packages
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-security/universe Sources
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-security/multiverse Packages
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-security/multiverse Sources
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/main/Sources Packages
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/restricted/Sources Packages
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/main Sources
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/restricted Sources
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/universe Sources
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/multiverse Sources
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-updates/main Sources
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-updates/restricted Sources
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-updates/universe Sources
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-updates/multiverse Sources
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-security/main Sources
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-security/restricted Sources
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-security/universe Sources
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-security/multiverse Sources
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/main/Sources Packages
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/restricted/Sources Packages
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/main Sources
  404 Not Found
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/restricted Sources
  404 Not Found
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/universe Sources
  404 Not Found
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/multiverse Sources
  404 Not Found
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-updates/main Sources
  404 Not Found
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-updates/restricted Sources
  404 Not Found
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-updates/universe Sources
  404 Not Found
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-updates/multiverse Sources
  404 Not Found
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-security/main Sources
  404 Not Found
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-security/restricted Sources
  404 Not Found
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-security/universe Sources
  404 Not Found
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty-security/multiverse Sources
  404 Not Found
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/main/Sources Packages
  404 Not Found
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) jaunty/restricted/Sources Packages
  404 Not Found
Fetched 2883B in 12min 9s (4B/s)
W: GPG error: [http://mirror.noreply.org](http://mirror.noreply.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CFF71CB3AFA44BDD
W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/jaunty/main/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/jaunty/main/source/Sources)  404 Not Found

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/jaunty/restricted/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/jaunty/restricted/source/Sources)  404 Not Found

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/jaunty/universe/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/jaunty/universe/source/Sources)  404 Not Found

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/jaunty/multiverse/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/jaunty/multiverse/source/Sources)  404 Not Found

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/jaunty-updates/main/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/jaunty-updates/main/source/Sources)  404 Not Found

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/jaunty-updates/restricted/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/jaunty-updates/restricted/source/Sources)  404 Not Found

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/jaunty-updates/universe/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/jaunty-updates/universe/source/Sources)  404 Not Found

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/jaunty-updates/multiverse/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/jaunty-updates/multiverse/source/Sources)  404 Not Found

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/jaunty-security/main/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/jaunty-security/main/source/Sources)  404 Not Found

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/jaunty-security/restricted/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/jaunty-security/restricted/source/Sources)  404 Not Found

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/jaunty-security/universe/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/jaunty-security/universe/source/Sources)  404 Not Found

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/jaunty-security/multiverse/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/jaunty-security/multiverse/source/Sources)  404 Not Found

W: Failed to fetch [http://ftp.iitm.ac.in/dists/jaunty/main/Sources/binary-i386/Packages](http://ftp.iitm.ac.in/dists/jaunty/main/Sources/binary-i386/Packages)  404 Not Found

W: Failed to fetch [http://ftp.iitm.ac.in/dists/jaunty/restricted/Sources/binary-i386/Packages](http://ftp.iitm.ac.in/dists/jaunty/restricted/Sources/binary-i386/Packages)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

Anybody having some ideas??
Thank you

---

### Post by Katalog on 2009-08-24
Maybe try switching servers in your repository settings?

---

### Post by bulls_eye on 2009-08-24
what do you imply?
you mean that the files are not available on the server i m usin??

---

### Post by Katalog on 2009-08-25
If you open up Synaptic, you can got to "Settings>Repositories" and on the first page in the dialog menu there should be a dropdown menu that says "Download from:" that let's you select a different server to download updates from if you are having troubles with the one you're currently using.

---

### Post by bulls_eye on 2009-08-25
thats fine...
but the thing is that i get better speed from this server and many packages that aren't available on the main server ae available on this one...
that is y i use it...
anyways i  will try server from some other country...
thanks a lot...

---

