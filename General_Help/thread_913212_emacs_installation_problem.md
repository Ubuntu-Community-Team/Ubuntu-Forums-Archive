---
title: "emacs installation problem"
date: 2008-09-07
forum: General Help
---

### Post by Kalidor on 2008-09-07
When I try to install emacs (the current version in the reps), both with kubuntu and ubuntu 8.04, it downloads it fine but then when it's time to configure adept freaks out and sticks the infamous "could not commit changes..." error

---

### Post by Kalidor on 2008-09-08
.

---

### Post by aloshbennett on 2008-09-08
It might help if you do an apt-get update before the install

---

### Post by Rocket2DMn on 2008-09-08
Please update/upgrade and try forcing install.
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f
```
Then try to install emacs again if the last command doesn't do it.  Please post any unusual output back here.

---

### Post by Kalidor on 2008-09-08
I tried to purge emacs and then reinstall. I also tried sudo dpkg --configure -a, but it returns

Setting up emacsen-common (1.4.17) ...
emacsen-common: Handling install of emacsen flavor emacs
install-info: No dir file specified; try --help for more information.
dpkg: error processing emacsen-common (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:


There's no way out of this error message

---

### Post by Rocket2DMn on 2008-09-08
Try cleaning out your cache first, that will force the .deb install file to be re-downloaded, it's possible it is corrupted.
```
sudo apt-get clean
```
Then try installing again.

---

### Post by Kalidor on 2008-09-08
done. Useless.

---

### Post by Rocket2DMn on 2008-09-08
> **Kalidor said:**
> done. Useless.

What happens if you just install the package "emacs"?

---

### Post by Kalidor on 2008-09-08
That's when the problem first arose. It makes an error while configuring emacsen-common and stops. It's just something peculiar of trying to install emacs. I'm using kde4.1

---

### Post by Kalidor on 2008-09-08
just so i can be precise if i try to install it through konsole this is the output.


Reading package lists... Done                     
Building dependency tree                          
Reading state information... Done                 
The following extra packages will be installed:   
  emacs22-bin-common emacs22-common emacsen-common
Suggested packages:                               
  emacs22-el                                      
The following NEW packages will be installed:     
  emacs22-bin-common emacs22-common emacs22-gtk emacsen-common
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 21.0MB of archives.                               
After this operation, 68.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y                                   
Get:1 [http://ubuntu.inode.at](http://ubuntu.inode.at) hardy/main emacsen-common 1.4.17 [17.6kB]
Get:2 [http://ubuntu.inode.at](http://ubuntu.inode.at) hardy-updates/main emacs22-common 22.1-0ubuntu10.1 [18.6MB]
Get:3 [http://ubuntu.inode.at](http://ubuntu.inode.at) hardy-updates/main emacs22-bin-common 22.1-0ubuntu10.1 [182kB]                                                                                         
Get:4 [http://ubuntu.inode.at](http://ubuntu.inode.at) hardy-updates/universe emacs22-gtk 22.1-0ubuntu10.1 [2209kB] 
Fetched 21.0MB in 26s (789kB/s)                                                           
Selecting previously deselected package emacsen-common.                                   
(Reading database ... 106421 files and directories currently installed.)                  
Unpacking emacsen-common (from .../emacsen-common_1.4.17_all.deb) ...                     
Selecting previously deselected package emacs22-common.                                   
Unpacking emacs22-common (from .../emacs22-common_22.1-0ubuntu10.1_all.deb) ...           
Selecting previously deselected package emacs22-bin-common.
Unpacking emacs22-bin-common (from .../emacs22-bin-common_22.1-0ubuntu10.1_amd64.deb) ...
Selecting previously deselected package emacs22-gtk.
Unpacking emacs22-gtk (from .../emacs22-gtk_22.1-0ubuntu10.1_amd64.deb) ...
Setting up emacsen-common (1.4.17) ...
emacsen-common: Handling install of emacsen flavor emacs
install-info: No dir file specified; try --help for more information.
dpkg: error processing emacsen-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of emacs22-common:
 emacs22-common depends on emacsen-common (>= 1.4.10); however:
  Package emacsen-common is not configured yet.
dpkg: error processing emacs22-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of emacs22-bin-common:
 emacs22-bin-common depends on emacs22-common (= 22.1-0ubuntu10.1); however:
  Package emacs22-common is not configured yet.
dpkg: error processing emacs22-bin-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of emacs22-gtk:
 emacs22-gtk depends on emacs22-bin-common (= 22.1-0ubuntu10.1); however:
  Package emacs22-bin-common is not configured yet.
dpkg: error processing emacs22-gtk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 emacsen-common
 emacs22-common
 emacs22-bin-common
 emacs22-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Rocket2DMn on 2008-09-08
OK, it's possible that the mirror you are using has missing dependencies or the package that was synced there is corrupt.  I suggest switching repositories (however this is done in KDE), make sure it updates the list when you close (or run apt-get update), clean the cache again, then try one more time to install.

---

### Post by Kalidor on 2008-09-08
Same problem. I guess something is broken in my system but everything else installs and works fine. I wonder how to get to use emacs as I really need it.

---

### Post by Rocket2DMn on 2008-09-08
Alright, let's start from the top by removing all the emacs stuff, cleaning the cache, updating, upgrading, checking dpkg, and reinstalling.  Please run and post the output of the following commands (just copy and paste the whole terminal here in [ code ] [ /code ] tags w/out the spaces):
```
sudo apt-get remove --purge emacs
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
dpkg -s emacs
sudo apt-get install -f
sudo apt-get install emacs
```
I can't do anything else without seeing more output.

---

### Post by Kalidor on 2008-09-08
```

joubert@ubuntu:~$ sudo apt-get remove --purge emacs
Reading package lists... Done                      
Building dependency tree                           
Reading state information... Done                  
Package emacs is not installed, so not removed     
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
joubert@ubuntu:~$ sudo apt-get autoremove                     
Reading package lists... Done                                 
Building dependency tree                                      
Reading state information... Done                             
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
joubert@ubuntu:~$ sudo apt-get clean
joubert@ubuntu:~$ sudo apt-get update
Hit http://archive.canonical.com hardy Release.gpg                  
Ign http://archive.canonical.com hardy/partner Translation-en_US    
Ign http://ppa.launchpad.net hardy Release.gpg                      
Ign http://ppa.launchpad.net hardy/main Translation-en_US            
Hit http://ftp.crihan.fr hardy Release.gpg                           
Ign http://ftp.crihan.fr hardy/main Translation-en_US                
Hit http://archive.canonical.com hardy Release                       
Get:1 http://ppa.launchpad.net hardy Release [27.6kB]                
Ign http://ftp.crihan.fr hardy/restricted Translation-en_US          
Ign http://ftp.crihan.fr hardy/universe Translation-en_US            
Ign http://ftp.crihan.fr hardy/multiverse Translation-en_US          
Hit http://ftp.crihan.fr hardy-updates Release.gpg                   
Ign http://ftp.crihan.fr hardy-updates/main Translation-en_US        
Ign http://ftp.crihan.fr hardy-updates/restricted Translation-en_US  
Ign http://ftp.crihan.fr hardy-updates/universe Translation-en_US    
Ign http://ftp.crihan.fr hardy-updates/multiverse Translation-en_US  
Hit http://ftp.crihan.fr hardy-security Release.gpg                  
Ign http://ppa.launchpad.net hardy/main Packages                     
Hit http://archive.canonical.com hardy/partner Packages              
Ign http://ftp.crihan.fr hardy-security/main Translation-en_US       
Ign http://ftp.crihan.fr hardy-security/restricted Translation-en_US 
Ign http://ftp.crihan.fr hardy-security/universe Translation-en_US   
Ign http://ftp.crihan.fr hardy-security/multiverse Translation-en_US 
Hit http://ftp.crihan.fr hardy Release                               
Hit http://ftp.crihan.fr hardy-updates Release                                           
Hit http://ppa.launchpad.net hardy/main Packages                                         
Hit http://archive.canonical.com hardy/partner Sources                                   
Hit http://ftp.crihan.fr hardy-security Release                                          
Hit http://ftp.crihan.fr hardy/main Packages                                             
Hit http://ftp.crihan.fr hardy/restricted Packages                                       
Hit http://ftp.crihan.fr hardy/main Sources                                              
Hit http://ftp.crihan.fr hardy/restricted Sources                                        
Hit http://ftp.crihan.fr hardy/universe Packages                                         
Hit http://ftp.crihan.fr hardy/universe Sources                                          
Hit http://ftp.crihan.fr hardy/multiverse Packages                                       
Hit http://ftp.crihan.fr hardy/multiverse Sources                                        
Hit http://ftp.crihan.fr hardy-updates/main Packages                                     
Hit http://ftp.crihan.fr hardy-updates/restricted Packages                               
Hit http://ftp.crihan.fr hardy-updates/main Sources                                      
Hit http://ftp.crihan.fr hardy-updates/restricted Sources                                
Hit http://ftp.crihan.fr hardy-updates/universe Packages                                 
Hit http://ftp.crihan.fr hardy-updates/universe Sources                                  
Hit http://ftp.crihan.fr hardy-updates/multiverse Packages                               
Hit http://ftp.crihan.fr hardy-updates/multiverse Sources                                
Hit http://ftp.crihan.fr hardy-security/main Packages                                    
Hit http://ftp.crihan.fr hardy-security/restricted Packages                              
Hit http://ftp.crihan.fr hardy-security/main Sources                                     
Hit http://ftp.crihan.fr hardy-security/restricted Sources                               
Hit http://ftp.crihan.fr hardy-security/universe Packages                                
Hit http://ftp.crihan.fr hardy-security/universe Sources                                 
Hit http://ftp.crihan.fr hardy-security/multiverse Packages                              
Hit http://ftp.crihan.fr hardy-security/multiverse Sources                               
Fetched 1B in 2s (0B/s)                                                                  
Reading package lists... Done                                                            
joubert@ubuntu:~$ sudo apt-get upgrade                                                   
Reading package lists... Done                                                            
Building dependency tree                                                                 
Reading state information... Done                                                        
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.                           
joubert@ubuntu:~$ dpkg -s emacs                                                          
Package: emacs                                                                           
Status: purge ok not-installed                                                           
Priority: optional                                                                       
Section: editors                                                                         
joubert@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done            
Building dependency tree                 
Reading state information... Done        
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
joubert@ubuntu:~$ sudo apt-get install emacs                  
Reading package lists... Done                                 
Building dependency tree                                      
Reading state information... Done                             
The following extra packages will be installed:               
  emacs22-bin-common emacs22-common emacs22-gtk emacsen-common
Suggested packages:                                           
  emacs22-el                                                  
The following NEW packages will be installed:                 
  emacs emacs22-bin-common emacs22-common emacs22-gtk emacsen-common
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.      
Need to get 21.0MB of archives.                                     
After this operation, 68.4MB of additional disk space will be used. 
Do you want to continue [Y/n]? y                                    
Get:1 http://ftp.crihan.fr hardy/main emacsen-common 1.4.17 [17.6kB]
Get:2 http://ftp.crihan.fr hardy-updates/main emacs22-common 22.1-0ubuntu10.1 [18.6MB]
Get:3 http://ftp.crihan.fr hardy-updates/main emacs22-bin-common 22.1-0ubuntu10.1 [182kB]
Get:4 http://ftp.crihan.fr hardy-updates/universe emacs22-gtk 22.1-0ubuntu10.1 [2209kB]  
Get:5 http://ftp.crihan.fr hardy-updates/main emacs 22.1-0ubuntu10.1 [6338B]             
Fetched 21.0MB in 44s (474kB/s)                                                          
Selecting previously deselected package emacsen-common.                                  
(Reading database ... 106461 files and directories currently installed.)                 
Unpacking emacsen-common (from .../emacsen-common_1.4.17_all.deb) ...                    
Selecting previously deselected package emacs22-common.                                  
Unpacking emacs22-common (from .../emacs22-common_22.1-0ubuntu10.1_all.deb) ...          
Selecting previously deselected package emacs22-bin-common.                              
Unpacking emacs22-bin-common (from .../emacs22-bin-common_22.1-0ubuntu10.1_amd64.deb) ...
Selecting previously deselected package emacs22-gtk.                                     
Unpacking emacs22-gtk (from .../emacs22-gtk_22.1-0ubuntu10.1_amd64.deb) ...              
Selecting previously deselected package emacs.                                           
Unpacking emacs (from .../emacs_22.1-0ubuntu10.1_all.deb) ...                            
Setting up emacsen-common (1.4.17) ...                                                   
emacsen-common: Handling install of emacsen flavor emacs                                 
install-info: No dir file specified; try --help for more information.                    
dpkg: error processing emacsen-common (--configure):                                     
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of emacs22-common:
 emacs22-common depends on emacsen-common (>= 1.4.10); however:
  Package emacsen-common is not configured yet.
dpkg: error processing emacs22-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of emacs22-bin-common:
 emacs22-bin-common depends on emacs22-common (= 22.1-0ubuntu10.1); however:
  Package emacs22-common is not configured yet.
dpkg: error processing emacs22-bin-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of emacs22-gtk:
 emacs22-gtk depends on emacs22-bin-common (= 22.1-0ubuntu10.1); however:
  Package emacs22-bin-common is not configured yet.
dpkg: error processing emacs22-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of emacs:
 emacs depends on emacs22-gtk | emacs22 | emacs22-nox; however:
  Package emacs22-gtk is not configured yet.
  Package emacs22 is not installed.
  Package emacs22-gtk which provides emacs22 is not configured yet.
  Package emacs22-nox is not installed.
dpkg: error processing emacs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 emacsen-common
 emacs22-common
 emacs22-bin-common
 emacs22-gtk
 emacs
E: Sub-process /usr/bin/dpkg returned an error code (1)
joubert@ubuntu:~$

```
I had already purged emacs from adept when i executed these tasks

---

### Post by Rocket2DMn on 2008-09-08
Well this is rather emabarassing, I can't seem to figure out what is wrong, other than the .deb installer being corrupt.  You can try downloading that particular deb package from the main repository and manually installing it - [http://packages.ubuntu.com/hardy/emacsen-common](http://packages.ubuntu.com/hardy/emacsen-common)
After you install that, you can try cleaning your cache again, then attempting to install emacs.

If that doesn't work, I would clean the cache, restart the computer, then just wait awhile.  You may want to try to main server rather than another mirror if you decide keep trying.

---

### Post by Kalidor on 2008-09-08
Well thanks for your time anyway. I guess I'll try to install emacs thru a normal procedure (make)

---

### Post by inetfish on 2008-11-01
To people who come into this page when seeking for help

when i encountered this problem , i cannot install any *-doc.deb package.
in my case, it was an installation of texlive2008.iso to blame
it got /usr/sbin/install-info overridden by its own version located in /usr/local/bin

And, thank you, Kalidor !

---

