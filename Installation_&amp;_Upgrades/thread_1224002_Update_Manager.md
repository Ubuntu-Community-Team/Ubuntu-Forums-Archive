---
title: "Update Manager"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by vchapman on 2009-07-26
My update manager no longer works. I click on Check and then I get the spinning wheel for ever. Is there a way to run this from a terminal window?

---

### Post by steveneddy on 2009-07-26
In terminal:

```
sudo apt-get update
```

let it run - then in terminal:

```
sudo apt-get upgrade
```

post anything that the terminal says you may need to do to get new packages.

---

### Post by vchapman on 2009-07-26
> **steveneddy said:**
> In terminal:

```
sudo apt-get update
```let it run - then in terminal:

Funny message here I think:

jean@jean-desktop:~$ sudo apt-get update
sudo: unable to resolve host jean-desktop
[sudo] password for jean: 
Ign [http://software.thinkgos.com](http://software.thinkgos.com) gadgets Release.gpg
Get:1 [http://packages.medibu](http://packages.medibu)




```
sudo apt-get upgrade
```post anything that the terminal says you may need to do to get new packages.

jean@jean-desktop:~$ sudo apt-get upgrade
sudo: unable to resolve host jean-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  base-files dbus dbus-x11 dhcp3-client dhcp3-common firefox firefox-3.0
  firefox-3.0-gnome-support firefox-gnome-support hal language-pack-en
  libdbus-1-3 libgnutls13 libhal-storage1 libhal1 libldap-2.4-2
  libnautilus-extension1 libnm-


This seems to be working ... I will let the download carry on and see what happens

Thanks for your help

---

### Post by mzakiy86 on 2009-07-28
Is there have any code or cammand in terminal to fix any problem in ubuntu?

When ran this command:

sudo apt-get update

all this appears in terminal:

Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Get:1 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]                  
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty Release.gpg                            
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty/main Translation-en_US                 
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Translation-en_US            
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                       
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty/universe Translation-en_US             
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty/multiverse Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US           
Get:3 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release [14.2kB]          
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates Release.gpg                
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates/main Translation-en_US     
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates/universe Translation-en_US 
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty Release                            
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.7kB]                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates Release                        
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty/restricted Packages                    
Get:5 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Packages [1245B]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty/main Sources                           
Get:6 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Sources [37B]              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty/restricted Sources           
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty/universe Packages            
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty/universe Sources             
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty/multiverse Packages          
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty/multiverse Sources           
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates/main Packages        
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates/restricted Packages  
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates/main Sources         
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates/restricted Sources   
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates/universe Packages    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                     
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates/universe Sources     
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Fetched 15.9kB in 14s (1078B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A6DCF7707EBC211F
W: You may want to run apt-get update to correct these problems

---

### Post by Vernunft on 2009-07-28
Hello everyone. Althought i'm using Xubuntu 7.10 for the second time, i'm still a complete newbie, so i need some help. The first time i installed Xubuntu everything went fine, but this time (with the same live CD) one error as occorred during the install, something about being impossible to install the security updates.
And now, everytime i try to upgrade my distro to LTS 8.04 an error occurs and it fails.
I went to Software Sources, clicked the Update Maneger tab and all the options about the security updates are unavailable. 

I would me really appreciated if someone could help me on this one.
regards.

p.s.: i wanna upgrade, because theoretically it's better, is it really recommended to upgrade? is 8.04 much better than 7.10.
If the difference isn't that big, or if the 8.04 version is slower than the 7.10, i'll probably not upgrade, but still i would be much more rested if i had the security update problem fixed. thanks

---

