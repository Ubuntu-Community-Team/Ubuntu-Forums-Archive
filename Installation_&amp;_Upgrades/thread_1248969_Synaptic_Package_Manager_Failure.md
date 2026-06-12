---
title: "Synaptic Package Manager Failure"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by patmartha on 2009-08-24
I have a Software Failure on a new machine that seemed to be working fine.  Can anyone help.  


When I open Synaptic Package Manager, I receive the following error,

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

When I run add/remove program, I receive this error,

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.


After running /etc/apt/sources.list I get

patmartha@system76-pc:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied


After running sudo apt-get install -f in the terminal I get

patmartha@system76-pc:~$ sudo apt-get install -f
[sudo] password for patmartha: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.



If I run cat /etc/apt/sources.list

patmartha@system76-pc:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse


The command sudo apt-get update results in the following.   

patmartha@system76-pc:~$ sudo apt-get update
Get:1 [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg [189B]                   
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg [189B]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_US                 
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_US          
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                   
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release.gpg [189B]             
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Translation-en_US
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release [74.6kB]              
Get:6 [http://planet76.com](http://planet76.com) ./ Release.gpg [197B]                                
Ign [http://planet76.com](http://planet76.com) ./ Translation-en_US                                   
Hit [http://planet76.com](http://planet76.com) ./ Release                                             
Ign [http://planet76.com](http://planet76.com) ./ Packages                                            
Hit [http://planet76.com](http://planet76.com) ./ Packages                                            
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release [49.6kB]                
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release [49.6kB]               
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages [1251kB]                  
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages [8858B]            
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources [3156B]             
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources [555kB]                   
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Sources [107kB]             
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Sources [2375kB]              
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages [4732kB]             
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages [189kB]            
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Packages [147kB]          
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Packages [2594B]    
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Sources [623B]      
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Sources [43.8kB]          
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Sources [1661B]     
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Sources [14.5kB]      
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Packages [47.9kB]     
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Packages [5026B]    
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Packages [79.1kB]        
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Packages [2594B]   
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Sources [623B]     
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Sources [23.0kB]         
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Sources [588B]     
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Sources [7109B]      
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Packages [28.7kB]    
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Packages [1538B]   
Fetched 9802kB in 28min 58s (5639B/s)                                          
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by tuxxy on 2009-08-24
Load Synaptic and did you click fix broken packages option first?

---

### Post by stlsaint on 2009-08-24
to repair a broken package its best to load into recovery mode and select "repair broken packages". and dont just use /etc/apt/menu.lst....thats why you got a permission denied....u must use sudo in front of it and if you want to edit use nano or gedit so it looks like this....

sudo gedit /etc/apt/menu.lst

---

### Post by Partyboi2 on 2009-08-24
Hi, open a terminal and remove the bad file and then download it again
```
 
sudo rm /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_ binary-amd64_Packages


```
```
 
sudo apt-get update

```

---

### Post by patmartha on 2009-08-25
> **tuxxy said:**
> Load Synaptic and did you click fix broken packages option first?


I can't get into synaptic at all, so I can't use the fix broken packages option.

---

### Post by patmartha on 2009-08-25
> **Partyboi2 said:**
> Hi, open a terminal and remove the bad file and then download it again
```
 
sudo rm /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_ binary-amd64_Packages


``````
 
sudo apt-get update

```


This did not work.  Here's what I got

patmartha@system76-pc:~$ sudo rm /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_ binary-amd64_Packages
[sudo] password for patmartha: 
rm: cannot remove `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_': No such file or directory
rm: cannot remove `binary-amd64_Packages': No such file or directory
patmartha@system76-pc:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
Hit [http://planet76.com](http://planet76.com) ./ Release.gpg                                         
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Ign [http://planet76.com](http://planet76.com) ./ Translation-en_US                         
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_US    
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg [189B]    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_US  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release.gpg            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Translation-en_US 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Translation-en_US
Hit [http://planet76.com](http://planet76.com) ./ Release                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://planet76.com](http://planet76.com) ./ Packages            
Hit [http://planet76.com](http://planet76.com) ./ Packages            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Translation-en_US     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release                                   
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release [49.6kB]                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Sources                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages                       
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Packages [147kB]           
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Packages [2594B]     
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Sources [623B]       
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Sources [43.8kB]           
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Sources [1661B]      
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Sources [14.5kB]       
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Packages [47.9kB]      
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Packages [5026B]    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Packages              
Fetched 313kB in 1min 32s (3376B/s)                                            
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by patmartha on 2009-08-25
> **stlsaint said:**
> to repair a broken package its best to load into recovery mode and select "repair broken packages". and dont just use /etc/apt/menu.lst....thats why you got a permission denied....u must use sudo in front of it and if you want to edit use nano or gedit so it looks like this....

sudo gedit /etc/apt/menu.lst


This didn't work either.  I went into recovery mode and selected "repair broken packages and I got the same error message.  

I wasn't sure where you wanted me to use sudo gedit /etc/apt/menu.lst.  If I use it in the terminal, some sort of document pops up that I don't know how to use?


Anymore thoughts?

---

### Post by patmartha on 2009-08-28
> **Partyboi2 said:**
> Hi, open a terminal and remove the bad file and then download it again
```
 
sudo rm /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_ binary-amd64_Packages


``````
 
sudo apt-get update

```


This was the answer
type this - sudo rm /var/lib/apt/lists/* -vf

[COLOR=#888888]  [/COLOR]then type this - sudo apt-get update

thanks for your help on the way

---

