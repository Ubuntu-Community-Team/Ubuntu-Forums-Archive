---
title: "I'm having trouble detecting ZSNES on my synaptic."
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by fidgetyacolyte on 2009-03-09
I want to install ZSNES on my Dell Mini 9 Ubuntu laptop running Hardy.

I keep reading that the best way to install anything is via Synaptic, however, I have a feeling that I do not have adequate repositories or something to that effect.

When I search for ZSNES in synaptic, it says no packages found.

So... I added a repository that supposedly had it and still no luck.  Anyways, here is my sources file:

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy restricted universe main multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security restricted main universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates restricted main universe multiverse
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse

when I run "sudo apt-get install zsnes" I also get nothing.

Any help would be appreciated.  Is it possible that Dell has put restrictions on my repositories?

---

### Post by pytheas22 on 2009-03-09
It should be there, but it's possible that your sources list is out of date for some reason.  Try running this command to fix that:
```

sudo apt-get update
```

Then run:
```

sudo apt-get install zsnes
```

again to install zsnes.  Does it work?  If not, please post the output of these commands:
```

apt-cache search zsnes
uname -rm
```

Another option would be to download the package manually from [http://packages.ubuntu.com/hardy/zsnes](http://packages.ubuntu.com/hardy/zsnes), save it to your desktop and double-click to install.  But using the repositories is the preferred method.

---

### Post by Partyboi2 on 2009-03-09
Looking at [http://dell-mini.archive.canonical.com/ubuntu/pool/universe/z/zsnes/](http://dell-mini.archive.canonical.com/ubuntu/pool/universe/z/zsnes/) there is no deb package.
But [http://us.archive.ubuntu.com/ubuntu/pool/universe/z/zsnes/](http://us.archive.ubuntu.com/ubuntu/pool/universe/z/zsnes/) has a deb package. So what You could do is manually download it from [http://us.archive.ubuntu.com/ubuntu/pool/universe/z/zsnes/](http://us.archive.ubuntu.com/ubuntu/pool/universe/z/zsnes/) and install it.

---

### Post by fidgetyacolyte on 2009-03-11
Maybe the problem lies in this...

I ran:

sudo apt-get update

This is the output:

```
 http://security.ubuntu.com hardy-security Release.gpg [189B]
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US        
Hit http://us.archive.ubuntu.com hardy Release.gpg                                
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US               
Hit http://archive.ubuntu.com hardy Release.gpg                                   
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US                  
Hit http://packages.medibuntu.org hardy Release.gpg                               
Ign http://packages.medibuntu.org hardy/free Translation-en_US                    
Ign http://security.ubuntu.com hardy-security/main Translation-en_US              
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US          
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US        
Get:2 http://security.ubuntu.com hardy-security Release [58.5kB]                  
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US                 
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US                     
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US               
Get:3 http://us.archive.ubuntu.com hardy-updates Release.gpg [189B]               
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US       
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US             
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US         
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US       
Hit http://archive.ubuntu.com hardy Release                                       
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US                
Hit http://packages.medibuntu.org hardy Release                                   
Hit http://us.archive.ubuntu.com hardy Release                                    
Get:4 http://us.archive.ubuntu.com hardy-updates Release [58.5kB]                 
Ign http://archive.ubuntu.com hardy/multiverse Packages                           
Hit http://packages.medibuntu.org hardy/free Packages                             
Err http://archive.ubuntu.com hardy/multiverse Packages                           
  404 Not Found [IP: 91.189.88.31 80]
Hit http://packages.medibuntu.org hardy/non-free Packages                         
Ign http://security.ubuntu.com hardy-security/restricted Packages                 
Ign http://us.archive.ubuntu.com hardy/restricted Packages                        
Ign http://us.archive.ubuntu.com hardy/universe Packages                 
Ign http://us.archive.ubuntu.com hardy/main Packages                     
Ign http://us.archive.ubuntu.com hardy/multiverse Packages               
Ign http://security.ubuntu.com hardy-security/main Packages              
Ign http://security.ubuntu.com hardy-security/universe Packages          
Ign http://security.ubuntu.com hardy-security/multiverse Packages                 
Ign http://us.archive.ubuntu.com hardy-updates/restricted Packages                
Ign http://us.archive.ubuntu.com hardy-updates/main Packages                      
Ign http://us.archive.ubuntu.com hardy-updates/universe Packages                  
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Packages                
Err http://us.archive.ubuntu.com hardy/restricted Packages                        
  404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy/universe Packages                          
  404 Not Found [IP: 91.189.88.40 80]
Err http://security.ubuntu.com hardy-security/restricted Packages                 
  404 Not Found
Err http://security.ubuntu.com hardy-security/main Packages                       
  404 Not Found
Err http://us.archive.ubuntu.com hardy/main Packages                              
  404 Not Found [IP: 91.189.88.40 80]
Err http://security.ubuntu.com hardy-security/universe Packages                   
  404 Not Found
Err http://us.archive.ubuntu.com hardy/multiverse Packages                        
  404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-updates/restricted Packages                
  404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-updates/main Packages             
  404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-updates/universe Packages         
  404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-updates/multiverse Packages       
  404 Not Found [IP: 91.189.88.40 80]
Err http://security.ubuntu.com hardy-security/multiverse Packages        
  404 Not Found
Hit http://dell-mini.archive.canonical.com hardy Release.gpg             
Ign http://dell-mini.archive.canonical.com hardy/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-updates Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-updates/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-security Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-security/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-netbook-base Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy Release
Hit http://dell-mini.archive.canonical.com hardy-updates Release
Hit http://dell-mini.archive.canonical.com hardy-security Release
Hit http://dell-mini.archive.canonical.com hardy-netbook-base Release
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release
Hit http://dell-mini.archive.canonical.com hardy/main Packages                    
Hit http://dell-mini.archive.canonical.com hardy/universe Packages                
Hit http://dell-mini.archive.canonical.com hardy/multiverse Packages              
Hit http://dell-mini.archive.canonical.com hardy/restricted Packages              
Hit http://dell-mini.archive.canonical.com hardy/main Sources                     
Hit http://dell-mini.archive.canonical.com hardy/universe Sources                 
Hit http://dell-mini.archive.canonical.com hardy/multiverse Sources               
Hit http://dell-mini.archive.canonical.com hardy/restricted Sources               
Hit http://dell-mini.archive.canonical.com hardy-updates/main Packages            
Hit http://dell-mini.archive.canonical.com hardy-updates/universe Packages        
Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Packages      
Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Packages      
Hit http://dell-mini.archive.canonical.com hardy-updates/main Sources             
Hit http://dell-mini.archive.canonical.com hardy-updates/universe Sources         
Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Sources       
Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Sources       
Hit http://dell-mini.archive.canonical.com hardy-security/main Packages           
Hit http://dell-mini.archive.canonical.com hardy-security/universe Packages       
Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Packages     
Hit http://dell-mini.archive.canonical.com hardy-security/restricted Packages     
Hit http://dell-mini.archive.canonical.com hardy-security/main Sources            
Hit http://dell-mini.archive.canonical.com hardy-security/universe Sources        
Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Sources      
Hit http://dell-mini.archive.canonical.com hardy-security/restricted Sources      
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages       
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages   
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages 
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages 
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources        
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources    
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources  
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources  
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages          
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages      
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages    
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages    
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources           
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources       
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources     
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources     
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages       
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages   
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages 
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages 
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources        
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources    
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources  
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources  
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages          
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages      
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages    
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages    
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources           
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources       
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources     
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources     
Fetched 117kB in 7s (15.6kB/s)                                                    
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz  404 Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz  404 Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Then I ran sudo apt-get install zsnes, here is the output:

```
 sudo apt-get install zsnes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package zsnes

```

Any ideas?

---

### Post by pytheas22 on 2009-03-11
I don't know why it's failing to fetch some of the archives.  But a manual work-around would be to download [this file]("http://us.archive.ubuntu.com/ubuntu/pool/universe/z/zsnes/zsnes_1.510-2.2ubuntu2_i386.deb"), save it to your desktop and double-click to install.  That should work; if not, let us know.

---

### Post by fidgetyacolyte on 2009-03-11
That worked beautifully... although now I'm a little bit concerned about this repository issue.  I was really excited about having all the programs available in one place easy to download.  Oh well, I suppose thats a problem for another section.

Thanks a ton!

---

### Post by pytheas22 on 2009-03-11
I'm glad that worked.  I'm still not sure why you have problems updating the sources list.  It's possible that it's just a temporary issue with Ubuntu's servers, and that you'd have better luck running 'sudo apt-get update' tomorrow.  It might also help to choose a different mirror by going to System>Administration>Software Sources and, under the 'Ubuntu Software' tab, change the "Download from" option.

If you want a clean Hardy sources list, this is mine:

```
#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

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
```

You could give that a try too, although I'm not sure whether it would be compatible with the Dell Mini.  Also remember to backup your current list first if you want to give mine a try.

---

### Post by Partyboi2 on 2009-03-11
There is no binary-lpia section in the ubuntu repository.
> W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/[COLOR=Red]binary-lpia[/COLOR]/Packages.gz]("http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz")  404 Not Found
At a guess I would say that is why their are the dell mini repositories. My suggestion would be to disable all the other repos except the dell-mini ones.

---

### Post by fidgetyacolyte on 2009-03-12
Any ideas on how to get apt-get update to look at the correct link?

Or how to get it to ignore the binary-lpia section?

---

### Post by Partyboi2 on 2009-03-12
Open a terminal (Applications>Accessories>Terminal) and backup you current sources.list
```
sudo cp /etc/apt/sources/list /etc/apt/sources.list.broken
```
then open your sources.list
```
gksu gedit /etc/apt/sources.list
``` delete the contents of the file and replace with:
```
deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
```
Then save the changes and close gedit. Then back in the terminal
```
sudo apt-get update
```

---

### Post by fidgetyacolyte on 2009-03-12
Changing my sources list to those above corrected my errors, however, I believe it restricts me to only Third Party software offered by Dell.  

When I go into my Software Sources, my Ubuntu Software tab has all 4 boxes unchecked (restricted, multiverse, universe, main).  I'm assuming this is where the majority of the software I'd want will be located, but with the aforementioned sources list, this software is not available.  If I check these boxes, I start getting the errors again, where the updater is looking in the wrong location.

With the sources above, I am not able to "sudo apt-get install zsnes" because it cannot find any packages related to zsnes.  These packages do exist, no?

Granted, I've only been on Ubuntu about a week now, so I might have no idea what I'm talking about.

---

### Post by Partyboi2 on 2009-03-12
If you look at the two respotories side by side majority of the the packages in the Ubuntu repo are avialable in the dell ones. Zsnes is in the dell repo the only problem is that the source code is provide but no deb package, that is why 'sudo apt-get install zsnes' returns no package available.

---

### Post by pytheas22 on 2009-03-13
From what I gather (I did some research because I was curious), the reason the Dell Mini archives are missing some packages is that not all packages were built for the [lpia processor architecture]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2007-August/000332.html"), which the Mini apparently uses.  Although it's possible to install and run regular i386 packages with no problems, it seems that Ubuntu will only include packages built specifically for lpia in the Mini repositories.

You're probably best off sticking with the Mini repositories rather than trying to use the generic ones, since the software in the Mini repositories is optimized for your system.  In cases where a particular package is not available, you should still always be able to download it from [http://packages.ubuntu.com](http://packages.ubuntu.com) and install manually.

I don't know why no one has built a package for ZSNES optimized for lpia yet, but my guess is that the code won't compile with the lpia-specific flags, hence why you only have the ZSNES source code in the Mini repository, not a binary.

Someone else may be able to clarify this stuff better; these are just my observations based on a few minutes on Google trying to figure out why the Mini repositories are different from the standard ones.

---

### Post by fidgetyacolyte on 2009-03-13
Well, as long as I have most of what I need!  If I have trouble finding something, I'll just google it!

Thank you all for your help!  Ubuntu is just getting better and better thanks to you guys.

---

