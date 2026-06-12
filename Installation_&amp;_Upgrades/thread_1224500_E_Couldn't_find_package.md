---
title: "E: Couldn't find package"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by kronicle on 2009-07-27
did a fresh installation of ubuntu 7.04 desktop.
i need to install several packages on it, so i run the following

sudo apt-get install apache2-mpm-prefork php5 php5-mysql 
mysql-server-5.0 mysql-client-5.0

and i get the following in return

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package apache2-mpm-prefork

i preety much cant install anything, i also run apt-get
for the packages one by one but the same result eg.
 
sudo apt-get apache2-mpm-prefork 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package apache2-mpm-prefork

sudo apt-get update returns the following
selom@websrv:/etc/apt$ sudo apt-get update
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
selom@websrv:/etc/apt$ 


PLEASE I NEED YOUR HELP URGENTLY
PLZ HELP A NEWBIE

---

### Post by dstew on 2009-07-27
I think the repositories have been moved to URL's like this:

[http://old-releases.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)

Try editing your /etc/apt/sources.list file to reflect the new location. Maybe that will work. Maybe you can do the same from the desktop in the System --> Preferences --> Software Sources window.

EDIT: Or maybe, install Jaunty 9.04 instead!

---

### Post by Soul-Sing on 2009-07-27
: [http://ubuntuforums.org/showthread.php?t=1223955](http://ubuntuforums.org/showthread.php?t=1223955)
multiple threads with the same question, and the same answers/recommendations.....

---

### Post by scroo.loose on 2009-07-27
I am having the same issue on the server verison of Jaunty Jackalope. I have tried pretty much everything i can think of. The packages are also not located in aptitude. I have tried duing a web update and it failed. My next step will be to formatt drive and start over and do and advance configuration, and just install every single possible apt. If anyone knows any better solution please let me know. I downloaded 9.04 approx 2 weeks ago, so it should be latest and greatest right? has there been any sort of patch to correct this issue?
 
My error occurs when trying to install apt vsftpd as well as dhcp3-server.

---

### Post by Partyboi2 on 2009-07-27
> **scroo.loose said:**
> I am having the same issue on the server verison of Jaunty Jackalope. I have tried pretty much everything i can think of. The packages are also not located in aptitude. I have tried duing a web update and it failed. My next step will be to formatt drive and start over and do and advance configuration, and just install every single possible apt. If anyone knows any better solution please let me know. I downloaded 9.04 approx 2 weeks ago, so it should be latest and greatest right? has there been any sort of patch to correct this issue?
 
My error occurs when trying to install apt vsftpd as well as dhcp3-server.
Hi, if you can not find the packages then make sure that you have all the required repos uncommented in your sources.list (if unsure how to do it, post the output to 'cat /etc/apt/sources.list') Also run
```
sudo aptitude update 
``` to update afterwards the package list.

---

### Post by kronicle on 2009-07-27
wondering if this is a good idea, i replaced the sources.list file in
my ubuntu 7.04 installation with another sources.list file i copied from an
ubuntu 8.04 instalation, and it worked, i was able to upgrade and 
download all the packages i needed, now am wondering if am going to have
any problems as a result of replacing the ubuntu7.04 sources.list file with an ubuntu 8.04 sources.list

thank you

---

### Post by asalina on 2012-01-13
> **Partyboi2 said:**
> 
```
sudo aptitude update 
```

Just installed 10.04LTS Server here and was having this problem, but the above command solved it. Thank you.

---

### Post by oldos2er on 2012-01-13
Closed, necromancy.

---

