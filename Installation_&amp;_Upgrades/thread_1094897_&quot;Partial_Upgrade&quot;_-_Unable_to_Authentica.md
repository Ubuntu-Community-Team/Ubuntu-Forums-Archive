---
title: "&quot;Partial Upgrade&quot; - Unable to Authenticate some packages"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by TBerk on 2009-03-13
This thread is based on the following post:
[http://ubuntuforums.org/showthread.php?t=136257&highlight=multisync](http://ubuntuforums.org/showthread.php?t=136257&highlight=multisync)

It relates to adding some repositories and getting SynCE installed.

[Note: I have redacted my host name and have chopped off the initial portion of the follow copy/paste to concentrate on the end, relevant portion. tb]

<snip>
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages [6552B]
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources [2985B]
Fetched 37.8kB in 2s (15.9kB/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B152F042D246C25D
W: You may want to run apt-get update to correct these problems
xxxxxx@txxxxxx-desktop:~$ sudo apt-get install synce-hal librra0-tools librapi2-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package librra0-tools is a virtual package provided by:
  librra-tools 0.13-0ubuntu0~ppa1~intrepid1
You should explicitly select one to install.
E: Package librra0-tools has no installation candidate
xxxxxx@xxxxxx-desktop:~$ 

AND Then:

--------------------------------

Update manager pops up and runs a 'partial update'.

------------------------------------
Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.


librapi2
librra-tools
librra0
librtfcomp0
libsynce-dbg
libsynce0
opensync-plugin-synce
python-rapi2
python-rra
python-rtfcomp
synce-hal
synce-kpm
synce-sync-engine
-------------------------

This leaves me with a an upgrade manger that still wants to install 12 upgrades; those listed above 'librapi2' to 'synce-sync-engine', inclusive.

My objective is to ultimately run SynCE to a pocketpc based PDA via a USB connection. 

I also note a 'No Public Key' message. 

Any help with this would be appreciated.

TBerk

---

### Post by prickee on 2009-03-13
I get the same thing when trying to update. I partial upgrade then get error authenticating some packages:
amsn
libaudacious4
pidgin-libnotify
w32codecs


 

:~$ sudo apt-get update
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1) intrepid Release.gpg
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1) intrepid/main Translation-en_US
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1) intrepid/restricted Translation-en_US
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1) intrepid Release
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1) intrepid/main Packages
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1) intrepid/restricted Packages
Err cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1) intrepid/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1) intrepid/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) intrepid Release.gpg                        
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) intrepid/all Translation-en_US              
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) intrepid Release                            
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) intrepid/all Packages                       
Hit [http://repoubuntusoftware.info](http://repoubuntusoftware.info) intrepid/all Packages                       
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                           
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US                     
Get:2 [http://dl.google.com](http://dl.google.com) testing Release.gpg [189B]                          
Ign [http://dl.google.com](http://dl.google.com) testing/non-free Translation-en_US                    
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1300B]                              
Get:4 [http://dl.google.com](http://dl.google.com) testing Release [772B]                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                     
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US                  
Get:6 [http://apt.debianchile.org](http://apt.debianchile.org) unstable Release.gpg [189B]                   
Ign [http://apt.debianchile.org](http://apt.debianchile.org) unstable/main Translation-en_US                 
Get:7 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [954B]                     
Get:8 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release.gpg [191B]              
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Translation-en_US            
Get:9 [http://dl.google.com](http://dl.google.com) testing/non-free Packages [746B]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                             
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_US            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports Release.gpg                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:12 [http://apt.debianchile.org](http://apt.debianchile.org) unstable Release [3594B]                     
Get:13 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release [1025B]                
Ign [http://apt.debianchile.org](http://apt.debianchile.org) unstable Release                                
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release                           
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/main Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/restricted Translation-en_US  
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/universe Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/multiverse Translation-en_US  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release.gpg                    
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46.7kB]                      
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Hit [http://apt.debianchile.org](http://apt.debianchile.org) unstable/main Packages                          
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages                     
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Get:18 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [52.9kB]                        
Get:19 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46.7kB]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Translation-en_US     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Translation-en_US   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Sources                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports Release                       
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
  404 Not Found
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Sources
Fetched 5765B in 2s (2628B/s)
W: GPG error: [http://apt.debianchile.org](http://apt.debianchile.org) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2C392DFEEFD17969
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 778978B00F7992B0
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 43C0AFF0D7FAE680
W: Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://ppa.launchpad.net/googlegadgets/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/googlegadgets/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
:~$

---

### Post by ronaldrand on 2009-03-16
Try something like this.. it worked for me.

gpg --keyserver hkp://subkeys.pgp.net --recv-keys B152F042D246C25D
sudo gpg --export --armor "B152F042D246C25D" | sudo apt-key add -
sudo apt-get update

Also, I think librra-tools provides librra0-tools.

---

### Post by forger on 2009-03-17
try this perl script, it should work for launchpad PPA repositories: [http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by SaintDanBert on 2010-03-20
> **ronaldrand said:**
> Try something like this.. it worked for me.
```

gpg --keyserver hkp://subkeys.pgp.net --recv-keys B152F042D246C25D
sudo gpg --export --armor "B152F042D246C25D" | sudo apt-key add -
sudo apt-get update

```
Also, I think librra-tools provides librra0-tools.

When I use [highlight]gpg --keyserver ...[/highlight] there is a keyserver timeout. Does this tell me that some PPA has become orphan
or that I have a key that is stale (eg--intrepid vs. jaunty)?
Also, how do I discover which package is doing the asking?

~~~ 0;-Dan

---

### Post by slakkie on 2010-03-20
Keyserver is probably busy, try one of the following:

keyserver.ubuntu.com
wwwkeys.eu.pgp.net

I myself make use of this line to add keys:

sudo apt-key adv --keyserver KEYSERVER --recv-keys KEY

---

### Post by PhillyChz on 2010-03-21
> **slakkie said:**
> Keyserver is probably busy, try one of the following:

keyserver.ubuntu.com
wwwkeys.eu.pgp.net

I myself make use of this line to add keys:

sudo apt-key adv --keyserver KEYSERVER --recv-keys KEY

I kept having server timeouts with the other commands/servers posted, this did the trick.
Thanks :D

---

### Post by SaintDanBert on 2010-03-22
> **forger said:**
> try this perl script, it should work for launchpad PPA repositories: [http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

Using your script I get:
```

user@host:path/ $ sudo ./launchpad-ppa-fix.pl

Found apt source list files:
  /etc/apt/sources.list

Checking file /etc/apt/sources.list
luckybackup-maintainers/ppa
Detected/Correct: deb http://ppa.launchpad.net/luckybackup-maintainers
/ppa/ubuntu jaunty main
luckybackup-maintainers/+archive/ppa
luckybackup-maintainers/ppa
Detected/Correct: deb-src http://ppa.launchpad.net/luckybackup-maintainers/ppa/ubuntu jaunty main
luckybackup-maintainers/+archive/ppa
synce/ppa
Detected/Correct: deb http://ppa.launchpad.net/synce/ppa/ubuntu jaunty main

synce/+archive/ppa

karl.hegbloom/ppa
Detected/Correct: deb-src http://ppa.launchpad.net/karl.hegbloom/ppa/ubuntu intrepid main
karl.hegbloom/+archive/ppa

No change for /etc/apt/sources.list

Will retrieve keys for: luckybackup-maintainers/+archive/ppa synce/+archive/ppa karl.hegbloom/+archive/ppa
Attempting to get Launchpad key for luckybackup-maintainers/+archive/ppa: http://launchpad.net/~luckybackup-maintainers/+archive/ppa
Attempting to get Launchpad key for synce/+archive/ppa: http://launchpad.net/~synce/+archive/ppa
Attempting to get Launchpad key for karl.hegbloom/+archive/ppa: http://launchpad.net/~karl.hegbloom/+archive/ppa

All done.

```

I don't know if I should expect more ... need to finish understanding your script ... but I continue to get:

```

user@host:path/ $  sudo apt-get update
...
Hit http://us.archive.ubuntu.com jaunty-backports/main Sources
Hit http://us.archive.ubuntu.com jaunty-backports/restricted Sources
Hit http://us.archive.ubuntu.com jaunty-backports/universe Sources
Hit http://us.archive.ubuntu.com jaunty-backports/multiverse Sources
Fetched 308B in 1s (195B/s)
Reading package lists... Done

W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B152F042D246C25D

W: You may want to run apt-get update to correct these problems
user@host:path/ $

```

I suspect that I have software looking for a package key for edition -N- and package key on file for *buntu edition -not-N-. None of the messages or utilities tell me which package causes the complaint.
(grinning) For security reasons, there likely is no way to ask "who owns this key?"

~~~ 0;-/ Dan

---

