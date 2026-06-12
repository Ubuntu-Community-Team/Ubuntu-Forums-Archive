---
title: "Upgrade 6.06 to 9.04"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by bobup on 2009-08-07
Hi All 

This is my first post so here goes. I have been using Ubuntu for many years now and have just realised that I have missed out on new version updates. I am currently running 6.06 LTS (dapper) and would like to upgrade to the latest version 9.04. I have found information on how to do this without doing a complete install but have had the following message when pressing the check for update button 

Could Not Download All Repository Indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.


[http://packages.freecontrib.org/plf/dists/dapper/Release.gpg:](http://packages.freecontrib.org/plf/dists/dapper/Release.gpg:) Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out
[http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg:](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg:) Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out


Can anyone help me with finding the above files or removing from the update process

Thank you

---

### Post by Cheesemill on 2009-08-07
Just edit your source list using:
```
gksudo gedit /etc/apt/sources.list
```
and remove the lines that refer to http://packages.freecontrib.org...........

---

### Post by bobup on 2009-08-07
Hi Cheesemill,

Thank you for the info it worked :). 

I am now unable to follow the steps in the Ubuntu document as I am not offered the option to upgrade to 8.04. I will try to find the file and burn it to cd and upgrade that way.

Regards

bobup

---

### Post by slakkie on 2009-08-07
You're unable to upgrade from 6.06 to 8.04? That is weird.

can you run 

graphical
```

sudo update-manage

```

cli only
```

sudo do-release-upgrade

```

---

### Post by snowpine on 2009-08-07
Hi Bobup, I can't stress enough how much easier your life will be if you back up your documents and do a clean install of 9.04.

6.06 is no longer supported (it reached "end of life" in june), and even if it was, you would have to upgrade 6.06->8.04->8.10->9.04, with a risk at each step that something will go wrong.

Whereas a fresh reinstall of 9.04 should only take 20 or 30 minutes.

---

### Post by slakkie on 2009-08-07
6.06 is still supported..

---

### Post by Cheesemill on 2009-08-07
> **snowpine said:**
> hi bobup, i can't stress enough how much easier your life will be if you back up your documents and do a clean install of 9.04.
 
6.06 is no longer supported (it reached "end of life" in june), and even if it was, you would have to upgrade 6.06->8.04->8.10->9.04, with a risk at each step that something will go wrong.
 
Whereas a fresh reinstall of 9.04 should only take 20 or 30 minutes.
 
+1

---

### Post by snowpine on 2009-08-07
> **slakkie said:**
> 6.06 is still supported..

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
[http://news.softpedia.com/news/Goodbye-Ubuntu-6-06-LTS-Desktop-Edition-116229.shtml](http://news.softpedia.com/news/Goodbye-Ubuntu-6-06-LTS-Desktop-Edition-116229.shtml)

---

### Post by slakkie on 2009-08-07
> **snowpine said:**
> [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
[http://news.softpedia.com/news/Goodbye-Ubuntu-6-06-LTS-Desktop-Edition-116229.shtml](http://news.softpedia.com/news/Goodbye-Ubuntu-6-06-LTS-Desktop-Edition-116229.shtml)

Sure, desktop release... 

Check this:

> 
Ubuntu 6.06's support will end in June 2009 for desktops and June 2011 for servers. This will mean a lot of desktop only applications will not be supported anymore (see this list of supported packages) but once 6.06 will become EOL expect an update here. 

Loads of packages which are still updated/supported for dapper. 

Also see these screenshots: 
[http://opperschaap.net/~wesleys/ubuntu_old_releases/Dapper.png](http://opperschaap.net/~wesleys/ubuntu_old_releases/Dapper.png)
[http://opperschaap.net/~wesleys/ubuntu_old_releases/Dapper_update.png](http://opperschaap.net/~wesleys/ubuntu_old_releases/Dapper_update.png)
[http://opperschaap.net/~wesleys/ubuntu_old_releases/Dapper_install_zsh.png](http://opperschaap.net/~wesleys/ubuntu_old_releases/Dapper_install_zsh.png)

---

### Post by bobup on 2009-08-07
Hi All and thank you for your help.

I have decided to opt for a clean install of 9.04

Ta
bobup

---

### Post by tgalati4 on 2009-08-07
You can always keep Dapper and put Jaunty on a second partition.

---

