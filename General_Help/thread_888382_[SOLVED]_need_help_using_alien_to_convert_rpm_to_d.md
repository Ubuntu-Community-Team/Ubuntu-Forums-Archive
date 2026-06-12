---
title: "[SOLVED] need help using alien to convert rpm to deb (new ubuntu user)"
date: 2008-08-13
forum: General Help
---

### Post by gorillastrong 2 on 2008-08-13
i'm trying to put adobe reader on my linux ubuntu 8.04. It comes as a rpm package and i used synaptic to get alien to try and convert it and it appears as follows....also need help converting for VMware player

josh@josh-laptop:~$ sudo alien --scripts '/home/josh/Desktop/AdobeReader_enu-8.1.2_SU1-1.i486.rpm' 
mkdir: cannot create directory `AdobeReader_enu-8.1.2_SU1': File exists
unable to mkdir AdobeReader_enu-8.1.2_SU1:  at /usr/share/perl5/Alien/Package.pm line 257.
josh@josh-laptop:~$ 

want to learn and have been up and down lookin for solutions.

---

### Post by Elfy on 2008-08-13
You can get adobe from the repos, it is in medibuntu. If you haven't installed that repo yet, do the following in a terminal - enter after each line. I assume you have version hardy/8.04 - if not get the correct repo from

[https://help.ubuntu.com/community/Medibuntu#Adding](https://help.ubuntu.com/community/Medibuntu#Adding) the Repositories

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo apt-get install acroread
```

---

### Post by gorillastrong 2 on 2008-08-13
k, tried that but looks like its saying it failed to retrieve from the site

josh@josh-laptop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
[sudo] password for josh: 
--02:44:10--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

100%[====================================>] 226           --.--K/s             

02:44:10 (19.29 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [226/226]

josh@josh-laptop:~$ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
josh@josh-laptop:~$ sudo apt-get install acroread
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package acroread has no installation candidate
josh@josh-laptop:~$ 



if this works thats cool, but any ideas or corrections for me with the "mkdir" error when i try with alien?

---

### Post by Elfy on 2008-08-13
Medibuntu has been a bit hit and miss lately, it's working now.

To use alien I have just done as you, never had a problem so can't answer, I would say though that you might be better of waiting as converting an rpm isn't always the best answer.

---

### Post by jocko on 2008-08-13
Don't install packages that were made for another distro, unless you are *absolutely* sure nothing else works. Chances are they are compiled with dependencies that are not available in the repos.
Try to run "sudo apt-get update" again, maybe the medibuntu repo was temporarily unavailable (I've noticed that it's sometimes exremely slow and sometimes completely down, but most of the time it works).

If you by some reason can't get a connection to medibuntu: Adobe does provide a .deb, so there's absolutely no reason for using a redhat package (check their [download page]("http://www.adobe.com/products/acrobat/readstep2_allversions.html"), select the .deb in the "Select an Installer" pull-down menu.

---

### Post by Elfy on 2008-08-13
> Adobe does provide a .deb, Thanks - I couldn't find that - not been up long enough :)

---

### Post by gorillastrong 2 on 2008-08-13
yea but i get the same error message with the VMware player installation

josh@josh-laptop:~$ sudo alien --scripts '/home/josh/Desktop/VMware-player-2.0.4-93057.i386.rpm' 
[sudo] password for josh: 
mkdir: cannot create directory `VMwarePlayer-2.0.4': File exists
unable to mkdir VMwarePlayer-2.0.4:  at /usr/share/perl5/Alien/Package.pm line 257.
josh@josh-laptop:~$ 


or where do i find the proper VMware package, bec i'm eventually gonna need it for my zune...only piece of MS holding me back

---

### Post by angry_johnnie on 2008-08-13
maybe

```
sudo alien -dc name-of-package.rpm
```

or, with [this]("http://ubuntuforums.org/showthread.php?t=311255") (just replace **~/.gnome2/nautilus-scripts/alien-this** with **gedit ~/.gnome2/nautilus-scripts/alien-this**)

Or you could just wait a while and see if Medibuntu starts working. :-)

As for vmware, I *think* that was available from Canonical's repository (check under third party repos).

---

### Post by WRDN on 2008-08-13
Type:

```
sudo alien -d [name].rpm
```

This should be entered in the terminal, and will convert the rpm to a debian package.

---

### Post by Elfy on 2008-08-13
There is info on the vmware here, never used it myself as I prefer vbox - which has a version in the repos or you can get the other version fromthem (which I do)

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

You need to really try and find things in deb, source, other order really.

The vbox deb is here
[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

there is a ubuntu 8.04 version available

---

### Post by gorillastrong 2 on 2008-08-13
> **forestpixie said:**
> There is info on the vmware here, never used it myself as I prefer vbox - which has a version in the repos or you can get the other version fromthem (which I do)

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

You need to really try and find things in deb, source, other order really.

The vbox deb is here
[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

there is a ubuntu 8.04 version available


thanks for the links...just a couple more questions (appreciate the quick response btw). will do my best to find deb files from now on.

1) most embarrassing...where are the repos? is it in the "partner repos" of the forums?

2) dealing with my Zune
[http://www.zune-online.com/news/zune/zune-on-linux-via-vmware.html](http://www.zune-online.com/news/zune/zune-on-linux-via-vmware.html)
refers to use VMware...but would it be ok to use vbox and still lower the usb to 1.1 and be ok? or does it have to be a specific virtual machine? seems everywhere people keep sayin VMware.

---

### Post by Elfy on 2008-08-13
First the easy one - I have no idea about zune - I don't have any mp3 players at all :) I had a quick look at the link you gave, vmware might have usb1.1 but vbox as long as you get the version form the sun link I gave you should be usb2.0

Second - repos are easily accessed from System >Admin> Software Sources. On the first page have restricted, main, universe and multiverse enabled - disable cdrom. On the partner tab - enable partners, on the 3rd party tab you should already have medibuntu enabled.

Once you've done that close and it will ask to reload - let it although it might have problem with medibuntu again.

Then you should have access to many, many programs - Add/Remove is a small version of synaptic.

If you have problems with those things - start a new thread.

Good luck

---

### Post by gorillastrong 2 on 2008-08-13
will do, lol i'll put in the beginner section too. Thx for the help

---

