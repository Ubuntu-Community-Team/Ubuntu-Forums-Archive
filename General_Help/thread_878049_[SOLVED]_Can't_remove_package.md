---
title: "[SOLVED] Can't remove package"
date: 2008-08-02
forum: General Help
---

### Post by Novus on 2008-08-02
Im trying to remove a package (soma) but it dosn't work :/


sudo apt-get remove soma
```
The following packages will be REMOVED:
  soma
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 9122kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 198541 files and directories currently installed.)
Removing soma ...
/etc/init.d/soma: 36: [[: not found
/etc/init.d/soma: 36: =: not found
/etc/init.d/soma: 38: f: not found
/etc/init.d/soma: 44: [[: not found
/etc/init.d/soma: 45: Syntax error: "else" unexpected
invoke-rc.d: initscript soma, action "stop" failed.
dpkg: error processing soma (--remove):
 subprocess pre-removal script returned error exit status 2
/etc/init.d/soma: 36: [[: not found
/etc/init.d/soma: 36: =: not found
/etc/init.d/soma: 38: f: not found
/etc/init.d/soma: 44: [[: not found
/etc/init.d/soma: 45: Syntax error: "else" unexpected
invoke-rc.d: initscript soma, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 soma
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

help please

---

### Post by sdowney717 on 2008-08-02
[http://linux.softpedia.com/get/Multimedia/Audio/Soma-suite-7775.shtml](http://linux.softpedia.com/get/Multimedia/Audio/Soma-suite-7775.shtml)

do you mean soma suite?

---

### Post by dentaku65 on 2008-08-02
Try with this:
```
sudo aptitude -f remove soma

```

---

### Post by Novus on 2008-08-02
> **sdowney717 said:**
> [http://linux.softpedia.com/get/Multimedia/Audio/Soma-suite-7775.shtml](http://linux.softpedia.com/get/Multimedia/Audio/Soma-suite-7775.shtml)

do you mean soma suite?
yea, soma is the daemon package.

> **dentaku65 said:**
> Try with this:
```
sudo aptitude -f remove soma

```

almost same result.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  dpatch 
The following packages will be REMOVED:
  soma 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 9470kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 198541 files and directories currently installed.)
Removing soma ...
/etc/init.d/soma: 36: [[: not found
/etc/init.d/soma: 36: =: not found
/etc/init.d/soma: 38: f: not found
/etc/init.d/soma: 44: [[: not found
/etc/init.d/soma: 45: Syntax error: "else" unexpected
invoke-rc.d: initscript soma, action "stop" failed.
dpkg: error processing soma (--remove):
 subprocess pre-removal script returned error exit status 2
/etc/init.d/soma: 36: [[: not found
/etc/init.d/soma: 36: =: not found
/etc/init.d/soma: 38: f: not found
/etc/init.d/soma: 44: [[: not found
/etc/init.d/soma: 45: Syntax error: "else" unexpected
invoke-rc.d: initscript soma, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Removing dpatch ...
Errors were encountered while processing:
 soma
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             

```

---

### Post by dentaku65 on 2008-08-02
Oh well, you have probably deleted some files previously... try in this way:
```
sudo aptitude install soma && sudo aptitute purge soma
```

---

### Post by Novus on 2008-08-02
> **dentaku65 said:**
> Oh well, you have probably deleted some files previously... try in this way:
```
sudo aptitude install soma && sudo aptitute purge soma
```

Can't remember I have.. and still same result :(

---

### Post by dentaku65 on 2008-08-03
Try this:
```
sudo updatedb
```
Then:
```
locate soma >soma.txt
```

Then post the content of soma.txt here:
```
cat soma.txt
```

---

### Post by Novus on 2008-08-04
```
/etc/somad
/etc/init.d/soma
/etc/logrotate.d/soma
/etc/rc0.d/K20soma
/etc/rc1.d/K20soma
/etc/rc2.d/S20soma
/etc/rc3.d/S20soma
/etc/rc4.d/S20soma
/etc/rc5.d/S20soma
/etc/rc6.d/K20soma
/etc/somad/certificate.pem
/etc/somad/palinsesto.cfg_example
/etc/somad/private.pem
/etc/somad/soma.cfg
/etc/somad/soma.cfg~
/etc/somad/spot.cfg_example
/home/novus/.isomaster
/home/novus/.somaplayer
/home/novus/.somaplayer/config
/home/novus/.somaplayer/dump
/usr/bin/soma-config
/usr/bin/somacheck
/usr/bin/somaclient
/usr/bin/somad
/usr/include/soma
/usr/include/soma/code.h
/usr/include/soma/commons.h
/usr/include/soma/controller.h
/usr/include/soma/local.h
/usr/include/soma/module.h
/usr/lib/libsoma.a
/usr/lib/libsoma.la
/usr/lib/libsoma.so
/usr/lib/libsoma.so.2
/usr/lib/libsoma.so.2.0.0
/usr/lib/cups/filter/cupsomatic
/usr/man/man1/soma-config.1
/usr/man/man1/somacheck.1
/usr/man/man1/somaclient.1
/usr/man/man1/somad.1
/usr/man/man5/soma.cfg.5
/usr/share/app-install/desktop/isomaster.desktop
/usr/share/app-install/desktop/somaplayer.desktop
/usr/share/app-install/icons/_usr_share_icons_isomaster_isomaster.png
/usr/share/doc/soma
/usr/share/doc/soma/NEWS.gz
/usr/share/doc/soma/README
/usr/share/doc/soma/README.Debian
/usr/share/doc/soma/README.module
/usr/share/doc/soma/changelog.Debian.gz
/usr/share/doc/soma/changelog.gz
/usr/share/doc/soma/copyright
/usr/share/man/man1/soma-config.1.gz
/usr/share/man/man1/somacheck.1.gz
/usr/share/man/man1/somaclient.1.gz
/usr/share/man/man1/somad.1.gz
/usr/share/man/man5/soma.cfg.5.gz
/var/lib/dpkg/info/soma.conffiles
/var/lib/dpkg/info/soma.list
/var/lib/dpkg/info/soma.md5sums
/var/lib/dpkg/info/soma.postinst
/var/lib/dpkg/info/soma.postrm
/var/lib/dpkg/info/soma.prerm
/var/log/soma.log

```

---

### Post by cariboo on 2008-08-04
I downloaded Soma from the site linked to above. This is source code for the program. The only way you can remove it automagically is to navigate to the directory you installed it from and type make uninstall. If you don't have the source directory on your hard drive you may want to download and extract the file again and then try make uninstall. You may have to run ./configure first.

Jim

---

### Post by zvacet on 2008-08-04
Do you still have folder in which you complie package?if you do go to that folder and type

```
sudo make uninstall
```

---

### Post by Novus on 2008-08-04
No it was installed from soma repos ([http://www.somasuite.org/debian/test/amd64/debian/](http://www.somasuite.org/debian/test/amd64/debian/))

---

### Post by zvacet on 2008-08-04
```
sudo dpkg --remove --force-remove-reinstreq packagename
```

---

### Post by Novus on 2008-08-04
> **zvacet said:**
> ```
sudo dpkg --remove --force-remove-reinstreq packagename
```

still not much luck. some parts got removed but not all and I got new error.. tried to reinstall and then remove again and still error. 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgtkhtml3.8-15 guile-1.6 libgoffice-0-common libgoffice-0-4
  libcrypt-ssleay-perl libdate-manip-perl slib libgsf-gnome-1-114
  libfinance-quote-perl guile-1.6-slib libhtml-tableextract-perl
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  soma
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 9122kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 197382 files and directories currently installed.)
Removing soma ...
/etc/init.d/soma: 36: [[: not found
/etc/init.d/soma: 36: =: not found
/etc/init.d/soma: 47: [[: not found
/etc/init.d/soma: 144: let: not found
invoke-rc.d: initscript soma, action "stop" failed.
dpkg: error processing soma (--remove):
 subprocess pre-removal script returned error exit status 127
/etc/init.d/soma: 36: [[: not found
/etc/init.d/soma: 36: =: not found
/etc/init.d/soma: 47: [[: not found
/etc/init.d/soma: 144: let: not found
invoke-rc.d: initscript soma, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 soma
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Every time I do anything with packages it gives me an error so I'd really like to get rid of this.. can I delete all soma files manually and somehow make the package manager "forget" it have ever seen soma?

---

### Post by Ataris on 2008-08-04
Administration --> Synaptic Package Manger

Search for 'soma.'

Find all of the soma packages you want to remove and then mark them for uninstallation and click Apply.

See if that works.

---

### Post by Novus on 2008-08-06
> **Ataris said:**
> Administration --> Synaptic Package Manger

Search for 'soma.'

Find all of the soma packages you want to remove and then mark them for uninstallation and click Apply.

See if that works.

already tried that one...
anyone else?

---

### Post by zvacet on 2008-08-06
> can I delete all soma files manually 

Yes you can.

```
sudo rm -r /path/to/file
```

But if you never do it before just to be sure what are you foing go to the every directory containing** soma** file with cd command (for example cd /usr/bin ) then type **ls ** to see content of directory and then in same directory 

```
sudo rm -r filename
``` 

If my explanation is not very clear (possible because I´m not native English speaker) post again if you have any question.

---

### Post by Novus on 2008-08-06
> **zvacet said:**
> Yes you can.

```
sudo rm -r /path/to/file
```

But if you never do it before just to be sure what are you foing go to the every directory containing** soma** file with cd command (for example cd /usr/bin ) then type **ls ** to see content of directory and then in same directory 

```
sudo rm -r filename
``` 

If my explanation is not very clear (possible because I´m not native English speaker) post again if you have any question.
I know how to force the remove of files, thats not the problem.. theres 2 questions:
1) how do I make apt-get/synaptic/dpkg/etc. "forget" that it ever had the soma package, making it not bugging me with errors.
2) is there some good reason not to do this when all else have failed?

---

### Post by drs305 on 2008-08-06
I generally don't read messages with this many posts but since you've tried many things here's one more you can try. It will export the dpkg info on what it thinks is on your computer into a file on your desktop. Then editthe file and remove any listing for 'soma' or affilitated packages. Then re-import the list to dpkg. It won't cleanly uninstall any remaining bits of the package but it may eliminate the error messages.

```

sudo dpkg --get-selections >~/Desktop/package-list
gedit ~/Desktop/package-list &
When done editing:
sudo dpkg --clear-selections
sudo dpkg --set-selections <~/Desktop/package-list
sudo apt-get update
sudo apt-get dselect-upgrade 

```

---

### Post by bodhi.zazen on 2008-08-06
Try :

```
sudo touch /etc/init.d/soma
sudo apt-get purge soma
```

---

### Post by Novus on 2008-08-07
> **bodhi.zazen said:**
> Try :

```
sudo touch /etc/init.d/soma
sudo apt-get purge soma
```

and this one finally worked! it's gone! :popcorn:
I had to do a sudo dpkg --configure soma before apt-get could purge it but then it just worked, thanx a ton mate!

---

### Post by Archbalt on 2009-11-28
I'm having the same problem, but with wine. I was installing it through "sudo apt-get install wine" and the pc turned off.
Now I cant finish the installation neither uninstall it at all. I've tried all that was said here, but nothing worked.

Anyone have any other idea about how to solve it? (I'm using Kubuntu Karmic Koala)

---

### Post by raktarok on 2009-11-28
Try editing the file /var/lib/dpkg/status. For more details, see this thread (post #10 and #12  might help, though the error there is a bit different. Follow the same pattern, replacing the package name there with yours. And proceed carefully!)
[http://ubuntuforums.org/showthread.php?t=1338829&page=2](http://ubuntuforums.org/showthread.php?t=1338829&page=2)
(Sorry, I am too lazy to post the instructions again..:)

---

