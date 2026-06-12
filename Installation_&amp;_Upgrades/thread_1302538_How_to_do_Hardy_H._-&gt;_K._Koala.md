---
title: "How to do: Hardy H. -&gt; K. Koala ?"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by chteuchteu on 2009-10-27
Helly !
I would like to know how to do, friday, to update my Ubuntu: i installed this one (Hardy Heron 8.04) yesterday, and i would like to know how to do it:

Must I to reinstall all my ubuntu ? Or just to update it by the "update" tool ??
If it's the first choice (reinstall all), is it a tool which allow us to import all programs and data from the precedent installation of Ubuntu ?

Sorry for my english: i'm french ;)

Thank you for the reply !


chteuchteu, who is loving Ubuntu :D

---

### Post by jheaton5 on 2009-10-27
If you want to update to Karmic, you have to update to Intrepid and then to Jaunty and then to Karmic.  You cannot go directly from Hardy to Karmic.  If you want to go that way be sure that Hardy is up to date. In a terminal, type:
```
$ sudo aptitude update
$ sudo aptitude safe-upgrade
```
Then edit your /etc/apt/sources.list file, as root, changing Hardy to Intrepid.```
$ gsksudo gedit /etc/apt/sources.list
```  Connect to the internet by ethernet instead of wireless.  Then do these steps: ```
$ sudo aptitude update
$ sudo aptitude install apt aptitude dpkg
$ sudo aptitude safe-upgrade
$ sudo full upgrade
```Then change your /etc/apt/sources.list file to point to Jaunty, repeat the above commands, Then change to Karmic and repeat the above commands.

You may want to back up your data and do a fresh install of Karmic by downloading the live cd.  Since you just installed Hardy, you probably don't have anything to back up.

---

### Post by slakkie on 2009-10-27
You can do it directly via adept_manager:

```

sudo adept_manager --dist-upgrade-devel-lts

```

I've tested it twice and it works.

You'll need to install the version from -updates or -proposed (they are the same now).

```

apt-cache policy adept-manager
adept-manager:
  Installed: (none)
  Candidate: 2.1.3ubuntu25.2
  Version table:
     2.1.3ubuntu25.2 0
        995 http://archive.ubuntu.com hardy-updates/main Packages
        300 http://archive.ubuntu.com hardy-proposed/main Packages
     2.1.3ubuntu25 0
        990 http://archive.ubuntu.com hardy/main Packages

```

Probably you can do it via another way too, but haven't looked at it and this is made on request of the KDE team afaik, so I'll stick with the KDE way of upgrading to 9.10 from 8.04. 

You could also upgrade to 8.10 and 9.04 and then to 9.10.

Be aware that 9.10 introduces ext4 (Jaunty did it, but in 9.10 it is the default), grub2, etc. A fresh install doesn't hurt ;)

---

### Post by slakkie on 2009-10-27
> **jheaton5 said:**
> 
Then edit your /etc/apt/sources.list file, as root, changing Hardy to Intrepid.```
$ gsksudo gedit /etc/apt/sources.list
```  Connect to the internet by ethernet instead of wireless.  Then do these steps: ```
$ sudo aptitude update
$ sudo aptitude install apt aptitude dpkg
$ sudo aptitude safe-upgrade
$ sudo full upgrade
```Then change your /etc/apt/sources.list file to point to Jaunty, repeat the above commands, Then change to Karmic and repeat the above commands.


Simply install update-manager-core, then run do-release-upgrade and let the update-manager do its job (basicly doing what you are doing).

---

### Post by jheaton5 on 2009-10-27
> **slakkie said:**
> Be aware that 9.10 introduces ext4 (Jaunty did it, but in 9.10 it is the default), grub2, etc. A fresh install doesn't hurt ;)If he upgrades an ext3 system, 9.10 will also be an ext3 system.  If he does a fresh install then the file system will default to ext4.

---

### Post by chteuchteu on 2009-10-27
Thank you all :)

I don't really know what to do lol

What is the difference between ext3 and ext4 ? I am forced to erase all data on my partition to transform it in ext4 ?
It is possible to update grub from 1 to 2 (version 2) ?

If I understood, by installing Karmic with the live cd, I will erase all my data and installed programs. Isn't it ? :s

I think I will install it from the live cd... I spend 2 days to configure Hardy but... I would like to have a clean Ubuntu...

Thank you all :D

---

### Post by kasrawis on 2009-10-27
i suggest you to download a new ubuntu 9.10 iso burn it to CD you will need it for next time installation

---

### Post by slakkie on 2009-10-27
> **jheaton5 said:**
> If he upgrades an ext3 system, 9.10 will also be an ext3 system.  If he does a fresh install then the file system will default to ext4.

Correct :)

---

### Post by chteuchteu on 2009-10-27
> **kasrawis said:**
> i suggest you to download a new ubuntu 9.10 iso burn it to CD you will need it for next time installation

Ubuntu 9.10 is released on thursday, isn't it ? For sure i will burn the iso on a CD and install it: i think i will install ubuntu 9.10 over my existant installation...

Thank you all for your help :D I'm already "back-uping" my files :)

---

### Post by phillw on 2009-10-27
Come Thursday, this should, hopefully, trip in & work ....

[http://www.unixnewbie.org/how-to-upgrade-to-ubuntu-910/](http://www.unixnewbie.org/how-to-upgrade-to-ubuntu-910/)

Looks good to me !!!

Nearly backup time :-)

[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)

It works for me :D

and ...

[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

(I have a lot of add-ons - lol)

Going to be a busy day on the forums !!!
I hope all you guyz & galz who've been testing have booked the day off to help us all.
(I have a full LAMP Server, mod-security, rkhunter, chkrootkit, webmin etc !!)
4 web-sites ..

Yikes !!!!!

Regards,

Phill.

---

### Post by chteuchteu on 2009-10-27
Thank you for the links :D

> Well, I'm here to tell you that those things, just like [rebooting]("http://www.ubuntuforums.org/showthread.php?t=34629"), are Windows CrazyThings (tm).

:D

---

