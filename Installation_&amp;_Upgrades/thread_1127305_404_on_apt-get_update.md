---
title: "404 on apt-get update"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by robinc on 2009-04-16
Hello all,

I'm running an ubuntu 7.04 feisty based web server.

When I try and **apt-get update** I get:

```
Err http://medibuntu.sos-sts.com feisty Release.gpg
  Could not resolve ‘medibuntu.sos-sts.com’
Err http://medibuntu.sos-sts.com feisty/free Translation-en_GB                                                                                                                      
  Could not resolve ‘medibuntu.sos-sts.com’
Err http://medibuntu.sos-sts.com feisty/non-free Translation-en_GB                                                                                                                  
  Could not resolve ‘medibuntu.sos-sts.com’
Ign http://medibuntu.sos-sts.com feisty Release                                                                                                                                     
Ign http://medibuntu.sos-sts.com feisty/free Packages                                                                                                  
Ign http://security.ubuntu.com feisty-security Release.gpg                                                       
Ign http://security.ubuntu.com feisty-security/main Translation-en_GB                                            
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_GB                                      
Ign http://medibuntu.sos-sts.com feisty/non-free Packages                                                                                              
Ign http://medibuntu.sos-sts.com feisty/free Sources                                                                                                    
Ign http://security.ubuntu.com feisty-security/universe Translation-en_GB                                                                               
Ign http://security.ubuntu.com feisty-security Release                                                                  
Ign http://medibuntu.sos-sts.com feisty/non-free Sources                                                                
Err http://medibuntu.sos-sts.com feisty/free Packages                                                                   
  Could not resolve ‘medibuntu.sos-sts.com’
Ign http://security.ubuntu.com feisty-security/main Packages                                                            
Err http://medibuntu.sos-sts.com feisty/non-free Packages                                                               
  Could not resolve ‘medibuntu.sos-sts.com’
Ign http://security.ubuntu.com feisty-security/restricted Packages                                                      
Ign http://security.ubuntu.com feisty-security/main Sources                                                             
Ign http://security.ubuntu.com feisty-security/restricted Sources                                                       
Err http://medibuntu.sos-sts.com feisty/free Sources                                                                    
  Could not resolve ‘medibuntu.sos-sts.com’
Get: 1 http://archive.canonical.com feisty-commercial Release.gpg [189B]                                                
Ign http://archive.canonical.com feisty-commercial/main Translation-en_GB                                               
Err http://medibuntu.sos-sts.com feisty/non-free Sources                                                                
  Could not resolve ‘medibuntu.sos-sts.com’
Ign http://security.ubuntu.com feisty-security/universe Packages                                  
Ign http://security.ubuntu.com feisty-security/universe Sources                   
Err http://security.ubuntu.com feisty-security/main Packages                      
  404 Not Found
Err http://security.ubuntu.com feisty-security/restricted Packages                
  404 Not Found
Err http://security.ubuntu.com feisty-security/main Sources                       
  404 Not Found
Err http://security.ubuntu.com feisty-security/restricted Sources                 
  404 Not Found
Err http://security.ubuntu.com feisty-security/universe Packages                  
  404 Not Found
Err http://security.ubuntu.com feisty-security/universe Sources                   
  404 Not Found
Hit http://archive.canonical.com feisty-commercial Release                        
Ign http://archive.canonical.com feisty-commercial/main Packages
Hit http://archive.canonical.com feisty-commercial/main Packages
Ign http://archive.ubuntu.com feisty Release.gpg
Ign http://archive.ubuntu.com feisty/main Translation-en_GB
Ign http://archive.ubuntu.com feisty/restricted Translation-en_GB
Ign http://archive.ubuntu.com feisty/universe Translation-en_GB
Ign http://archive.ubuntu.com feisty/multiverse Translation-en_GB
Ign http://archive.ubuntu.com feisty-updates Release.gpg
Ign http://archive.ubuntu.com feisty-updates/main Translation-en_GB
Ign http://archive.ubuntu.com feisty-updates/restricted Translation-en_GB
Ign http://archive.ubuntu.com feisty-backports Release.gpg
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_GB
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_GB
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_GB
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_GB
Ign http://archive.ubuntu.com feisty Release
Ign http://archive.ubuntu.com feisty-updates Release
Ign http://archive.ubuntu.com feisty-backports Release
Ign http://archive.ubuntu.com feisty/main Packages
Ign http://archive.ubuntu.com feisty/restricted Packages
Ign http://archive.ubuntu.com feisty/main Sources
Ign http://archive.ubuntu.com feisty/restricted Sources
Ign http://archive.ubuntu.com feisty/universe Packages
Ign http://archive.ubuntu.com feisty/universe Sources
Ign http://archive.ubuntu.com feisty/multiverse Packages
Ign http://archive.ubuntu.com feisty/multiverse Sources
Ign http://archive.ubuntu.com feisty-updates/main Packages
Ign http://archive.ubuntu.com feisty-updates/restricted Packages
Ign http://archive.ubuntu.com feisty-updates/main Sources
Ign http://archive.ubuntu.com feisty-updates/restricted Sources
Ign http://archive.ubuntu.com feisty-backports/main Packages
Ign http://archive.ubuntu.com feisty-backports/restricted Packages
Ign http://archive.ubuntu.com feisty-backports/universe Packages
Ign http://archive.ubuntu.com feisty-backports/multiverse Packages
Err http://archive.ubuntu.com feisty/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com feisty/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com feisty/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com feisty/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com feisty/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com feisty/universe Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com feisty/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com feisty/multiverse Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com feisty-updates/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com feisty-updates/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com feisty-updates/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com feisty-updates/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com feisty-backports/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com feisty-backports/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com feisty-backports/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com feisty-backports/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
Fetched 1B in 0s (4B/s)  
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/Release.gpg  Could not resolve ‘medibuntu.sos-sts.com’
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/i18n/Translation-en_GB.bz2  Could not resolve ‘medibuntu.sos-sts.com’
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/i18n/Translation-en_GB.bz2  Could not resolve ‘medibuntu.sos-sts.com’
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz  Could not resolve ‘medibuntu.sos-sts.com’
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz  Could not resolve ‘medibuntu.sos-sts.com’
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz  Could not resolve ‘medibuntu.sos-sts.com’
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz  Could not resolve ‘medibuntu.sos-sts.com’
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz  404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```



**here is my sources file:**


```

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

deb http://archive.ubuntu.com/ubuntu feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty multiverse

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

```





I'm currently trying to install php-cli but when I run **apt-get install php-cli** I get:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package php-cli
```

when I run **apt-cache search php**
```
apache-ssl - versatile, high-performance HTTP server with SSL support
php5-cgi - server-side, HTML-embedded scripting language (CGI binary)
php5-gd - GD module for php5
php5-curl - CURL module for php5
php5-common - Common files for packages built from the php5 source
php5-mcrypt - MCrypt module for php5
libapache2-mod-php5 - server-side, HTML-embedded scripting language (apache 2 module)
php5 - server-side, HTML-embedded scripting language (meta-package)
php5-mysql - MySQL module for php5
```

---

### Post by taurus on 2009-04-16
Feisty has expired and no longer support.  Therefore, the repos have been moved to [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/).

You need to replace the current repos in your /etc/apt/sources.list with the new repos, [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/).

```

deb **http://old-releases.ubuntu.com**/ubuntu feisty main restricted
.....
.....

```

---

### Post by mkljun on 2011-11-23
You should also upgrade your system.


After all your lines in sources.list look like (in this example I use jaunty release) 

```
deb http://old-releases.ubuntu.com/ubuntu jaunty main restricted universe
```

update the repos

```
sudo apt-get update
```

Install update-manager-core if it is not yet installed:

```
sudo apt-get install update-manager-core
```

And now upgrade your system. 

```
sudo do-release-upgrade
```

Note that you can just upgrade to the next release (in my example from 9.04 to 9.10 or from LTS 8.04 to 10.04).

Also note that if upgrading over the ssh session it is advised to run the upgrade in the screen. So if the ssh session drops, the upgrade will continue. Install screen first (if not yet installed)

```
sudo apt-get install screen
```

Now run screen

```
screen
```

And upgrade with 

```
sudo do-release-upgrade
```

How to return to the screen is beyond this post.

lp mk

---

### Post by feerdawooz on 2011-11-27
when i hit sudo apt-get upgrade


then i type my pasword
it's works
but the problems is after that it's come like this


E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


what that's probs?? somebody helpme

---

### Post by davetv on 2011-11-27
Make sure no package manager is running then 
in the terminal enter :-  sudo rm /var/lib/dpkg/lock

---

### Post by lisati on 2011-11-27
Back to sleep, oh old thread!

Rule of thumb: start a new thread if your problem isn't related to thread's topic.

---

