---
title: "problems with sudo apt-get update command"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by neodudecurt on 2009-06-04
hey guys, I installed Ubuntu yesterday, and when I tried to do the sudo apt-get update, this is all that I got:

curtis@curtis-laptop:~$ sudo apt-get update
[sudo] password for curtis: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Translation-en_US                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Translation-en_US              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Translation-en_US      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Translation-en_US    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_US              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages                       
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg                         
  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Translation-en_US
  Unable to connect to packages.freecontrib.org http:
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Translation-en_US
  Unable to connect to packages.freecontrib.org http:
W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg)  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_US.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_US.bz2)  Unable to connect to packages.freecontrib.org http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
curtis@curtis-laptop:~$ 



Every single time I run the command it stops exactly at the same spot. I was wondering if that was something I should be worried about, and whether there was a way to fix it

---

### Post by logos34 on 2009-06-04
what a mes--dapper and jaunty mixed together (?)...try to a different server location (synaptic>settings>repos>ubuntu sw>'download from'

also, can't run update from command line while synaptic is open...close it first

---

### Post by raymondh on 2009-06-04
That and/or go to your sources list (system > administration > software sources) and untick dapper repos .... leaving jaunty repos ticked (except the CD), specially "main".

How did you upgrade to 9.04?

@ logos ... good job on the ladydonna thread :)

Regards,

---

### Post by logos34 on 2009-06-04
> **raymondhenson said:**
> 
@ logos ... good job on the ladydonna thread :)


yeah, a real epic...Little did I know what I was getting into :rolleyes:...

if only the Bios would boot grub on the USB directly...

---

### Post by raymondh on 2009-06-04
> **logos34 said:**
> yeah, a real epic...Little did I know what I was getting into :rolleyes:...

if only the Bios would boot grub on the USB directly...

Sorry for the quick hijack neodudcurt ...

logos, I am thinking cylinder limit.  Also, the 200mb may be an OEM-placed partition (not the recovery) such as an EID or something.  My dell that came with a dock had that.  Anyway, good job.  I wish we could see a gparted shot as well as a bootinfo script.  I know it seems complicated but it'll help visualize and read what that darn grub is doing.

OK ... back to the thread, sorry neo....

@ neo, any results after closing synaptic and running the command thru terminal (success or errors)?

---

