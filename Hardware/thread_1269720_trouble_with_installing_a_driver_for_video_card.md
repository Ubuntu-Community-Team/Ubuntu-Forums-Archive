---
title: "trouble with installing a driver for video card"
date: 2009-09-18
forum: Hardware
---

### Post by hyburn on 2009-09-18
Ubuntu HH

hey folks, I recently got a new computer 

I have sudo apt-get update. and it give me this
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release.gpg
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_CA
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_CA
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release             
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages       
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages 
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages       
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages 
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy Release.gpg                                            
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Translation-en_CA                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                                            
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_CA                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_CA                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_CA                    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Translation-en_CA                           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Translation-en_CA                             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Translation-en_CA                           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates Release.gpg                                    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Translation-en_CA                         
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Translation-en_CA                   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Translation-en_CA                     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Translation-en_CA                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy Release                                                
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_CA                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                                      
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg                                      
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_CA                           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                                
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Packages                                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Packages                                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Sources                                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Sources                                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Packages                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Sources              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Packages           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Sources            
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Packages         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Sources      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages
W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.




Can someone help me? im off for a coffee, I'll be back in 30. leave on and I will respond immediately

best regards

---

### Post by utnubuuser on 2009-09-18
What's the problem?  Is the CD in the drawer?  Are you trying to use the CD as the source?
If not, go to System>>Administration>>Synaptic Package Manager>>Settings>>Repositories>>Third Party Software and check or uncheck the box for CDrom

What driver are you wanting to install?  For which card?  Output of > lspci

---

### Post by hyburn on 2009-09-18
yes the CD is in the drive bay. I unchecked the CD as a repository. still no dice on the issue

this is what I get from input: sudo dpkg -i xorg-driver-fglrx-8.593-0ubuntu1_i386.deb fglrx-kernal-source-8.593-0ubuntu1_i836.deb fglrx-amdcccle_8.593-0ubuntu1_i386.deb

```
dpkg: error processing xorg-driver-fglrx-8.593-0ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fglrx-kernal-source-8.593-0ubuntu1_i836.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fglrx-amdcccle_8.593-0ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xorg-driver-fglrx-8.593-0ubuntu1_i386.deb
 fglrx-kernal-source-8.593-0ubuntu1_i836.deb
 fglrx-amdcccle_8.593-0ubuntu1_i386.deb
```

I think I somehow I now have i686. is that why this is not working? FFS can someone help me fix my system please?

---

### Post by Yellow Pasque on 2009-09-20
It looks like you have an internet connection, so just install the driver following: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

If you're still having issues with warnings/errors from apt-get, then post your /etc/apt/sources.list file.

---

### Post by hyburn on 2009-09-20
it tells me something about not having an installation candidate; restricted-manager

Should I do a fresh install of linux? im trying to convert drivers for an intel to an asus compatible boot. should I say "hell with it"' and do a fresh install?

---

