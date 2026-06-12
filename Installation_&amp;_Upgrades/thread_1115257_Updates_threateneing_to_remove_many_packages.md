---
title: "Updates threateneing to remove many packages"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by paulhurleyuk on 2009-04-03
I'm running Kubuntu 8.10 (2.6.27-7 generic).  I keep it fairly up to date, doing updates weekly or so.  Today the update icon appeared, so I clicked and told it to fetch the list of packages.

The list seems to be mainly packages that will be removed.  The list includes many of the kde games, amor, kdesudo, adept, ark, systemsettings, kdm, kdelibs5-data and kmix to name but a few...

Now, usually I don't even look at the list, luckily today I did.  Does anyone know why it's suggesting I kill my system, or how I can find what's the root cause ?

Thanks

Paul.

---

### Post by bapoumba on 2009-04-03
Please post your sources.list and the update output
```
cat /etc/apt/sources.list
sudo apt-get update
```

Have you been using third party repos?

---

### Post by paulhurleyuk on 2009-04-03
sources.list
```

# deb cdrom:[Kubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1)]/ intrepid main restricted                                                                          
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to            
# newer versions of the distribution.                                                

deb http://gb.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid restricted main multiverse universe #Added by software-properties                                                   

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates restricted main multiverse universe #Added by software-properties                                           

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any  
## review or updates from the Ubuntu security team.                        
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid universe                 
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates universe         

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in      
## multiverse WILL NOT receive any review or updates from the Ubuntu        
## security team.                                                           
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid multiverse                
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse        

## Uncomment the following two lines to add software from the 'backports'
## repository.                                                           
## N.B. software from this repository may not have been tested as        
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.                               
# deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse                                                                         
# deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse                                                                     

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is 
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.                                                                
deb http://archive.canonical.com/ubuntu intrepid partner                 
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://apt.wicd.net intrepid extras
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main
deb http://packages.medibuntu.org/ hardy free non-free

```

Result of sudo apt-get update
```

Hit http://gb.archive.ubuntu.com intrepid Release.gpg                                
Hit http://gb.archive.ubuntu.com intrepid/main Translation-en_GB                     
Hit http://gb.archive.ubuntu.com intrepid/restricted Translation-en_GB               
Get: 1 http://ppa.launchpad.net intrepid Release.gpg [307B]                          
Ign http://ppa.launchpad.net intrepid/main Translation-en_GB                         
Hit http://archive.canonical.com intrepid Release.gpg                                
Ign http://archive.canonical.com intrepid/partner Translation-en_GB                  
Hit http://packages.medibuntu.org hardy Release.gpg                                  
Ign http://packages.medibuntu.org hardy/free Translation-en_GB                       
Hit http://security.ubuntu.com intrepid-security Release.gpg                         
Ign http://security.ubuntu.com intrepid-security/main Translation-en_GB              
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_GB        
Hit http://gb.archive.ubuntu.com intrepid/universe Translation-en_GB                 
Hit http://gb.archive.ubuntu.com intrepid/multiverse Translation-en_GB               
Hit http://gb.archive.ubuntu.com intrepid-updates Release.gpg                        
Hit http://gb.archive.ubuntu.com intrepid-updates/main Translation-en_GB             
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Translation-en_GB       
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Translation-en_GB         
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Translation-en_GB       
Get: 2 http://ppa.launchpad.net intrepid Release [46.7kB]                            
Ign http://ppa.launchpad.net intrepid Release                                        
Hit http://gb.archive.ubuntu.com intrepid Release                                    
Hit http://archive.canonical.com intrepid Release                                    
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_GB          
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_GB        
Hit http://security.ubuntu.com intrepid-security Release                             
Ign http://packages.medibuntu.org hardy/non-free Translation-en_GB                   
Hit http://packages.medibuntu.org hardy Release                                      
Hit http://apt.wicd.net intrepid Release.gpg                                         
Ign http://apt.wicd.net intrepid/extras Translation-en_GB                            
Ign http://ppa.launchpad.net intrepid/main Packages                                  
Hit http://gb.archive.ubuntu.com intrepid-updates Release                            
Hit http://archive.canonical.com intrepid/partner Packages                           
Hit http://security.ubuntu.com intrepid-security/main Packages                       
Hit http://packages.medibuntu.org hardy/free Packages                                
Hit http://ppa.launchpad.net intrepid/main Packages                                  
Hit http://gb.archive.ubuntu.com intrepid/main Packages                              
Hit http://gb.archive.ubuntu.com intrepid/restricted Packages                        
Hit http://gb.archive.ubuntu.com intrepid/restricted Sources                         
Hit http://gb.archive.ubuntu.com intrepid/main Sources                               
Hit http://gb.archive.ubuntu.com intrepid/multiverse Sources                         
Hit http://security.ubuntu.com intrepid-security/restricted Packages                 
Hit http://security.ubuntu.com intrepid-security/restricted Sources                  
Hit http://security.ubuntu.com intrepid-security/main Sources                        
Hit http://security.ubuntu.com intrepid-security/multiverse Sources                  
Hit http://apt.wicd.net intrepid Release                                             
Hit http://packages.medibuntu.org hardy/non-free Packages                            
Hit http://gb.archive.ubuntu.com intrepid/universe Sources                           
Hit http://gb.archive.ubuntu.com intrepid/universe Packages                          
Hit http://gb.archive.ubuntu.com intrepid/multiverse Packages                        
Hit http://gb.archive.ubuntu.com intrepid-updates/main Packages                      
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Packages                
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Sources                 
Hit http://gb.archive.ubuntu.com intrepid-updates/main Sources                       
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Sources                 
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Sources                   
Hit http://security.ubuntu.com intrepid-security/universe Sources                    
Hit http://security.ubuntu.com intrepid-security/universe Packages                   
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Packages
Ign http://apt.wicd.net intrepid/extras Packages
Hit http://apt.wicd.net intrepid/extras Packages
Fetched 308B in 1s (193B/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9423A34CCA967634
W: You may want to run apt-get update to correct these problems

```

I don't know why I get the signature error, I haven't got any third party repo's except for wicd !

---

### Post by bapoumba on 2009-04-03
Please try to remove the ppa and the wicd repos and see if it helps.

---

### Post by paulhurleyuk on 2009-04-03
I added the keys using instructions [here]("http://ubuntuforums.org/showthread.php?t=1054906") and apt-get update ran without error, but the update window still shows lots of packages to remove

I commented out the ppa and wicd repo's and tried again, apt-get upate ran without problem again and the update window now only shows eight packages to update or so (although they're biggies like dpkg)

Thanks for the help....

Paul.

---

### Post by CdeSousaG on 2009-04-04
I'm having the same problem here. 

I haven't tried the method mentioned before by paulhurleyuk yet. I'll like to know the root cause. Does anyone have more info, explanation ?

Thanks for the info!

---

### Post by cabernet54 on 2009-04-04
This solved my problem:

[http://www.nabble.com/keys-td22878104.html](http://www.nabble.com/keys-td22878104.html)

:guitar:

---

### Post by collix on 2009-04-04
> Now, usually I don't even look at the list, luckily today I did.

I did not, and it wiped out half of my KDE apps. What now? The launchpad lists are updated fine.

Trying to run a dist-upgrade returns:

```
The following packages have been kept back:
  kdegraphics-strigi-plugins kdelibs-bin kdelibs5 kdepimlibs5

```

Trying to install one of these manually gives you an endless list of unmet dependencies (mostly, it asks for KDE 4.2 libs but only finds 4.1 ones)

Help!

---

### Post by bapoumba on 2009-04-04
@ paulhurleyuk: you're welcome, glad to see you got it to work :)
My own little advice, as it is my own little habit: I always keep commented extra or third party repos (such as ppa) on a daily basis. I just enable them to see if there is an upgrade to perform, or when I know there is one, when my system is already up to date.

@ collix: please disable every third party repo you have in your sources.list and run an update ```
sudo apt-get-update
```
Then ```
sudo apt-get install kubuntu-desktop
```
and see if it helps.

---

### Post by pickarooney on 2009-04-04
I enabled the backports in my sources.lst - the version of libanylyzer0 there is higher than the one in the normal repositories - and I was then able to reinstall kdebaselibs5 and associated programs.

---

### Post by collix on 2009-04-04
Thanks for your help guys. Commenting out the ppa's wasn't enough, but pasting in the backports' address did the trick. In fact, I'm downloading KDE 4.2 right now. I hope it'll work alright.

---

### Post by abn91c on 2009-04-04
you should be OK, your Kubntu is just updating itself to 4.2.x.x
and it jut removing and updating packages not needed, you may even see plasma taken oy but dont worry thats normal also, you just getting a newer version. Some of the plasmoids you using may not work, just add  the new widgets when done(like the weather, clock, etc..)

---

