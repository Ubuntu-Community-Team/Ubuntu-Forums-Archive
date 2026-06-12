---
title: "need help with installing nvidia driver plz"
date: 2010-09-22
forum: Hardware
---

### Post by howzdis on 2010-09-22
hi , i have downloaded the newest nvidia 260 drivers from the nvidia website but now do not know how to install them :(..

Im fairly new to ubuntu & linux but am slowly getting the hang of it all & so if somone could give me a hand or point me somwhere it would be really appericated.Ive tryed useing commands in terminals from scrpits but no luck :(..Anyway thanks in advance :).

---

### Post by realzippy on 2010-09-22
If you install the 260.xx driver manually,you have to do that always when there is a kernel update...and you have to disable nouveau manually also.

Recommend to add **xswat ppa** to your sources,the "current" driver will be the 260.xx then
and you can install it easily with System/Administration/HardwareDrivers.

[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates)

Let us know if you have problems with adding the PPA...


And Welcome!!

---

### Post by howzdis on 2010-09-22
> **realzippy said:**
> If you install the 260.xx driver manually,you have to do that always when there is a kernel update...and you have to disable nouveau manually also.

Recommend to add **xswat ppa** to your sources,the "current" driver will be the 260.xx then
and you can install it easily with System/Administration/HardwareDrivers.

[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://edge.launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

Let us know if you have problems with adding the PPA...


And Welcome!!

Hi & thank you for the quick response :)..How  ever can you help with me with some instructions on how run or install  the package ive downloaded.Ill link the Os & hardware info also.

This is my hardware & Os list.
Motherboard - gigabyte ep41-ud3l
Cpu - intel dual core e8500
Video card - gigabyte 250 gts.

Os version is unbuntu 10.04 & default drivers.

---

### Post by realzippy on 2010-09-22
No advantage in installing the package you downloaded.You get the **same** driver with the xswat ppa. ?!

But,if you want it explicitly:

[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

---

### Post by howzdis on 2010-09-22
> **realzippy said:**
> No advantage in installing the package you downloaded.You get the **same** driver with the xswat ppa. ?!

Ok then no problems :)..Sorry im just not sure how to install it.I have disabled the default drivers with the hardware manager.And now dont know what to do.

I understand how to open a terminal & things just not real sure of all the commands though just yet :(.

Im very new at it all & sorry if im newsance lol.

---

### Post by realzippy on 2010-09-22
get the xswat ppa.Open a terminal,type:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```
```
sudo apt-get update
```

Then the "current" driver should be the 260.xx

---

### Post by howzdis on 2010-09-22
> **realzippy said:**
> get the xswat ppa.Open a terminal,type:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
``````
sudo apt-get update
```Then the "current" driver should be the 260.xx

Ok thanks i tryed what you told me to do.I opened a terminal & copyed & paste the commands you mentioned it downloaded a few things but come up with a error , ill copy & paste into here for you too look at.

This what i have tryed ,

( howzdis@howzdis-desktop:~$ sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 643DC6BD56580CEB1AB4A9F63B22AB97AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: key AF1CDFA9: "Launchpad PPA for Ubuntu-X" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
howzdis@howzdis-desktop:~$ sudo apt-get update
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid Release.gpg
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_AU
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_AU
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_AU
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid Release 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates Release                         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/main Packages                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/restricted Packages           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/universe Sources              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/multiverse Packages           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/main Packages         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/restricted Packages   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/) jaunty/main Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/multiverse Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg            
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_AU
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_AU
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_AU
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg 
Ign [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/) lucid/main Translation-en_AU
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
Ign [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) lucid/main Translation-en_AU
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg 
Ign [http://ppa.launchpad.net/user/ppa-name/ubuntu/](http://ppa.launchpad.net/user/ppa-name/ubuntu/) lucid/main Translation-en_AU
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
howzdis@howzdis-desktop:~$ )

---

### Post by realzippy on 2010-09-22
Nothing bad.
Now install the  "current" driver in Hardware drivers.After reboot
open nvidia-settings,and check if the 260.xx is installed.

---

### Post by howzdis on 2010-09-22
Ok thanks again.Sorry but where do i find it & how do install it? 

I restarted my system but it obiously has not installed :(.

---

### Post by howzdis on 2010-09-23
bump.

---

### Post by realzippy on 2010-09-23
You installed it with "System/Administration/HardwareDrivers" and
it did not work?

---

