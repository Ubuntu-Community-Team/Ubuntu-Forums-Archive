---
title: "Broken libc6"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by Epitaph44 on 2009-03-15
I tried 'sudo apt-get install libc6' , but received :

```
Reading package lists... Done                
Building dependency tree                     
Reading state information... Done            
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:             
  libc6-i686: PreDepends: libc6 (= 2.8~20080505-0ubuntu9) but 2.9-4 is to be installed                                                                          
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
Taking It's advice for 'sudo apt-get -f install' , the output was :
```
sudo apt-get -f install
Reading package lists... Done             
Building dependency tree                  
Reading state information... Done         
Correcting dependencies... Done           
The following packages were automatically installed and are no longer required:
  libopenal1 python-gst0.10 scorched3d-data python-debian libwxgtk2.6-0        
  libsdl-net1.2 python-gtkhtml2 libalut0 python-sexy libwxbase2.6-0            
  python-xapian gnome-app-install libgtkhtml2-0 python-launchpad-integration   
  gnome-icon-theme update-manager-kde librsvg2-common                          
Use 'apt-get autoremove' to remove them.                                       
The following extra packages will be installed:                                
  libc6 libc6-i686                                                             
Suggested packages:                                                            
  glibc-doc                                                                    
The following packages will be upgraded:                                       
  libc6 libc6-i686                                                             
2 upgraded, 0 newly installed, 0 to remove and 858 not upgraded.               
1 not fully installed or removed.
Need to get 0B/5780kB of archives.
After this operation, 246kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libc6 libc6-i686
Install these packages without verification [y/N]? y
Preconfiguring packages ...
(Reading database ... 124452 files and directories currently installed.)
Preparing to replace libc6 2.8~20080505-0ubuntu9 (using .../archives/libc6_2.9-4_i386.deb) ...
Checking for services that may need to be restarted...
Checking init scripts...
Unpacking replacement libc6 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.9-4_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/localedef.1.gz', which is also in package belocs-locales-bin
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.9-4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

When I try to re-install it in synaptic :
```
E: /var/cache/apt/archives/libc6_2.9-4_i386.deb: trying to overwrite `/usr/share/man/man1/localedef.1.gz', which is also in package belocs-locales-bin
```

Please help ! It would seem impossible to repair this !

---

### Post by mc4man on 2009-03-15
You may want to say whether you are running 8.10 (intrepid) or 9.04 (jaunty
It appears your running 8.10 and have a 9.04 repo(s) in your sources

Also why are you trying to install libc6 in the first place (it's a core lib that's installed when you install ubuntu, trying to or installing a higher version is generally a poor idea

So a little more info and maybe post this
```

cat /etc/apt/sources.list
```

---

### Post by Epitaph44 on 2009-03-15
I need to re-install it . Synaptic says it's broken . . .

My results from cat '/etc/apt/sources.list' :

```
# deb cdrom:[Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted                                                                       
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to       
# newer versions of the distribution.                                           

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid restricted main multiverse universe #Added by software-properties                                         

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates restricted main multiverse universe #Added by software-properties                                 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in     
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.                                                                   
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe                 
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe         

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in      
## multiverse WILL NOT receive any review or updates from the Ubuntu        
## security team.                                                           
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse                
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse        

## Uncomment the following two lines to add software from the 'backports'
## repository.                                                           
## N.B. software from this repository may not have been tested as        
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.                               
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse                                                                  
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse                                                              

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main
# deb http://ppa.launchpad.net/project-neon/ubuntu hardy main
# deb http://ppa.launchpad.net/project-neon/ubuntu hardy main
# deb http://ppa.launchpad.net/project-neon/ubuntu hardy main
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main
deb http://ftp.us.debian.org/debian/ sid main
deb-src http://ftp.us.debian.org/debian/ sid main
deb http://ftp.us.debian.org/debian/ experimental main
deb-src http://ftp.us.debian.org/debian/ experimental main
```

---

### Post by mc4man on 2009-03-15
> I need to re-install it . Synaptic says it's broken . . .
The most probable reason it's 'broken' is from trying to install libc6 2.9-4  from debian main (sid)

While it's possible to have a limited 'hyprid' install, mixing debian main with intrepid repo's is not going to work well in the long run.

For instance I run intrepid with debian-multimedia and a few selected jaunty packages. I would never go into debian main for dependencies. Even then I make sure I'm not creating any version issues with packages from Intrepid.

You need to decide if you want debian -sid or ubuntu -intrepid (or possibly jaunty.

Your best bet to re install libc6 is to comment out the debian entries, do a sudo apt-get update and then do a reinstall of libc6
After that if you wish you can re enable the debian sources, just don't install anything that depends on the higher version of libc6. (or any other 'core' intrepid lib

You may also want to comment out the hardy ppa source for the moment. (if not for good

---

### Post by Epitaph44 on 2009-03-18
Thank you very much ! I have everything working again .

---

