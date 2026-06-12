---
title: "no pubkey?"
date: 2008-09-06
forum: General Help
---

### Post by douggiephresh on 2008-09-06
[http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783


what does this mean and what do i have to do?

---

### Post by drs305 on 2008-09-06
The way to include the Medibuntu repository changed with the introduction of Hardy. If you used old commands to add it the medibuntu.list may not be correct. The following will install  the Medibuntu Repository following the guidance from [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu"). 

These commands will restore the medibuntu repository and add the correct public key.

```

sudo mv /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list-old 
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

---

### Post by douggiephresh on 2008-09-06
i am new to this and have no idea what you just said

---

### Post by douggiephresh on 2008-09-06
i am trying to install AWN and keep getting this message when i get to this step

doug@doug-laptop:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) hardy Release.gpg                            
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [189B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources                               
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) hardy/avant-window-navigator Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release.gpg                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Translation-en_US  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Translation-en_US    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                 
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) hardy Release                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Translation-en_US  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) hardy/avant-window-navigator Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources            
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) hardy/avant-window-navigator Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources                    
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) hardy/avant-window-navigator Packages        
  404 Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages   
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) hardy/avant-window-navigator Sources
  404 Not Found
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [9335B]            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Packages           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Fetched 190B in 1s (110B/s)
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/hardy/avant-window-navigator/binary-amd64/Packages.gz](http://download.tuxfamily.org/syzygy42/dists/hardy/avant-window-navigator/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/hardy/avant-window-navigator/source/Sources.gz](http://download.tuxfamily.org/syzygy42/dists/hardy/avant-window-navigator/source/Sources.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
doug@doug-laptop:~$



This happens at around step 8 of this instructional
[http://linuxondesktop.blogspot.com/2007/12/making-your-ubuntu-look-like-mac-os-x.html](http://linuxondesktop.blogspot.com/2007/12/making-your-ubuntu-look-like-mac-os-x.html)

---

### Post by LonelyTraveler on 2008-09-07
It seem like there are a few people having this problem. I'm having the same problem. I've even restored my repository to the original one (like it was upon installation of hardy) but I still have the same problem.

That makes it sound like it is not user error right? I'm hitting a brick wall here so if anyone figures it out please let us know.

Thanks.

---

### Post by drs305 on 2008-09-07
> **LonelyTraveler said:**
> It seem like there are a few people having this problem. I'm having the same problem. I've even restored my repository to the original one (like it was upon installation of hardy) but I still have the same problem.

That makes it sound like it is not user error right? I'm hitting a brick wall here so if anyone figures it out please let us know.

Thanks.

I just deleted my medibuntu keyring and references to the medibuntu repositories. I then ran the three lines from post #2. Aside from a message saying it could not get the public key, the public key WAS installed and all the other commands worked correctly, including 'sudo apt-get update'. I then successfully downloaded an app from the medibuntu repository.

Adding the medibuntu repository changed earlier this year. If you haven't updated things it may be the reason for the errors. Running the commands in #2 may solve things if you haven't run them already.

---

### Post by LonelyTraveler on 2008-09-07
> **drs305 said:**
> I just deleted my medibuntu keyring and references to the medibuntu repositories. I then ran the three lines from post #2. Aside from a message saying it could not get the public key, the public key WAS installed and all the other commands worked correctly, including 'sudo apt-get update'. I then successfully downloaded an app from the medibuntu repository.

Adding the medibuntu repository changed earlier this year. If you haven't updated things it may be the reason for the errors. Running the commands in #2 may solve things if you haven't run them already.

Cool, my problem is not with mediubuntu though (i don't even know what that is!) it is just with the standard repositories.

---

### Post by drs305 on 2008-09-07
> **LonelyTraveler said:**
> Cool, my problem is not with mediubuntu though (i don't even know what that is!) it is just with the standard repositories.
> **douggiephresh said:**
> 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Fetched 190B in 1s (110B/s)
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/hardy/avant-window-navigator/binary-amd64/Packages.gz](http://download.tuxfamily.org/syzygy42/dists/hardy/avant-window-navigator/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/hardy/avant-window-navigator/source/Sources.gz](http://download.tuxfamily.org/syzygy42/dists/hardy/avant-window-navigator/source/Sources.gz)  404 Not Found


At some point you must have enabled the medibuntu repository, as you are getting an error message from it.

Your main problem appears to be with the tuxfamily repository. I have gone to their repository and the only distribution currently in the 'syzygy42/dists' directory is for feisty. For whatever reason, there is not longer a 'hardy' subfolder, which is why you are getting the errors.

---

### Post by LonelyTraveler on 2008-09-07
> **drs305 said:**
> At some point you must have enabled the medibuntu repository, as you are getting an error message from it.

Your main problem appears to be with the tuxfamily repository. I have gone to their repository and the only distribution currently in the 'syzygy42/dists' directory is for feisty. For whatever reason, there is not longer a 'hardy' subfolder, which is why you are getting the errors.

Sorry, my bad. I didn't make my situation clear. This is the output I get:

```
W: GPG error: http://security.ubuntu.com hardy-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://archive.ubuntu.com hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://archive.ubuntu.com hardy-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
```

Not with mediubuntu, but I also have the no pubkey problem. I take it it is because of what you just said. So I guess it is a waiting game until get get fixed.

What is mediubuntu by the way?

---

### Post by drs305 on 2008-09-07
> **LonelyTraveler said:**
> Sorry, my bad. I didn't make my situation clear. 

Close synaptic, run this, then restart it or run 'sudo apt-get update' and see if your problem is fixed:
```
sudo apt-get install ubuntu-keyring
```

Here is a link to [http://www.medibuntu.org/]("http://www.medibuntu.org/") It maintains a lot of multimedia packages - one of the most popular being GoogleEarth.

---

### Post by LonelyTraveler on 2008-09-07
> **drs305 said:**
> Close synaptic, run this, then restart it or run 'sudo apt-get update' and see if your problem is fixed:
```
sudo apt-get install ubuntu-keyring
```

Here is a link to [http://www.medibuntu.org/]("http://www.medibuntu.org/") It maintains a lot of multimedia packages - one of the most popular being GoogleEarth.

Thanks, but already installed.

---

### Post by LonelyTraveler on 2008-09-07
I just did something that I already tried, but this time it worked.

I cleared my sources.list file and ran apt-get update. Then I went to Software Sources and checked the things that was checked (everything except hardy-proposed and backports) ran apt-get update again and now everthing is perfect.

Tells me it was just a problem on the servers or whatever. Thanks for the help!

---

### Post by LonelyTraveler on 2008-09-08
I'm back with the same problem. I've pin pointed the problem to the Hardy Recommended Updates. As soon as I check that I get this problem:

Code:

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

I also have problem with Wine. When I add the key and repository at stated on [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) this is what I get:

Code:

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/hardy/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/hardy/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)

E: Some index files failed to download, they have been ignored, or old ones used instead.

Any ideas?

Thanks.

---

### Post by zvacet on 2008-09-08
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by LonelyTraveler on 2008-09-09
> **zvacet said:**
> ```
sudo apt-get update && sudo apt-get upgrade
```

Thanks but I still get this:
```

W: GPG error: http://archive.ubuntu.com hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```

---

### Post by drs305 on 2008-09-09
> **LonelyTraveler said:**
> Thanks but I still get this:


The option I haven't mentioned is this: Make sure the synaptic, repository section (hardy-updates) you are getting the error message is ticked/selected; then to go to synaptic, settings, repositories, authentication tab. "Remove" the Ubuntu Archive Automatic Signing Key and then hit the "Restore Defaults" button. 

If you still get the error message posting your sources.list is the only recourse that comes to mind.

---

### Post by LonelyTraveler on 2008-09-09
> **drs305 said:**
> The option I haven't mentioned is this: Make sure the synaptic, repository section (hardy-updates) you are getting the error message is ticked/selected; then to go to synaptic, settings, repositories, authentication tab. "Remove" the Ubuntu Archive Automatic Signing Key and then hit the "Restore Defaults" button. 

If you still get the error message posting your sources.list is the only recourse that comes to mind.

Thanks but no luck. My sources.list:

```
deb http://archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted

deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted
```

---

### Post by drs305 on 2008-09-11
Via PM LonelyTraveler was able to fix his/her problem. Here is the contents of that PM:

Sorry we can't get this figured out for you. My last shot: replace (by commenting out) your 2 'hardy-updates' lines wit the following, which are the ones I use and which are currently using the key generated with the Restore button:

deb [http://www.gtlib.gatech.edu/pub/ubuntu/](http://www.gtlib.gatech.edu/pub/ubuntu/) hardy-updates restricted multiverse universe main

deb-src [http://www.gtlib.gatech.edu/pub/ubuntu/](http://www.gtlib.gatech.edu/pub/ubuntu/) hardy-updates restricted multiverse universe main

Just for the record, here are the other lines in mine:

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe

deb-src [http://www.gtlib.gatech.edu/pub/ubuntu/](http://www.gtlib.gatech.edu/pub/ubuntu/) hardy-security restricted main multiverse universe

deb [http://www.gtlib.gatech.edu/pub/ubuntu/](http://www.gtlib.gatech.edu/pub/ubuntu/) hardy restricted multiverse universe main

deb-src [http://www.gtlib.gatech.edu/pub/ubuntu/](http://www.gtlib.gatech.edu/pub/ubuntu/) hardy restricted multiverse universe main

These are all from the Georgia Tech mirror in Atlanta, GA, USA

---

