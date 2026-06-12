---
title: "Problem installing wine in ubuntu 8.4 live cd"
date: 2008-11-27
forum: General Help
---

### Post by Tony007 on 2008-11-27
Hi all. I used VMware Player to boot ubuntu 8.4 iso and followed the bellow Command Line Instructions for Installing Wine:

> Command Line Instructions for Installing Wine:
An alternate method for adding the Wine repositories and installing Wine is through the command line, as follows:

First, open a terminal window (Applications->Accessories->Terminal). On Debian, you will need to open a root terminal. Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following into your terminal:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:

For Ubuntu Intrepid (8.10):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list](http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/winehq.list

For Ubuntu Hardy (8.04):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list

For Debian Etch (4.0):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/etch.list](http://wine.budgetdedicated.com/apt/sources.list.d/etch.list) -O /etc/apt/sources.list.d/winehq.list

Then update APT's package information by running 'sudo apt-get update'. 

If you are using Ubuntu, you can now install Wine by clicking this link. Alternatively, you can install by going to Applications->Add/Remove and searching for Wine.


But unfortunately  i get this error:


> ubuntu@ubuntu:~/Desktop$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

[B]The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
E: Broken packages[/B]


I be happy if you guys help install wine correctly.Thanks

Full script:

> ubuntu@ubuntu:~/Desktop$ wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
OK
ubuntu@ubuntu:~/Desktop$ sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list
--17:59:43--  [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list)
           => `/etc/apt/sources.list.d/winehq.list'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 180 [text/plain]

100%[====================================>] 180           --.--K/s             

17:59:43 (9.33 MB/s) - `/etc/apt/sources.list.d/winehq.list' saved [180/180]

ubuntu@ubuntu:~/Desktop$ sudo apt-get update
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg                          
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_US               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Reading package lists... Done
ubuntu@ubuntu:~/Desktop$ wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
OK
ubuntu@ubuntu:~/Desktop$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
E: Broken packages

---

