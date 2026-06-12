---
title: "uninstalling flash?"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by On Boards on 2009-09-23
hello , i'm trying to remove adobe flash from my pc .. 

when i enter the add/remove menu i get this message 


> This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.then in terminal 


> mohammed@mohammed-laptop:~$ sudo apt-get update
[sudo] password for mohammed: 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages          
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release [49.6kB]  
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security Release [49.6kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources                     
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages [178kB]        
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources [50.6kB]        
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages [56.0kB]   
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources [14.9kB]    
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages [8128B]  
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources [2505B]  
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Packages [101kB]      
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Sources [26.2kB]      
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Packages [35.7kB] 
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Sources [7109B]   
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Packages [1662B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Sources [588B]  
Fetched 582kB in 23s (24.9kB/s)                                                
Reading package lists... Done```


mohammed@mohammed-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  adobe-flashplugin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 10.2MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 44 files and directories currently installed.)
Removing adobe-flashplugin ...
dpkg: error processing adobe-flashplugin (--remove):
 cannot remove `/.': Invalid argument
E: Sub-process /usr/bin/dpkg returned an error code (1)
mohammed@mohammed-laptop:~$ 

```thanks

---

### Post by wojox on 2009-09-23
Try:

```
sudo dpkg --remove -force --force-remove-reinstreq flash
```

---

### Post by On Boards on 2009-09-24
thanks , can you re check the code ? ```



Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
mohammed@mohammed-laptop:~$ 
```

---

### Post by On Boards on 2009-09-24
pump :)

---

