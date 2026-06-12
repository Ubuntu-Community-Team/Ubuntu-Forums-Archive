---
title: "Can't Upgrade to 9.04"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by albertjvm on 2009-04-24
When I attempt to upgrade to jaunty via the update manager, the first couple times i tried it failed to download the release notes. The last time I tried it got the release notes, then hung for awhile and then gave me this error message: 

Authentication failed
Authenticating the upgrade failed. There may be a problem with the network or with the server. 

when i run apt-get dist-upgrade from the terminal i get:
~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

and apt-get update gives this:
~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_CA  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release             
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages     
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid Release.gpg
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates Release.gpg
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/multiverse Packages
Reading package lists... Done

any help would be appreciated

---

### Post by cariboo on 2009-04-24
With everybody updating or installing Jaunty the servers have been very slow. I took me about three hours to install all the programs I need for a fresh installation using the Canadian server. You may want to try a different server. Go to System-->Administration-->Software Sources and click other from the Download from dropdown, the click the Choose Best Server button and wait for it to finish checking. once it is done click Choose Server.

---

### Post by albertjvm on 2009-04-24
ok, I tried it again, twice each on two different servers with the same result. If it's just a traffic issue, I can be patient... i guess.

---

