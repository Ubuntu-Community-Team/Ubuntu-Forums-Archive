---
title: "problem whith update &amp; install.."
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by m3asmi on 2009-05-17
I can't open the links in firefox & i can't open the Add/Del program  & I can't do update 
this is the message when I open the update applecation:

An insoluble problem appeared during the initialization of data packets.

Please report this error as a bug in the package "update-manager 'and include the following error message:

'E: Encountered a section with no Package: header E: Problem with MergeList / var / lib / dpkg / status, E: The package lists or file "status" can not be analyzed or read. "

---

### Post by hansdown on 2009-05-17
Hi m3asmi.

Try this.

Click applications> accessories> terminal.

Copy and paste this in the terminal.

```
sudo apt-get clean all
```

Enter your password; you won't see the letters as you type.

Just enter it and click enter.

Next, copy and paste this into the terminal.

```
sudo apt-get update
```

---

### Post by m3asmi on 2009-05-18
_**[FONT=&quot]I  see this message[/FONT]**_
[COLOR=Black][FONT=&quot]
[/FONT][/COLOR]
[COLOR=Black][FONT=&quot]m3asmi@XXX:~$ sudo apt-get clean all
m3asmi@XXX:~$ sudo apt-get update
Ign cdrom://[APTonCD for ubuntu gutsy - i386 (2007-11-22 14:21) CD1]  Release.gpg
Ign cdrom://[APTonCD for ubuntu gutsy - i386 (2007-11-22 14:21) CD1]  Translation-fr
Ign cdrom://[APTonCD for ubuntu gutsy - i386 (2007-11-22 14:21) CD1]  Release  
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-fr              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-fr        
Atteint [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-fr             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-fr       
Atteint [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                    
Atteint [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-fr            
Atteint [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-fr      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-fr  
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release              
Atteint [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                     
Atteint [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-fr                
Atteint [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-fr      
Atteint [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                
Atteint [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages       
Atteint [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                  
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages  
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources         
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources   
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages    
Atteint [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages         
Atteint [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages                    
Atteint [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages              
Atteint [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages            
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources     
Lecture des listes de paquets... Erreur !
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: Les listes de paquets ou le fichier « status » ne peuvent être analysés ou lus[/FONT][/COLOR]
[COLOR=Black][FONT=&quot]m3asmi@XXX:~$[/FONT][/COLOR]
[COLOR=Navy][FONT=&quot] 

 [/FONT][/COLOR]

---

### Post by hansdown on 2009-05-18
You have both gutsy and hardy repos.

Which version of ubuntu are you running?

Click system> about ubuntu> version and release numbers.

---

### Post by m3asmi on 2009-05-18
I have Ubuntu 8.04

---

### Post by hansdown on 2009-05-18
o.k.

Click applications> accessories> terminal.

Enter```
 sudo gedit /etc/apt/sources.list
```

Delete the three lines with gutsy.

Then, control+o to save.Then control+x to exit.

Then run ```
 sudo apt-get clean && sudo apt-get update
```

---

### Post by m3asmi on 2009-05-19
m3asmi @ XXX: ~ $ sudo gedit / etc / apt / sources.list  
 m3asmi @ XXX: ~ $ sudo apt-get clean & & sudo apt-get update  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / main Translation-fr  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / restricted Translation-fr  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-fr  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-fr  
 Achieved [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-fr  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-fr  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / universe Translation-fr  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / multiverse Translation-fr  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-fr  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release  
 Achieved [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / main Packages  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages  
 Achieved [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / restricted Packages  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / universe Packages  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / multiverse Packages  
 Achieved [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources  
 Reading package lists ... Mistake!  
 E: Encountered a section with no Package: header  
 E: Problem with MergeList / var / lib / dpkg / status  
 E: The package lists or file "status" can not be analyzed or read.  
 m3asmi @ XXX: ~ $

---

### Post by hansdown on 2009-05-19
Hi m3asmi.

I believe the answer is in this solved thread, but I need to look some

more.

[http://ubuntuforums.org/showthread.php?t=863742](http://ubuntuforums.org/showthread.php?t=863742)

There is more to look over, so I'll give you some more info.

[http://www.google.ca/search?q=E%3A+Encountered+a+section+with+no+Package%3A+header+&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=E%3A+Encountered+a+section+with+no+Package%3A+header+&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

Yes, run this in the terminal.

```
sudo rm /var/lib/apt/lists/* -vf
```

Then ```
sudo apt-get update
```

This will clear the packages that are the problem.

---

### Post by m3asmi on 2009-05-21
no chages 
this is the message
m3asmi @ XXXXX: ~ $ sudo rm / var / lib / apt / lists / *-vf  
 [sudo] password for m3asmi:  
 détruit `/ var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages'  
 détruit `/ var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_main_i18n_Translation-fr '  
 détruit `/ var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_multiverse_binary-i386_Packages'  
 détruit `/ var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_multiverse_i18n_Translation-fr '  
 détruit `/ var / lib / apt / lists / archive.ubuntu.com_ubuntu_dists_hardy_Release '  
 détruit `/ var / lib / apt / lists / archive.ubuntu.com_ubuntu_dists_hardy_Release.gpg '  
 détruit `/ var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_restricted_binary-i386_Packages'  
 détruit `/ var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_restricted_i18n_Translation-fr '  
 détruit `/ var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages'  
 détruit `/ var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_universe_i18n_Translation-fr '  
 détruit `/ var / lib / apt / lists / lock '  
 rm: can not remove `/ var / lib / apt / lists / partial ': is a folder  
 détruit `/ var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_main_binary-i386_Packages'  
 détruit `/ var / lib / apt / lists / security.ubuntu.com_ubuntu_dists_hardy-security_main_source_Sources'  
 détruit `/ var / lib / apt / lists / security.ubuntu.com_ubuntu_dists_hardy-security_Release '  
 détruit `/ var / lib / apt / lists / security.ubuntu.com_ubuntu_dists_hardy-security_Release.gpg '  
 détruit `/ var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_restricted_binary-i386_Packages'  
 détruit `/ var / lib / apt / lists / security.ubuntu.com_ubuntu_dists_hardy-security_restricted_source_Sources'  
 détruit `/ var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_universe_binary-i386_Packages'  
 détruit `/ var / lib / apt / lists / security.ubuntu.com_ubuntu_dists_hardy-security_universe_source_Sources'  
 détruit `/ var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy-updates_main_binary-i386_Packages'  
 détruit `/ var / lib / apt / lists / us.archive.ubuntu.com_ubuntu_dists_hardy-updates_Release '  
 détruit `/ var / lib / apt / lists / us.archive.ubuntu.com_ubuntu_dists_hardy-updates_Release.gpg '  
 détruit `/ var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy-updates_restricted_binary-i386_Packages'  
 m3asmi @ XXXXX: ~ $ sudo rm / var / lib / apt / lists / *-vf  
 rm: can not remove `/ var / lib / apt / lists / partial ': is a folder  
 m3asmi @ XXXXX: ~ $ sudo rm / var / lib / apt / lists / *-vf  
 rm: can not remove `/ var / lib / apt / lists / partial ': is a folder  
 m3asmi @ XXXXX: ~ $ sudo apt-get update  
 Reception: 1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-fr  
 Reception: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg [189B]  
 Reception: 3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / main Translation-fr [169kb]  
 Reception: 4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg [189B]  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-fr  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-fr  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-fr  
 Reception: 5 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5 kB]  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-fr  
 Reception: 6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release [58.5 kB]  
 Reception: 7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages [435kB]  
 Reception: 8 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [164kB]  
 Reception: 9 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / restricted Translation-fr [2790B]  
 Reception: 10 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / universe Translation-fr [194kb]  
 Reception: 11 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / universe Translation-fr [194kb]  
 Reception: 12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages [8437B]  
 Reception: 13 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [8008B]  
 Reception: 14 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [27.6 kB]  
 Reception: 15 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / multiverse Translation-fr [3614B]  
 Reception: 16 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release [65.9 kB]  
 Reception: 17 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [903B]  
 Reception: 18 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / main Packages [1178kB]  
 Reception: 19 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [82.6 kB]  
 Reception: 20 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources [12,9 kB]  
 Reception: 21 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / restricted Packages [6986B]  
 Reception: 22 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / universe Packages [4293kB]  
 Reception: 23 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / multiverse Packages [179KB]  
 6937ko approved 3min10 (36.4 kb / s)  
 Reading package lists ... Mistake!  
 E: Encountered a section with no Package: header  
 E: Problem with MergeList / var / lib / dpkg / status  
 E: The package lists or file "status" can not be analyzed or read.  
 m3asmi @ XXXXX: ~ $ sudo apt-get update  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-fr  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-fr  
 Achieved [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-fr  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-fr  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / main Translation-fr  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / restricted Translation-fr  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-fr  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release  
 Achieved [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / universe Translation-fr  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / multiverse Translation-fr  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages  
 Achieved [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / main Packages  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages  
 Achieved [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / restricted Packages  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / universe Packages  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / multiverse Packages  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources  
 Reading package lists ... Mistake!  
 E: Encountered a section with no Package: header  
 E: Problem with MergeList / var / lib / dpkg / status  
 E: The package lists or file "status" can not be analyzed or read.  
 m3asmi @ XXXXX: ~ $ sudo apt-get upgrade  
 Reading package lists ... Mistake!  
 E: Encountered a section with no Package: header  
 E: Problem with MergeList / var / lib / dpkg / status  
 E: The package lists or file "status" can not be analyzed or read.  
 m3asmi @ XXXXX: ~ $  

 m3asmi @ XXXXX: ~ $ sudo rm / var / lib / apt / lists / *-vf  
 détruit `/ var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages'  
 détruit `/ var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_main_i18n_Translation-fr '  
 détruit `/ var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_multiverse_binary-i386_Packages'  
 détruit `/ var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_multiverse_i18n_Translation-fr '  
 détruit `/ var / lib / apt / lists / archive.ubuntu.com_ubuntu_dists_hardy_Release '  
 détruit `/ var / lib / apt / lists / archive.ubuntu.com_ubuntu_dists_hardy_Release.gpg '  
 détruit `/ var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_restricted_binary-i386_Packages'  
 détruit `/ var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_restricted_i18n_Translation-fr '  
 détruit `/ var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages'  
 détruit `/ var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_universe_i18n_Translation-fr '  
 détruit `/ var / lib / apt / lists / lock '  
 rm: can not remove `/ var / lib / apt / lists / partial ': is a folder  
 détruit `/ var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_main_binary-i386_Packages'  
 détruit `/ var / lib / apt / lists / security.ubuntu.com_ubuntu_dists_hardy-security_main_source_Sources'  
 détruit `/ var / lib / apt / lists / security.ubuntu.com_ubuntu_dists_hardy-security_Release '  
 détruit `/ var / lib / apt / lists / security.ubuntu.com_ubuntu_dists_hardy-security_Release.gpg '  
 détruit `/ var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_restricted_binary-i386_Packages'  
 détruit `/ var / lib / apt / lists / security.ubuntu.com_ubuntu_dists_hardy-security_restricted_source_Sources'  
 détruit `/ var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_universe_binary-i386_Packages'  
 détruit `/ var / lib / apt / lists / security.ubuntu.com_ubuntu_dists_hardy-security_universe_source_Sources'  
 détruit `/ var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy-updates_main_binary-i386_Packages'  
 détruit `/ var / lib / apt / lists / us.archive.ubuntu.com_ubuntu_dists_hardy-updates_Release '  
 détruit `/ var / lib / apt / lists / us.archive.ubuntu.com_ubuntu_dists_hardy-updates_Release.gpg '  
 détruit `/ var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy-updates_restricted_binary-i386_Packages'  
 m3asmi @ XXXXX: ~ $ sudo apt-get update  
 Reception: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg [189B]  
 Reception: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / main Translation-fr [169kb]  
 Reception: 3 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-fr  
 Reception: 4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg [189B]  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-fr  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-fr  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-fr  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-fr  
 Reception: 5 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5 kB]  
 Reception: 6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release [58.5 kB]  
 Reception: 7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages [435kB]  
 Reception: 8 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [164kB]  
 Reception: 9 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / restricted Translation-fr [2790B]  
 Reception: 10 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / universe Translation-fr [194kb]  
 Reception: 11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages [8437B]  
 Reception: 12 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [8008B]  
 Reception: 13 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [27.6 kB]  
 Reception: 14 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [903B]  
 Reception: 15 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / multiverse Translation-fr [3614B]  
 Reception: 16 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release [65.9 kB]  
 Reception: 17 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [82.6 kB]  
 Reception: 18 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / main Packages [1178kB]  
 Reception: 19 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources [12,9 kB]  
 Reception: 20 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / restricted Packages [6986B]  
 Reception: 21 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / universe Packages [4293kB]  
 Reception: 22 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / multiverse Packages [179KB]  
 6950ko approved 5min14s (22.1 kb / s)  
 Reading package lists ... Mistake!  
 E: Encountered a section with no Package: header  
 E: Problem with MergeList / var / lib / dpkg / status  
 E: The package lists or file "status" can not be analyzed or read.  
 m3asmi @ XXXXX: ~ $ sudo apt-get update  
 [sudo] password for m3asmi:  
 Sorry, try again.  
 [sudo] password for m3asmi:  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-fr  
 Achieved [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-fr  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / main Translation-fr  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-fr  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-fr  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-fr  
 Achieved [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / restricted Translation-fr  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / universe Translation-fr  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / multiverse Translation-fr  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages  
 Achieved [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / main Packages  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources  
 Achieved [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / restricted Packages  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / universe Packages  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / multiverse Packages  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources  
 Reading package lists ... Mistake!  
 E: Encountered a section with no Package: header  
 E: Problem with MergeList / var / lib / dpkg / status  
 E: The package lists or file "status" can not be analyzed or read.  
 m3asmi @ XXXXX: ~ $  
 m3asmi @ XXXXX: ~ $  
 m3asmi @ XXXXX: ~ $ sudo apt-get check  
 Reading package lists ... Mistake!  
 E: Encountered a section with no Package: header  
 E: Problem with MergeList / var / lib / dpkg / status  
 E: The package lists or file "status" can not be analyzed or read.  
 m3asmi @ XXXXX: ~ $  
 m3asmi @ XXXXX: ~ $ sudo dpkg - configure-a  
 dpkg: error parsing in the file "/ var / lib / dpkg / status' near line 1:  
  the field name "" must be followed by a colon (:)  
 m3asmi @ XXXXX: ~ $ clea  
 ^ [[Abash: clea: command not found  
 m3asmi @ XXXXX: ~ $ clear  

 m3asmi @ XXXXX: ~ $ sudo apt-get check  
 Reading package lists ... Mistake!  
 E: Encountered a section with no Package: header  
 E: Problem with MergeList / var / lib / dpkg / status  
 E: The package lists or file "status" can not be analyzed or read.  
 m3asmi @ XXXXX: ~ $ sudo dpkg - configure-a  
 dpkg: error parsing in the file "/ var / lib / dpkg / status' near line 1:  
  the field name "" must be followed by a colon (:)  
 m3asmi @ XXXXX: ~ $ sudo aptitude update  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-fr  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-fr  
 Achieved [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-fr  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / main Translation-fr  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-fr  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-fr  
 Achieved [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / restricted Translation-fr  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / universe Translation-fr  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / multiverse Translation-fr  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages  
 Achieved [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / main Packages  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages  
 Achieved [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / restricted Packages  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / universe Packages  
 Achieved [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy / multiverse Packages  
 Achieved [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources  
 Reading package lists ... Mistake!  
 E: Encountered a section with no Package: header  
 E: Problem with MergeList / var / lib / dpkg / status  
 E: The package lists or file "status" can not be analyzed or read.  
 E: Could not rebuild package cache  
 m3asmi @ XXXXX: ~ $ sudo aptitude upgrade  
 W: The "upgrade" command is deprecated, use "safe-upgrade" instead.  
 Reading package lists ... Mistake!  
 E: Encountered a section with no Package: header  
 E: Problem with MergeList / var / lib / dpkg / status  
 E: The package lists or status file could not be opened or are incomprehensible.  
 Reading package lists ... Mistake!  
 E: Encountered a section with no Package: header  
 E: Problem with MergeList / var / lib / dpkg / status  
 E: The package lists or status file could not be opened or are incomprehensible.

---

### Post by m3asmi on 2009-05-21
Please help 
I don't know ho I'm goin to do

---

### Post by m3asmi on 2009-05-22
Please help 
I don't know ho I'm goin to do

---

### Post by m3asmi on 2009-05-22
Please help

---

