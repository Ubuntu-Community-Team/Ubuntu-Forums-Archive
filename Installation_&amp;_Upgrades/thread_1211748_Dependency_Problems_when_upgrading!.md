---
title: "Dependency Problems when upgrading!"
date: 2009-07-13
forum: Installation &amp; Upgrades
---

### Post by shinnphoto on 2009-07-13
Help!  I tried to upgrade from 7.10 to 8.04 (to get current and possibly upgrade even further), but I keep running into an error while trying to configure libpam-runtime.  Here's the output from sudo apt-get -f install: 

```
shinnphoto /: sudo apt-get -f install
[sudo] password for andrew:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libuuid1
Recommended packages:
  uuid-runtime
The following packages will be upgraded:
  libuuid1
1 upgraded, 0 newly installed, 0 to remove and 298 not upgraded.
2 not fully installed or removed.
Need to get 0B/41.1kB of archives.
After unpacking 8192B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up libpam-runtime (0.99.7.1-5ubuntu6.1) ...
/var/lib/dpkg/info/libpam-runtime.postinst: 19: md5sum: not found

```

It always hangs on that "md5sum: not found", and my entire distro upgrade is hosed.  This is a production web server, so I can't just wipe it clean and install the latest version from scratch.  How do I resolve the dependency issue?

---

### Post by Partyboi2 on 2009-07-13
Hi, try reinstalling the libpam-runtime package.
```
sudo apt-get --reinstall install libpam-runtime
sudo apt-get -f install
```

---

### Post by shinnphoto on 2009-07-13
It's gotten worse.  apt-get won't work, because it can't connect to the internet.  

Yesterday, I tried to upgrade from 7.10 to 8.04 following these steps:  
1) I added the old-releases repositories to /etc/apt/sources.list 
2) sudo apt-get update 
3) sudo apt-get install update-manager-core 
4) sudo do-release-upgrade 

The installation hung while installing libpam_rumtime, saying that no MD5 was found. 

Since then, I haven't been able to SSH into the server, and I can't ping it, either. It seems there's a problem with the network interfaces. I disabled the firewall, but I'm still not able to connect to the server. I checked /etc/resolv.conf, and the only entry there was: nameserver 127.0.0.1. 
I need help checking the other network interfaces. 

If we can't fix this installation, I'm happy to ditch it and start from scratch with a new one, but I need to know how to get the data off. Thanks for your help!

---

