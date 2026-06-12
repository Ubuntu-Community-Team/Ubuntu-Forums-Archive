---
title: "Packages won't install"
date: 2008-09-01
forum: General Help
---

### Post by F34R1355 on 2008-09-01
I have a problem when trying to install packages on my laptop I get an error stating Relies on * but won't be installed: * Not installable. If I try to apt-get install the package it says there is not entry point. I have tried a few fixes that people have brought up for what appeared to be the same issue. I know that the packages that I am attempting to get are in working order, I have them installed on my desktop.
I also don't know if this is the proper place for this. My thought was that this is the are for installation problems, I am have problems installing packages.
If you need more info just let me know, and I can get it for you.
Thanks in advance,
F34r1355.

---

### Post by iaculallad on 2008-09-01
Try to post the exact error you received.

---

### Post by aysiu on 2008-09-02
Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? ```
cat /etc/apt/sources.list
cat /etc/lsb-release
uname -m
sudo apt-get update
```

---

### Post by F34R1355 on 2008-09-02
cat /etc/apt/sources.list
```

deb http://security.ubuntu.com/ubuntu hardy-security restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

cat /etc/lsb-release
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

```

uname -m
```

i686

```

sudo apt-get update
```

Password or swipe finger: 
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US     
Hit http://us.archive.ubuntu.com hardy Release.gpg                             
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US              
Hit http://playonlinux.botux.net hardy Release.gpg                             
Ign http://playonlinux.botux.net hardy/main Translation-en_US                  
Hit http://wine.budgetdedicated.com hardy Release.gpg                          
Ign http://wine.budgetdedicated.com hardy/main Translation-en_US     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release                          
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US            
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg           
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://playonlinux.botux.net hardy Release                       
Hit http://us.archive.ubuntu.com hardy Release                       
Hit http://wine.budgetdedicated.com hardy Release                   
Hit http://us.archive.ubuntu.com hardy-updates Release                         
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Ign http://playonlinux.botux.net hardy/main Packages                           
Ign http://wine.budgetdedicated.com hardy/main Packages              
Hit http://us.archive.ubuntu.com hardy/restricted Packages           
Hit http://us.archive.ubuntu.com hardy/restricted Sources                      
Hit http://us.archive.ubuntu.com hardy/universe Packages                       
Hit http://us.archive.ubuntu.com hardy/universe Sources                        
Hit http://security.ubuntu.com hardy-security/restricted Sources               
Hit http://security.ubuntu.com hardy-security/universe Packages                
Hit http://security.ubuntu.com hardy-security/universe Sources                 
Hit http://playonlinux.botux.net hardy/main Packages                           
Hit http://wine.budgetdedicated.com hardy/main Packages                        
Hit http://us.archive.ubuntu.com hardy/multiverse Packages           
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Reading package lists... Done

```

One example of an exact error, see attached files.
Sorry for not including the build info in the original post.

---

### Post by aysiu on 2008-09-02
If you have dependency problems like those, they're usually due to conflicting repositories.

Your /etc/apt/sources.list has only a few repositories, but when you *sudo apt-get update* there are all these other repositories that come in. Do you have sources other than sources.list?

---

### Post by F34R1355 on 2008-09-02
In total I have three list files. sources.list playonlinux.list winehq.list
But I have used these other lists on my desktop and they work fine there. Perhaps that may be the difference between the 64-bit and 32-bit sources. I know that this laptop has had these problems since before I added winehq and playonlinux. The original problem started when I was trying to install wine, hence the winehq.
Although I don't think that it will have much effect, should I try restoring the original sources.list, and removing the winehq and playonlinux? I have tried it before, but perhaps I did it wrong at the time. I renamed the current sources.list, and replaced it with the backup. Then I moved the winehq and playonlinux from the sources.list.d.

---

