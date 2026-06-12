---
title: "problem installing real player in hardy"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by abhinav.p on 2009-03-06
using the guide given in
[http://swik.net/Ubuntu/Only+Ubuntu/H...n+Ubuntu/b5t6f](http://swik.net/Ubuntu/Only+Ubuntu/H...n+Ubuntu/b5t6f)


i was able to insatll real player.but the command marked 9.that is
#cp /opt/real/RealPlayer/mozilla/nphelix.so ~/.mozilla/plugins/nphelix.so && cp /opt/real/RealPlayer/mozilla/nphelix.xpt ~/.mozilla/plugins/nphelix.xpt
gave an error saying




/plugins/nphelix.xpt cp: cannot stat `/opt/real/RealPlayer/mozilla/nphelix.so': No such file or directory




what should i do ?the installed real player does not play anyfiles as of now...

---

### Post by Partyboi2 on 2009-03-07
Are you sure that it is installed? The first time I ran the installer it said it had installed but when I looked at /opt there was no real folder, but after running the installer again it created the /opt/real.

---

### Post by abhinav.p on 2009-03-07
as i said i just followed the steps given.however when i tried to reinstall it using the same command ./configure,it says no such file or directory.how do i reinstall it?

---

### Post by spcwingo on 2009-03-07
> **abhinav.p said:**
> as i said i just followed the steps given.however when i tried to reinstall it using the same command ./configure,it says no such file or directory.how do i reinstall it?

```
sudo apt-get install realplayer
```

Just make sure to enable the multiverse repos...or is it universe...:-k

---

### Post by Partyboi2 on 2009-03-07
> **abhinav.p said:**
> as i said i just followed the steps given.however when i tried to reinstall it using the same command ./configure,it says no such file or directory.how do i reinstall it?
You should be using 
```
sudo ./RealPlayer11GOLD.bin
```
not ./configure


@ spcwingo
There is no realplayer in either repo, maybe you are thinking of a third party repo?

---

### Post by abhinav.p on 2009-03-07
OUTPUT FOR#sudo apt-get install realplayer



Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate

---

### Post by abhinav.p on 2009-03-07
OUTPUT FOR#sudo apt-get install realplayer



Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate

---

### Post by abhinav.p on 2009-03-07
OUTPUT FOR#sudo apt-get install realplayer



Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate

---

### Post by abhinav.p on 2009-03-07
OUTPUT FOR#sudo apt-get install realplayer



Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate

---

### Post by spcwingo on 2009-03-07
> **Partyboi2 said:**
> 
There is no realplayer in either repo, maybe you are thinking of a third party repo?

Oops, yeah, it's in the medibuntu repos.

---

### Post by Partyboi2 on 2009-03-07
> **abhinav.p said:**
> OUTPUT FOR#sudo apt-get install realplayer



Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate
You will get this message because realplayer is not in the ubuntu repository, you will need to add the medibuntu repository first. To do this open a terminal and type or paste to add the medibuntu repository.
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```
Then add the key
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```then install by typing
 
```
sudo apt-get install realplayer
```@spcwingo
Thanks for that I was not aware they had a realplayer11.

---

### Post by abhinav.p on 2009-03-08
it installed without any problem as per your commands.just out of curiosity,what is the difference between ubuntu,kubuntu and medibubtu?

---

### Post by Partyboi2 on 2009-03-09
> **abhinav.p said:**
> it installed without any problem as per your commands.just out of curiosity,what is the difference between ubuntu,kubuntu and medibubtu?
Ubuntu uses gnome for the Desktop and Kubuntu uses kde, they are basically the same under the hood. Kubuntu is a derived version of Ubuntu.
Medibuntu is a repository that has packages that are not included in the Ubuntu repository for  different reasons like licensing, copyrights etc. You can read more [[COLOR=Blue]here[/COLOR]]("http://www.medibuntu.org/") about it.

---

