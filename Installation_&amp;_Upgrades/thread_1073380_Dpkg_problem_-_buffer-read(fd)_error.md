---
title: "Dpkg problem - buffer-read(fd) error"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by Thyago Lopes on 2009-02-18
Hello, I've been getting an error message in any action that uses dpkg (for example, updates, installations, uninstallations, etc.).

Everytime I try to perform any of these actions it gives me the following error message:

"dpkg: erro processando /var/cache/apt/archives/dpkg_1.14.20ubuntu6.1_amd64.deb (--unpack): falhou em buffer_read(fd): lista de arquivos do pacote 'linux-headers-2.6.27-9-generic': Erro de entrada/saída
Erros foram encontrados durante o processamento de: /var/cache/apt/archives/dpkg_1.14.20ubuntu6.1_amd64.deb"

which, translating to English should be something like:
dpkg: error processing /var/cache/apt/archives/dpkg_1.14.20ubuntu6.1_amd64.deb (--unpack): failed in buffer_read(fd): files list from package 'linux-headers-2.6.27-9-generic': Input/output error
Errors have been found while processing: /var/cache/apt/archives/dpkg_1.14.20ubuntu6.1_amd64.deb"

As for now, I've already tried to delete the cached files from apt-get but it download the files again and nothing changed. Since then I'm assuming the problem is in a lower level than apt-get.
I've googled the message but couldn't find a resolution for this problem.

Can anyone try to help me, please?

Thanks in advance :)

---

### Post by Miedzinjsh on 2009-03-11
I have the same problem now....
Can you please tell your solution?

---

### Post by Thyago Lopes on 2009-03-11
Actually, I couldn't find a solution anywhere, so I decided to make a whole new installation of Ubuntu.
Sorry for not being able to help =/

---

### Post by Neo_The_User on 2009-03-11
Open up a terminal:

```

sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install -f && sudo apt-get install dpkg linux-headers-2.6.27-9-generic

```

---

### Post by el duderino's dude on 2010-06-13
i have tried everything that you and many other people have  suggested 

but i have a red circle in the top right of my desktop right next to my wireless internet connection and it says

an error occurred, please run package manager from the right click menu  or apt-get in a terminal to see what is wrong and the error code is: 

error: opening the cache (e:read  error - read (5:input/output error), E: problem opeing  /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid-updates_universe_binary-i386_packages,  E: The package lists or status file could not be parsed or opened.)

when i click on this package it pulls up a file in gedit but it then  says couldn't open the file and it had an: error reading file:  input/output error

anything you can do to help will be appreciated i cant update or install  anything to try and help because of it

here is what happens when i type in sudo apt-get update

```
mike@Mikes-Computational:~$ sudo apt-get update
[sudo] password for mike: 
Get:1 http://dl.google.com stable Release.gpg [189B]
Ign http://dl.google.com/linux/deb/ stable/main Translation-en_US              
Get:2 http://dl.google.com stable Release [2,544B]                             
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ lucid/partner Translation-en_US              
Hit http://archive.ubuntu.com lucid Release.gpg                                
Hit http://us.archive.ubuntu.com lucid Release.gpg                             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/ lucid/main Translation-en_US
Get:3 http://dl.google.com stable/main Packages [1,061B]                       
Hit http://archive.ubuntu.com lucid Release                                    
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg                     
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://archive.canonical.com lucid Release                                 
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://us.archive.ubuntu.com lucid-security Release.gpg                    
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com lucid/main Sources                               
Hit http://us.archive.ubuntu.com lucid Release                                 
Hit http://us.archive.ubuntu.com lucid-updates Release               
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://us.archive.ubuntu.com lucid-security Release                        
Hit http://archive.ubuntu.com lucid/restricted Sources               
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-security/main Packages
Hit http://us.archive.ubuntu.com lucid-security/restricted Packages
Hit http://us.archive.ubuntu.com lucid-security/universe Packages
Hit http://us.archive.ubuntu.com lucid-security/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-security/main Sources
Hit http://us.archive.ubuntu.com lucid-security/restricted Sources
Hit http://us.archive.ubuntu.com lucid-security/universe Sources
Hit http://us.archive.ubuntu.com lucid-security/multiverse Sources
Fetched 3,794B in 1s (2,627B/s)
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: Problem opening /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid-updates_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
mike@Mikes-Computational:~$
```

---

