---
title: "3D Acceleration on 5450 HD Radeon under 14.04"
date: 2015-07-25
forum: Hardware
---

### Post by Simon_Tomoko on 2015-07-25
I have this card installed on my desktop and would like to get the 3D acceleration working as well as it does in 12.04.

First a little about my rig. I am running two HDD both are 500Gb each and both partitioned with Linux Kubuntu in a dual boot of 12.04 (the original system) and 14.04 on the other HDD (brand new, not an upgrade).  I have both Linux and Windows (under WINE) games that use 3D acceleration. To keep this simple I will only address the Linux games only.

So far, last weekend I ran a variety of games to test the 3D differences between 12.04 an 14.04. They are clear as night and day. Kubuntu 12.04 out performs 14.04 on all the tests. At present if you are into any kind of 3D accelerated gaming, I would recommend sticking with 12.04, I know it has "run its course" but I will stick with what works.

I ran my Linux versions Portal 1 and Portal 2, also tested Borderlands 2. These games run under 14.04 but all the videos ran like they were skipping frames and the game play lagged. Portal 2 kept crashing at the most inopportune moments. I had to readjust (lower) the settings for them to play in 14.04 which is sad for the newer "upgrade" to be this way. When I rebooted to my 12.04 the same games played from the same drive ran flawless.

The difference is the graphics drivers. I attempted to install the fglrx into my 14.04 and got this;


```
**$ sudo apt-get install fglrx**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 fglrx : Depends: dkms but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


**$ sudo apt-get install dkms**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 dkms : Depends: gcc but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


**$ sudo apt-get install gcc**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 gcc : Depends: gcc-4.8 (>= 4.8.2-5~) but it is not going to be installed
       Recommends: libc6-dev but it is not going to be installed or
                   libc-dev
E: Unable to correct problems, you have held broken packages.
```


Next I went to the AMD website and downloaded the deb packaged driver for 14.04 proprietary drivers. 

I was met with; 

[IMG]http://s3.postimg.org/dn3mrh2hv/snapshot7.png[/IMG][IMG]http://s28.postimg.org/cggtjukdp/snapshot8.png[/IMG]



Unless someone here has a rabbit in their hat, my opinion is 14.04 for work and internet surfing but games is much better on Precise 12.04 with the proprietary drivers.

---

### Post by deadflowr on 2015-07-25
Have you run a system update yet?

---

### Post by Simon_Tomoko on 2015-07-25
Yes 100%, here you can see that through "Additional Drivers" app, I have Catalyst installed on the 12.04.

[[IMG]http://s13.postimg.org/p5q6v8ilv/snapshot1.jpg[/IMG]]("http://postimg.org/image/p5q6v8ilv/") [[IMG]http://s1.postimg.org/ltgu06wgb/snapshot2.jpg[/IMG]]("http://postimg.org/image/ltgu06wgb/") [[IMG]http://s13.postimg.org/7d9813qr7/snapshot3.jpg[/IMG]]("http://postimg.org/image/7d9813qr7/")

While the information shows that mesa is running the show on the 14.04.

[[IMG]http://s4.postimg.org/oj5cr0621/snapshot0.jpg[/IMG]]("http://postimg.org/image/oj5cr0621/")

I have no real problems with mesa wanting to steal the show, but it lacks any hardware acceleration. Not to change the subject, but it feels as bad as; when they are pushing a junk audio app on us like Pulse Audio. I have no desire to be the lab rat. Thank you for your interest in my problems.

---

### Post by davidvandoren on 2015-07-25
I have the same card and had to find out that the newer kernel in 14.04 does not support this card any longer. 
The other way around ATI does not support this kernel. 

I installed Lubuntu 14.01 I guess and it let me install the proprietary driver which works. 
After that, I installed Ubuntu desktop and gnome shell classic. 

Find an older install medium with either Kubuntu, Lubuntu or Ubuntu and don't upgrade to 14.04

---

### Post by Simon_Tomoko on 2015-07-25
Thanks davidvandoren, I figured this was the issue. I am not bent on name brands but I suppose my next graphics card will have to be an Nvidia.  Meanwhile I will just keep the dual boot option I have available to me.

I have mixed emotions about it but I will mark this as "solved".

---

### Post by deadflowr on 2015-07-25
I asked if you were fully updated because the problem is not the driver.
The driver fully supports the card and the version of Ubuntu.

The problem is entirely a package management problem.

Perhaps post the terminal output for both
```
sudo apt-get update
sudo apt-get upgrade
```

I know Kubuntu's software updater can get iffy sometimes.

---

### Post by Yellow Pasque on 2015-07-25
> I have no real problems with mesa wanting to steal the show, but it lacks any hardware acceleration
False. Why does this feel like an nvidia shill?

---

### Post by Simon_Tomoko on 2015-07-25
@[COLOR=#000000]deadflowr: No problem.[/COLOR]

```
Ign http://dl.google.com stable InReleaseIgn http://security.ubuntu.com precise-security InRelease                      
Hit http://security.ubuntu.com precise-security Release.gpg                    
Hit http://dl.google.com stable Release.gpg                                    
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com precise-security Release                        
Ign http://archive.canonical.com precise InRelease                             
Ign http://archive.ubuntu.com trusty InRelease                                 
Hit http://dl.google.com stable Release                                        
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://archive.ubuntu.com trusty Release.gpg                               
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://security.ubuntu.com precise-security/main Sources                   
Hit http://archive.getdeb.net trusty-getdeb InRelease                          
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://security.ubuntu.com precise-security/restricted Sources             
Hit http://archive.ubuntu.com trusty Release                                   
Hit http://security.ubuntu.com precise-security/main i386 Packages             
Ign http://nl.archive.ubuntu.com precise-updates InRelease                     
Hit http://archive.canonical.com precise Release                               
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://security.ubuntu.com precise-security/restricted i386 Packages       
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit http://archive.getdeb.net trusty-getdeb/apps i386 Packages                 
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://nl.archive.ubuntu.com precise-updates Release.gpg                   
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://archive.ubuntu.com trusty/main i386 Packages                        
Hit http://archive.getdeb.net trusty-getdeb/games i386 Packages                
Hit http://nl.archive.ubuntu.com precise-updates Release                       
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://archive.ubuntu.com trusty/universe i386 Packages                    
Hit http://archive.canonical.com precise/partner i386 Packages                 
Hit http://nl.archive.ubuntu.com precise-updates/main Sources                  
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://archive.ubuntu.com trusty/multiverse i386 Packages                  
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://archive.canonical.com precise/partner Translation-en                
Hit http://nl.archive.ubuntu.com precise-updates/restricted Sources            
Ign http://dl.google.com stable/main Translation-en                            
Hit http://archive.ubuntu.com trusty/restricted i386 Packages                  
Hit http://nl.archive.ubuntu.com precise-updates/main i386 Packages            
Hit http://archive.ubuntu.com trusty/main Translation-en                       
Hit http://nl.archive.ubuntu.com precise-updates/restricted i386 Packages      
Hit http://nl.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://archive.ubuntu.com trusty/multiverse Translation-en                 
Hit http://nl.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://archive.ubuntu.com trusty/restricted Translation-en                 
Hit http://archive.ubuntu.com trusty/universe Translation-en                   
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en_US             
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en    
Ign http://archive.getdeb.net trusty-getdeb/games Translation-en_US
Ign http://archive.ubuntu.com trusty/main Translation-en_US        
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US  
Ign http://archive.getdeb.net trusty-getdeb/games Translation-en   
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US  
Ign http://archive.ubuntu.com trusty/universe Translation-en_US
Reading package lists... Done                                        

```

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Is that all you needed to know?

@[COLOR=#000000]Temüjin: Please read again, I don't have a Nvidia Shell card -- I know exactly what hardware I purchased, it is a Radeon 5450 HD.
   I thought screenshots would be sufficient but here is the output of lspci as well;
[/COLOR]```
lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series] [1002:68f9]

```
Also I can verify for a fact I don't have acceleration in the 14.04 OS.

[COLOR=#000000]Thank you for your continued interest in my problems.[/COLOR]

---

### Post by deadflowr on 2015-07-26
Interesting.
You seem to have mixed sources.
I'd recommend editing the the file /etc/apt/sources.list
and remove all entries concerning precise.

Something clearly didn't go right if this was an upgrade from 12.04 to 14.04, and those precise entries still show.

You need to be root to edit this file so either run
```
sudo nano /etc/apt/sources.list
```
to edit in a terminal editor
or, since this is Kubuntu
```
kdesudo kate /etc/apt/sources.list
```
to use the kate text editor to edit it.
then re-run the update/upgrade command again and see what happens.
If it's still up-to-date, then try installing the fglrx package again.

for fun, perhaps, you might post the output for this:
```
apt-cache policy gcc
```
since it's the gcc version which is causing the dkms package from installing, which in turn is causing fglrx package from installing.
even if you were to try to use an nvidia card and then tried to install nvidia-current (the nvidia driver package) you'd run into this same problem...

---

### Post by Simon_Tomoko on 2015-07-26
> [COLOR=#000000]Something clearly didn't go right if this was an upgrade from 12.04 to 14.04, and those precise entries still show.[/COLOR]

No this is a not an upgrade, I needed to add precise because Muon Software Manager won't allow for me to download my preferred version of GIMP 2.6. The repositories for 14.04 insist on upgrading my GIMP to 2.8. So yes I have some precise mixed but only for the GIMP;

Saved as /etc/apt/sources.list.d/precise-for-gimp.list
```
deb http://nl.archive.ubuntu.com/ubuntu/ precise-updates main restricteddeb-src http://nl.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
```

Saved as /etc/apt/sources.list.d/precise-for-gimp.list.save
```
deb http://nl.archive.ubuntu.com/ubuntu/ precise-updates main restricteddeb-src http://nl.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
```

I am not blowing my GIMP 2.6 off just to prove a point. Too much work getting it back up to 100% and lost too much artwork already.

apt-cache policy gcc
This is not a problem.
```
gcc:  Installed: (none)
  Candidate: 4:4.8.2-1ubuntu6
  Version table:
     4:4.8.2-1ubuntu6 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main i386 Packages

```

Once again, Thank you for your continued interest.

---

### Post by deadflowr on 2015-07-26
> [COLOR=#000000]I am not blowing my GIMP 2.6 off just to prove a point. Too much work getting it back up to 100% and lost too much artwork already.[/COLOR]

Yeah, and I surely do not want to do that either.
At this point I'm not sure it'd be worth it go further trying to fix fglrx.
Not without a slight chance of breaking gimp for you.

That said, there are several better methods to get older versions of software running in newer systems.

The first is an oldie but a goodie.
[Chroot]("https://help.ubuntu.com/community/BasicChroot")
pretty simple idea.

And another is relatively new
[LXC containers]("https://help.ubuntu.com/14.04/serverguide/lxc.html")

A primer on how to setup containers and a nice writeup here
[https://www.stgraber.org/2013/12/20/lxc-1-0-blog-post-series/](https://www.stgraber.org/2013/12/20/lxc-1-0-blog-post-series/)
and in particular for running gui apps here
[https://www.stgraber.org/2014/02/09/lxc-1-0-gui-in-containers/](https://www.stgraber.org/2014/02/09/lxc-1-0-gui-in-containers/)

Simply put either method will allow you to try out and run, what could be considered out-of-date software(or bleeding edge for that matter), isolated from the rest of the systems packages.
While still able to utilize the system's resources.

Not that any of this is in anyway helpful to the current situation.
Just something i thought about...

---

### Post by Simon_Tomoko on 2015-07-26
Thank again for all your efforts, and like I said before, unless I upgrade hardware, I will just dual boot 12.04 and 14.04 depending on my "mood". :D

---

