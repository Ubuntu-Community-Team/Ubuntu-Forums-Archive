---
title: "unable to install OOo 3 on Ubuntu 8.10"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by cdouv on 2009-10-23
Hello

I run Ubuntu 8.10 on a Dell Inspiron 1525 laptop. I followed the directions in this tutorial [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml) in order to install OOo 3 (Interpid comes with 2.4). They are very simple and it seems that they have worked for everyone else but they didn't work for me :(

I followed the 2 steps and waited for the update button to show up but it didn't
Then I followed these instructions to do it on the command line (given as Comment #15 on the same link) :

sudo gedit /etc/apt/sources.list.d/openoffice.list
add
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

sudo apt-get update
sudo apt-get dist-upgrade 

(BTW, I noticed that the /etc/apt/sources.list.d/openoffice.list was empty before I edited it, which I didn't expect, but it does contain the line now)

The update button showed eventually but it wasn't about the OOo 3 

I guess that you'll ask me about the console output so here it is:

kostas@todeli:~$ sudo gedit /etc/apt/sources.list.d/openoffice.list
[sudo] password for kostas: 
kostas@todeli:~$ cat /etc/apt/sources.list.d/openoffice.list
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
kostas@todeli:~$ sudo apt-get update
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US         
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid/main Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release  
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid/restricted Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                                         
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages               
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid/multiverse Translation-en_US           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources              
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid-updates Release.gpg                    
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid Release
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid-updates Release  
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid/main Packages    
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid/main Sources
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid/universe Packages
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid/universe Sources
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid-updates/multiverse Sources
Reading package lists... Done
kostas@todeli:~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kostas@todeli:~$ 

What do you think about that?

---

### Post by Ian Clark on 2009-11-07
I'm having the same issue. It looks like OOo3 isn't in the intrepid repositories anymore.

---

### Post by Hagar Delest on 2009-11-07
Try the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

