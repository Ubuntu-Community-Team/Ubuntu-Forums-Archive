---
title: "Trouble installing Java, Please help!"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by Drumm3r4lyfe on 2009-03-16
Ok well I had java working on an older version of ubuntu (I think 8.04) but it's missing some file. and won't work. So I just burned a 8.10 ubuntu cd and I'm using that right now. I have not permanently installed 8.10 because there is no more space on my hard drive so I am using a temporary version of it. (I hope all of that made sense.)

Anyways I cannot seem to figure out how to install java and/or get it to run in firefox for games and such.


[COLOR="Red"]**Here's what I get for...**[/COLOR]


```
java -version
```
```
root@ubuntu:/home/ubuntu# java -version
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6) Runtime Environment (build 1.6.0_0-b12)
OpenJDK Client VM (build 1.6.0_0-b12, mixed mode, sharing)
root@ubuntu:/home/ubuntu# 

```
[COLOR="Red"]
**The errors I get so far...**[/COLOR]


```
root@ubuntu:/home/ubuntu# sudo apt-get install sun-java6-plugin ; sudo update-java-alternatives -s java-6-sun
```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6-plugin
update-java-alternatives: directory does not exist: /usr/lib/jvm/java-6-sun
root@ubuntu:/home/ubuntu#  sudo apt-get install sun-java6-plugin ; sudo update-java-alternatives -s java-6-sun
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6-plugin
update-java-alternatives: directory does not exist: /usr/lib/jvm/java-6-sun
```

```
root@ubuntu:/home/ubuntu# sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin 
```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate
```

I read somewhere that I need to delete IcedTea6, but I don't know how, or if I should do that?

Any help would be greatly appreciated. I also tried searching for sun java in the synaptic package manager, but it doesn't find anything. Is there anyway to delete my older partition of Ubuntu that doesn't work? I also have windows xp installed, but it needs to repair the config file using the cd, which I can't find :(.

Thanks.

---

### Post by taurus on 2009-03-16
Are you running 32bit or 64bit?

Have you enable all the repos in System -> Administration -> Software Sources?

---

### Post by Drumm3r4lyfe on 2009-03-16
I have a 32bit. I enabled everything, I guess I'll try everything I did again...

---

### Post by taurus on 2009-03-16
Run these two commands to install java again.

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
And if you still get the same error message, post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by chelrob on 2009-03-16
You can download binaries from Sun and manually install them.

---

### Post by Drumm3r4lyfe on 2009-03-17
Thanks for the help taurus, but still no luck. :(

Here's my /etc/apt/sources.list

```
root@ubuntu:/home/ubuntu# cat /etc/apt/sources.list
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb http://archive.ubuntu.com/ubuntu intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu intrepid main restricted

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu intrepid-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu intrepid universe
# deb-src http://archive.ubuntu.com/ubuntu intrepid universe
# deb http://archive.ubuntu.com/ubuntu intrepid-updates universe
# deb-src http://archive.ubuntu.com/ubuntu intrepid-updates universe
# deb http://security.ubuntu.com/ubuntu intrepid-security universe
# deb-src http://security.ubuntu.com/ubuntu intrepid-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb http://archive.ubuntu.com/ubuntu intrepid multiverse
# deb-src http://archive.ubuntu.com/ubuntu intrepid multiverse
# deb http://archive.ubuntu.com/ubuntu intrepid-updates multiverse
# deb-src http://archive.ubuntu.com/ubuntu intrepid-updates multiverse
# deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
# deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
```

And this is what I get for
```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

```
root@ubuntu:/home/ubuntu# sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6-bin
```

Is there anything else I could try?

Thanks.

---

### Post by taurus on 2009-03-17
You don't have enough repos enable in your /etc/apt/sources.list.  Go into System -> Administration -> Software Sources and place a check mark in front of the first four entries (leave Source code blank).  Then, remove the check mark for Cdrom.  Click the Third-Party Software tab and put a check mark for the first entry.  Close it and run those two commands again.

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by Drumm3r4lyfe on 2009-03-17
Ok, I was able to check the first 4 boxes under the software sources, and unchecked the last 2. But there is nothing under the 3rd party software  tab?

I retried and it's downloading something, so I think it worked! The file size is 130mb, will that be deleted once I reboot, because I have not actually installed ubuntu, just the "trial" version since I can't delete the 8.04 ubuntu partition that was installed using wubi. And since windows also is missing some file, I can't delete that partition. :( 


Just to make sure everything went smooth this is what I got...

```

root@ubuntu:/home/ubuntu# sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gsfonts-x11 java-common odbcinst1debian1 unixodbc xutils-dev
Suggested packages:
  equivs sun-java6-fonts libmyodbc odbc-postgresql libct1
The following NEW packages will be installed:
  gsfonts-x11 java-common odbcinst1debian1 sun-java6-bin sun-java6-jre
  sun-java6-plugin unixodbc xutils-dev
0 upgraded, 8 newly installed, 0 to remove and 291 not upgraded.
Need to get 35.3MB of archives.
After this operation, 103MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com intrepid/main java-common 0.30ubuntu3 [80.3kB]
Get:2 http://archive.ubuntu.com intrepid/multiverse sun-java6-jre 6-10-0ubuntu2 [6363kB]
Get:3 http://archive.ubuntu.com intrepid/main odbcinst1debian1 2.2.11-16build2 [66.3kB]
Get:4 http://archive.ubuntu.com intrepid/main unixodbc 2.2.11-16build2 [295kB] 
Get:5 http://archive.ubuntu.com intrepid/multiverse sun-java6-bin 6-10-0ubuntu2 [28.1MB]
Get:6 http://archive.ubuntu.com intrepid/main xutils-dev 1:7.4+3 [302kB]       
Get:7 http://archive.ubuntu.com intrepid/main gsfonts-x11 0.20ubuntu1 [10.8kB] 
Get:8 http://archive.ubuntu.com intrepid/multiverse sun-java6-plugin 6-10-0ubuntu2 [1962B]
Fetched 35.3MB in 1min57s (299kB/s)                                            
Preconfiguring packages ...
Selecting previously deselected package java-common.
(Reading database ... 102335 files and directories currently installed.)
Unpacking java-common (from .../java-common_0.30ubuntu3_all.deb) ...
Selecting previously deselected package sun-java6-jre.
Unpacking sun-java6-jre (from .../sun-java6-jre_6-10-0ubuntu2_all.deb) ...
Selecting previously deselected package odbcinst1debian1.
Unpacking odbcinst1debian1 (from .../odbcinst1debian1_2.2.11-16build2_i386.deb) ...
Selecting previously deselected package unixodbc.
Unpacking unixodbc (from .../unixodbc_2.2.11-16build2_i386.deb) ...
Selecting previously deselected package sun-java6-bin.
Unpacking sun-java6-bin (from .../sun-java6-bin_6-10-0ubuntu2_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package xutils-dev.
Unpacking xutils-dev (from .../xutils-dev_1%3a7.4+3_i386.deb) ...
Selecting previously deselected package gsfonts-x11.
Unpacking gsfonts-x11 (from .../gsfonts-x11_0.20ubuntu1_all.deb) ...
Selecting previously deselected package sun-java6-plugin.
Unpacking sun-java6-plugin (from .../sun-java6-plugin_6-10-0ubuntu2_i386.deb) ...
Processing triggers for doc-base ...
Processing 23 changed, 2 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Setting up java-common (0.30ubuntu3) ...

Setting up odbcinst1debian1 (2.2.11-16build2) ...

Setting up unixodbc (2.2.11-16build2) ...

Setting up xutils-dev (1:7.4+3) ...
Setting up gsfonts-x11 (0.20ubuntu1) ...

Setting up sun-java6-bin (6-10-0ubuntu2) ...

Setting up sun-java6-jre (6-10-0ubuntu2) ...

Setting up sun-java6-plugin (6-10-0ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```


Also, now that I have java, how would I enable java in my firefox 3 web browser?

Thanks you soo much for your help taurus! I'm defiantly sticking with ubuntu, once I figure out how to get windows to delete my older wubi partition ;).

---

### Post by taurus on 2009-03-17
You need to restart firefox.  Then, in the address field, type

```
about:plugins
```
and see if java-1.6 is on the list.

---

### Post by Drumm3r4lyfe on 2009-03-17
**_[COLOR="Red"]Taurus you are god[/COLOR]_**. I would give you a million dollars if I had enough :D.

Thank you sooo much for your help, I now can use java in firefox! Yay! Cookies for taurus! :D:D:D

Thanks again, they were not joking when they said ubuntu has the best community ever! Yay for ubuntu!

---

