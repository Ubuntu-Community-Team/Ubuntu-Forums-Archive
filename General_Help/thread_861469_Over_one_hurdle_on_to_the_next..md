---
title: "Over one hurdle on to the next."
date: 2008-07-16
forum: General Help
---

### Post by edward fish on 2008-07-16
I'm trying to get wine to work so I can play some video games on my Linux machine, but I can't seem to get it to install:

edward@Cthulhu:~$ sudo apt-get install wine
[sudo] password for edward:
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
  wine: Depends: libldap-2.4-2 (>= 2.4.7) but it is not installable
        PreDepends: dpkg (>= 1.14.12ubuntu3) but 1.14.5ubuntu16 is to be installed
E: Broken packages
edward@Cthulhu:~$ 

Thats the message I get, any suggestions?
I'm new, and lost.

---

### Post by jerome1232 on 2008-07-16
I would try the following code, usually helps to resolve dependency problems
```
sudo apt-get update && sudo apt-get dist-upgrade
```

might want to try
```
sudo apt-get install libldap-2.4-2
```
see if it will install

hopefully that helps

---

### Post by edward fish on 2008-07-16
> **jerome1232 said:**
> I would try the following code, usually helps to resolve dependency problems
```
sudo apt-get update && sudo apt-get dist-upgrade
```

might want to try
```
sudo apt-get install libldap-2.4-2
```
see if it will install

hopefully that helps

After the last one,

 

edward@Cthulhu:~$ sudo apt-get install libldap-2.4-2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libldap-2.4-2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libldap-2.4-2 has no installation candidate

---

### Post by Viper666 on 2008-07-16
maybe you don't have all the repositories enabled?

```
sudo gedit /etc/apt/sources.list
```

and uncomment the lines containing deb (remove the "#" symbol")

```
sudo apt-get update
```

and try installing wine again...

---

### Post by edward fish on 2008-07-16
> **Viper666 said:**
> maybe you don't have all the repositories enabled?

```
sudo gedit /etc/apt/sources.list
```

and uncomment the lines containing deb (remove the "#" symbol")

```
sudo apt-get update
```

and try installing wine again...

They all seem to have the #, do I delete the # on all of them?

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:

---

### Post by Viper666 on 2008-07-16
well this seems to be your problem... have no idea why they show up as "Line commented out by installer because it failed to verify"

yeah try uncommenting all the "#" infront of the "deb" lines and see if that works

---

### Post by edward fish on 2008-07-16
> **Viper666 said:**
> well this seems to be your problem... have no idea why they show up as "Line commented out by installer because it failed to verify"

yeah try uncommenting all the "#" infront of the "deb" lines and see if that works

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
 deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse restricted universe main

Thats what it looks like now, correct?

---

### Post by edward fish on 2008-07-16
This is what happens now...

edward@Cthulhu:~$ sudo gedit /etc/apt/sources.list
[sudo] password for edward:
edward@Cthulhu:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [189B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US               
Get:5 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release [6998B]                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release [58.5kB]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US            
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [189B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US    
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release.gpg [189B]          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Translation-en_US        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US  
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release [65.9kB]                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                              
Get:10 [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages [3613B]             
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release [58.5kB]             
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages [103kB]         
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release [44.0kB]           
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages [1075kB]               
Get:15 [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources [1483B]              
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages [5280B]   
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources [19.6kB]         
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources [944B]     
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages [75.1kB]    
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources [11.5kB]     
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages [5774B]   
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources [812B]     
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages [7664B]          
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources [306kB]                 
Get:25 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg [191B]                
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_US               
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources [2120B]           
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages [4065kB]       
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release                              
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                        
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                        
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources [1226kB]            
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages [158kB]          
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources [56.8kB]          
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages [271kB]        
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages [5764B]  
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources [74.2kB]        
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources [944B]    
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages [100kB]    
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources [16.9kB]    
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages [10.8kB] 
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources [1881B]   
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Packages [32.6kB]     
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Packages [14B]  
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Packages [103kB]  
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Packages [16.9kB]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Sources [9660B]       
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Sources [14B]   
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Sources [25.0kB]  
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Sources [3659B] 
Fetched 8031kB in 13s (581kB/s)                                                
Reading package lists... Done
edward@Cthulhu:~$ sudo apt-get install wine
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
  wine: Depends: libldap-2.4-2 (>= 2.4.7) but it is not installable
        PreDepends: dpkg (>= 1.14.12ubuntu3) but 1.14.5ubuntu16 is to be installed
E: Broken packages
edward@Cthulhu:~$

---

### Post by Viper666 on 2008-07-16
hmmmm.... strange... the repository's are working now but still the dependency problem

---

### Post by jerome1232 on 2008-07-16
you gotta do the sudo apt-get update first otherwise you're computer won't fetch all the stuff you uncommented

edit: nvm i should read more carefully you did, still do try a sudo apt-get dist-upgrade with all the new sources, it *might* help

---

### Post by Viper666 on 2008-07-16
just wanted to suggest the dist-upgrade... if that doesnt work... you might try a little dirty trick as in downloading & installing that package manually from over here: [http://packages.ubuntu.com/hardy/libldap-2.4-2]("http://packages.ubuntu.com/hardy/libldap-2.4-2")

---

### Post by edward fish on 2008-07-16
> **jerome1232 said:**
> you gotta do the sudo apt-get update first otherwise you're computer won't fetch all the stuff you uncommented

edit: nvm i should read more carefully you did, still do try a sudo apt-get dist-upgrade with all the new sources, it *might* help

edward@Cthulhu:~$ sudo apt-get dist-upgrade
[sudo] password for edward:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Viper666 on 2008-07-16
> **edward fish said:**
> edward@Cthulhu:~$ sudo apt-get dist-upgrade
[sudo] password for edward:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

you have synaptic or an update/install window already opened... if you don't and still get the error do a reboot and try again

---

### Post by edward fish on 2008-07-16
> **Viper666 said:**
> you have synaptic or an update/install window already opened... if you don't and still get the error do a reboot and try again

I was asked to run a distritbution upgrade that is still in progress, would that interfere?

---

### Post by Viper666 on 2008-07-16
> **edward fish said:**
> I was asked to run a distritbution upgrade that is still in progress, would that interfere?

leave it to finish what it's doing and then try the rest

---

### Post by edward fish on 2008-07-16
> **Viper666 said:**
> leave it to finish what it's doing and then try the rest

Fair enough, I'll post results as soon as I get them, thanks.

---

