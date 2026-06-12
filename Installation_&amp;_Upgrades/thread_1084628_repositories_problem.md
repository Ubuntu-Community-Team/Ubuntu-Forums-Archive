---
title: "repositories problem"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by keedaiit on 2009-03-02
when i am trying ti upgrade my system using syanptic package manager.
i am always getting the same reply.
i want to make it clear i am using proxy and its working clearly.

WARNING: The following packages cannot be authenticated!
  libbeecrypt6 libneon25 librpm4 python-elementtree python-celementtree
  python-urlgrabber rpm python-rpm yum
Install these packages without verification [y/N]? y
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) gutsy/main libbeecrypt6 4.1.2-6build1
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/main libbeecrypt6 4.1.2-6build1
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/main libneon25 0.25.5.dfsg-6build1
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/main librpm4 4.4.1-14.1ubuntu2
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/universe python-elementtree 1.2.6-11ubuntu1
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/universe python-celementtree 1.0.5-9
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/universe python-urlgrabber 3.1.0-3
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/main rpm 4.4.1-14.1ubuntu2
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/universe python-rpm 4.4.1-14.1ubuntu2
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/universe yum 2.4.0-3.1
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/b/beecrypt/libbeecrypt6_4.1.2-6build1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/b/beecrypt/libbeecrypt6_4.1.2-6build1_i386.deb)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/n/neon/libneon25_0.25.5.dfsg-6build1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/n/neon/libneon25_0.25.5.dfsg-6build1_i386.deb)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/r/rpm/librpm4_4.4.1-14.1ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/r/rpm/librpm4_4.4.1-14.1ubuntu2_i386.deb)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/e/elementtree/python-elementtree_1.2.6-11ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/e/elementtree/python-elementtree_1.2.6-11ubuntu1_all.deb)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/c/celementtree/python-celementtree_1.0.5-9_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/c/celementtree/python-celementtree_1.0.5-9_i386.deb)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/u/urlgrabber/python-urlgrabber_3.1.0-3_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/u/urlgrabber/python-urlgrabber_3.1.0-3_all.deb)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/r/rpm/rpm_4.4.1-14.1ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/r/rpm/rpm_4.4.1-14.1ubuntu2_i386.deb)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/r/rpm/python-rpm_4.4.1-14.1ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/r/rpm/python-rpm_4.4.1-14.1ubuntu2_i386.deb)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/y/yum/yum_2.4.0-3.1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/y/yum/yum_2.4.0-3.1_all.deb)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by taurus on 2009-03-02
From synaptic, click Settings -> Repositories and use another server.  Don't forget to click the Reload button once you have switched to another server.  Use the Main Server if you can't decide which one to use.

---

### Post by keedaiit on 2009-03-02
i am using the main server.i am using evrything correctly.i dunno whats wrong.wait
also when i am trying to upgrade using synaptic upgrader i am getting following error.

Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-backports/restricted/source/Sources.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-backports/restricted/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Some index files failed to download, they have been ignored, or old ones used instead.

Edit : Output clipped. @ [keedaiit]("http://ubuntuforums.org/member.php?u=691677") : Use attachments for posting long output like that. Attach the output as a text file.

It is the same error over and over and over, we do not need to see it repeated 500 times :)

---

### Post by taurus on 2009-03-02
Are you running gutsy or hardy because you have both in your /etc/apt/sources.list?

```
lsb_release -a
```
Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by keedaiit on 2009-03-02
the output for sources.list is 

Edit : Output clipped. @ [keedaiit]("http://ubuntuforums.org/member.php?u=691677") : Use attachments for posting long output like that. Attach the output as a text file.


and the one for lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 8.04.1
Release:    8.04
Codename:    hardy
 
what are the lsb modules?

---

### Post by taurus on 2009-03-02
You need to edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and put a # in front of the first line to comment out the cdrom option.

```
**[COLOR="Blue"]#[/COLOR]**deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
```
Then, replace the word **gutsy** with **hardy** for all the repos in there since you are running hardy.

Also, remove the last two lines.

```

[B][COLOR="Red"]deb http://Ubuntu 5.10 "Breezy Badger" (Binary)
deb http://wine.sourceforge.net/apt/ binary/[/COLOR][/B]

```
Save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by blackened on 2009-03-02
Wow, what a mess. Did you edit /etc/apt/sources.list by hand?

For future reference, it is sometimes ok to mix repos meant for different versions (sometimes even different distributions), but that should also be one of the first things you look at when apt goes sideways (depending on what it complains about, obviously).

---

### Post by keedaiit on 2009-03-02
problems more problems.........


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

E: Some index files failed to download, they have been ignored, or old ones used instead.
  
well from next time the code you ask me to run.......please also tell what they do if you don't mind

Edit : Output clipped. @ [keedaiit]("http://ubuntuforums.org/member.php?u=691677") : Use attachments for posting long output like that. Attach the output as a text file.

It is the same error over and over and over, we do not need to see it repeated 500 times :)

---

### Post by keedaiit on 2009-03-02
problems more problems.........

Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy-updates/restricted Packages                    
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Ign [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-proposed/main Packages                         
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy-security/main Packages                         
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Ign [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-proposed/multiverse Packages                   
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy-security/universe Packages                     
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Ign [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-proposed/restricted Packages                   
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy-security/multiverse Packages                   
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Ign [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-proposed/universe Sources                      
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy-security/restricted Packages                   
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Ign [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-proposed/main Sources                          
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy-backports/main Packages                        
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy-backports/universe Packages                    
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy-backports/multiverse Packages                  
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy-backports/restricted Packages                  
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Ign [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-proposed/multiverse Sources                    
Ign [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-proposed/restricted Sources                    
Ign [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-backports/universe Packages                    
Ign [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-backports/main Packages                        
Ign [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-backports/multiverse Packages                  
Ign [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-backports/restricted Packages                  
Ign [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-backports/universe Sources                     
Ign [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-backports/main Sources                         
Ign [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-backports/multiverse Sources                   
Ign [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-backports/restricted Sources                   
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy/main Packages                                  
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy/universe Packages                              
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy/restricted Packages                            
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy/multiverse Packages                            
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy/main Sources                                   
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy/universe Sources                               
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy/restricted Sources                             
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy/multiverse Sources                             
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-security/universe Sources                      
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-security/main Sources                          
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-security/multiverse Sources                    
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-security/restricted Sources                    
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-updates/universe Packages                      
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-updates/main Packages                          
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-updates/multiverse Packages                    
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-updates/restricted Packages                    
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-updates/universe Sources                       
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-updates/main Sources                           
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-updates/multiverse Sources                     
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-updates/restricted Sources                     
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-proposed/universe Packages                     
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-proposed/main Packages                         
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-proposed/multiverse Packages                   
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-proposed/restricted Packages                   
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-proposed/universe Sources                      
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-proposed/main Sources                          
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-proposed/multiverse Sources                    
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-proposed/restricted Sources                    
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-backports/universe Packages                    
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-backports/main Packages                        
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-backports/multiverse Packages                  
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-backports/restricted Packages                  
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-backports/universe Sources                     
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-backports/main Sources                         
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-backports/multiverse Sources                   
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Err [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-backports/restricted Sources                   
  407 Proxy Authentication Required [IP: 10.94.0.32 3128]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy Release.gpg                             c
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/main Translation-en_IN                  
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) hardy Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_IN               
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/restricted Translation-en_IN            
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) hardy/avant-window-navigator Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) hardy Release                                
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Translation-en_IN              
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) hardy/avant-window-navigator Packages        
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Translation-en_IN            
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) hardy/avant-window-navigator Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates Release.gpg              
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) hardy/avant-window-navigator Packages        
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Translation-en_IN   
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) hardy/avant-window-navigator Sources         
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy Release    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/multiverse Sources
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/main Packages
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/restricted Packages
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Sources
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Sources
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Packages
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Sources
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Packages
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Sources
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Packages
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Packages
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Sources
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Sources
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Packages
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Sources
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Packages
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Sources
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/main Packages
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/restricted Packages
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/universe Packages
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/multiverse Packages
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/main Sources
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/restricted Sources
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/universe Sources
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/multiverse Sources
  407 Proxy Authentication Required [IP: 10.94.0.31 3128]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://ftp.utexas.edu/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](http://ftp.utexas.edu/ubuntu/dists/hardy/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz](http://ftp.utexas.edu/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz](http://ftp.utexas.edu/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy/main/source/Sources.gz](http://ftp.utexas.edu/ubuntu/dists/hardy/main/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy/universe/source/Sources.gz](http://ftp.utexas.edu/ubuntu/dists/hardy/universe/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy/restricted/source/Sources.gz](http://ftp.utexas.edu/ubuntu/dists/hardy/restricted/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy/multiverse/source/Sources.gz](http://ftp.utexas.edu/ubuntu/dists/hardy/multiverse/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-security/universe/source/Sources.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-security/universe/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-security/main/source/Sources.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-security/main/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-backports/main/binary-i386/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-backports/main/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-security/multiverse/source/Sources.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-security/multiverse/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-security/restricted/source/Sources.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-security/restricted/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-backports/multiverse/binary-i386/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-backports/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-backports/restricted/binary-i386/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-backports/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-updates/universe/source/Sources.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-updates/universe/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-updates/main/source/Sources.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-updates/main/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-updates/restricted/source/Sources.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-updates/restricted/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-proposed/universe/binary-i386/Packages.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-proposed/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-proposed/main/binary-i386/Packages.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-proposed/main/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-proposed/multiverse/binary-i386/Packages.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-proposed/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-proposed/restricted/binary-i386/Packages.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-proposed/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-proposed/universe/source/Sources.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-proposed/universe/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-proposed/main/source/Sources.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-proposed/main/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-proposed/multiverse/source/Sources.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-proposed/multiverse/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-proposed/restricted/source/Sources.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-proposed/restricted/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-backports/main/binary-i386/Packages.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-backports/main/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-backports/multiverse/binary-i386/Packages.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-backports/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-backports/restricted/binary-i386/Packages.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-backports/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-backports/universe/source/Sources.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-backports/universe/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-backports/main/source/Sources.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-backports/main/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-backports/multiverse/source/Sources.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-backports/multiverse/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy-backports/restricted/source/Sources.gz](http://ftp.utexas.edu/ubuntu/dists/hardy-backports/restricted/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.32 3128]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/hardy/avant-window-navigator/binary-i386/Packages.gz](http://download.tuxfamily.org/syzygy42/dists/hardy/avant-window-navigator/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/hardy/partner/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/hardy/avant-window-navigator/source/Sources.gz](http://download.tuxfamily.org/syzygy42/dists/hardy/avant-window-navigator/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/source/Sources.gz)  407 Proxy Authentication Required [IP: 10.94.0.31 3128]

E: Some index files failed to download, they have been ignored, or old ones used instead.
  
well from next time the code you ask me to run.......please also tell what they do if you don't mind

---

### Post by blackened on 2009-03-02
lsb_relase -a just prints the version of Ubuntu you're running.

You've got something seriously out of whack. Please post your current sources.list.

---

### Post by silverglade00 on 2009-03-02
407 Proxy Authentication Required [IP: 10.94.0.31 3128]

This is telling you what the issue is. A 10.x.x.x address is normally an internal network. It is asking you to authenticate to a web proxy. Do you normally have to log into something to access the Internet? That would be the first place to check. Your sources.list is(was) probably fine. It's the network connection that it is using that needs to be checked.

---

### Post by keedaiit on 2009-03-03
indeed  i use proxy .i need to log on to the proxy server to access the internet.
but i am able to access internet very easily...like i am doing now!!!!!!!!1
dunno what the problem is
laso when i am trying to download using synaptic i am getting this error failed to fetch from ubntu pool etc........

---

