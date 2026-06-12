---
title: "can't remove package to reinstall"
date: 2012-05-05
forum: Hardware
---

### Post by etrexuser on 2012-05-05
Any suggestions.  Running 10.04.  How can I have Ubuntu scan my HD to see if that's the problem.

sudo apt-get install -f
[sudo] password for ______ : 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  java-common odbcinst libnss3-dev sun-java6-bin unixodbc odbcinst1debian1
  sun-java6-jre libnspr4-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  adobe-flashplugin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 10.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 221203 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--remove):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 adobe-flashplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)


Addendum:  If I try to download and install Adobe flash player from the web, I'm told by my 
operating system that the Software Index is Broken and it's a major failure of my software 
management system.

---

### Post by ProfessorFarnsworth on 2012-05-06
I had this problem and ended up fixing it by referencing [http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/]("http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/"). Basically something like the below seemed to remove it for me, and I can now install other packages and such:

cd /var/lib/dpkg/info/
sudo rm adobe-flashplugin.*
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin
sudo apt-get install -f
sudo apt-get update

---

### Post by traditionalist on 2012-05-06
Had this a couple of times and used Bleachbit;

[http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

( In UBUNTU software center ).  This fixed the problems.  

Regards...Trad

---

### Post by etrexuser on 2012-05-06
> **ProfessorFarnsworth said:**
> I had this problem and ended up fixing it by referencing [http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/](http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/). Basically something like the below seemed to remove it for me, and I can now install other packages and such:

cd /var/lib/dpkg/info/
sudo rm adobe-flashplugin.*
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin
sudo apt-get install -f
sudo apt-get update


That seemed to do it a lot of good; however, when I go to youtube or accuweather I still get reports that the flash plug in is not installed on many videos and certain content.

Update:  scratch that, System told me that Adobe flash plug in failed to install or upgrade when I clicked the little icon in upper tool bar right before I shut down.

Update #2: I just went to Youtube and when a video told me to download the Adobe flash plug in, I did, which took a while, but everything seems to be working now.

---

### Post by etrexuser on 2012-05-06
> **traditionalist said:**
> Had this a couple of times and used Bleachbit;

[http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

( In UBUNTU software center ).  This fixed the problems.  

Regards...Trad


I downloaded Bleachbit.  Exactly what did you do with the program from there, delete flash cache and cookies?

---

### Post by traditionalist on 2012-05-07
Yes.  I deleted everything the program showed except for where it warned me that things might be slow or experimental;

I did this in both "root"  and "normal".  After that I had no more problems with the flash plugin. I have no idea why it worked.

[[IMG]http://img6.imageshack.us/img6/5706/selection004t.png[/IMG]](http://img6.imageshack.us/i/selection004t.png/)
[[IMG]http://img593.imageshack.us/img593/101/selection003j.png[/IMG]](http://img593.imageshack.us/i/selection003j.png/)

Regards....Trad

---

### Post by Ian Clark on 2012-10-10
A failed flash update borked flash for Youtube. I can see flash movies off my hard drive but Youtube doesn't work anymore. Basically I'm computing out of China and my VPN only runs out of firefox, not for the updates. If some server or another is blocked by the CCP this can happen.

So now what happens is Software Center cannot remove it, sudo dpkg --configure -a does not finish the install, as I can't connect to the adobe server, ```
find /var/lib/dpkg/alternatives/*flash* -type f -size 0 | xargs sudo rm -f
```returns ```
find: "/var/lib/dpkg/alternatives/*flash*": File o directory non esistente
```(as I don't really know where the file is)...```
sudo dpkg -r --force-remove-reinstreq flashplugin-nonfree
```returns```
dpkg: qualche altro processo detiene il blocco sul database di stato (some other process is blocking this from running)
```

Basically I want to remove the current flash install completely and reinstall from the tar.gz file I downloaded from Adobe's website (this way the upgrade happens and the CCP block has no effect).

Thanks to anyone who cares

---

### Post by admelfo on 2012-10-11
> **traditionalist said:**
> Yes.  I deleted everything the program showed except for where it warned me that things might be slow or experimental;

I did this in both "root"  and "normal".  After that I had no more problems with the flash plugin. [COLOR="DarkOrange"]I have no idea why it worked.[/COLOR]


Regards....Trad

...pretty much sums up the bulk of my command line experience... ;)

---

### Post by Ian Clark on 2012-10-11
[This]("http://www.upubuntu.com/2012/06/how-to-install-flash-player-11-manually.html") solution worked for me.

---

