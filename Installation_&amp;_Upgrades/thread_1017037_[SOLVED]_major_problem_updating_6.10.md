---
title: "[SOLVED] major problem updating 6.10"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by flyingsliverfin on 2008-12-20
how do I update from 6.10 to 8.04 or anything better than 6.10? I don't have internal CD drive, its an ancient laptop, and I can't seem to be able to set boot priority to external PC card CD drive. (its also too old to set to boot from memory stick). HELP!!!!

---

### Post by oilchangeguy on 2008-12-20
> **flyingsliverfin said:**
> how do I update from 6.10 to 8.04 or anything better than 6.10? I don't have internal CD drive, its an ancient laptop, and I can't seem to be able to set boot priority to external PC card CD drive. (its also too old to set to boot from memory stick). HELP!!!!

how was 6.10 installed? and what are the specs of this computer? it may not be able to run a newer version of ubuntu.

---

### Post by flyingsliverfin on 2008-12-21
I don't know how it was installed, because my dad (it was his old laptop) gave it to his institute technichian, who installed 6.10

ill have to take a look at the specs, is there a way to find out them from inside 6.10?

like on windows there is a "devices", and something else that will tel you the things about comp (GHz, Ram, HD) all I know is that there is a 30GB HD and 22 GB are free

there is an option to install from the net, (which is probably how the guy did it) but I don't know how to do it.

---

### Post by taurus on 2008-12-21
The command from a terminal is 

```
lshw
```

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
Scroll down the the middle of the page.

---

### Post by Partyboi2 on 2008-12-21
From a terminal you can check hard drive size with
```
df -h
``` for memory
```
free -m
```
for cpu
```
cat /proc/cpuinfo
```

---

### Post by AusIV4 on 2008-12-21
Can you do a standard dist-upgrade? Feisty (7.04) is out of support, but I believe the repositories are still up. If you go to the update manager, it should give you the opportunity to upgrade. Just apply updates until you get to the version you want.

---

### Post by flyingsliverfin on 2008-12-21
ausIV4: I have tried but there is an error

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz) 404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz) 404 Not Found [IP: 91.189.88.40 80]


the CPU is 866 MhZ
RAM: 233 MB
and HD: 24 GB

---

### Post by flyingsliverfin on 2008-12-21
looks to me like either they switched the server for downloads or the reps are out.

---

### Post by Partyboi2 on 2008-12-21
You will probably need to add
```
deb http://old-releases.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ edgy-security main restricted universe multiverse 
``` to your sources.list before trying to upgrade.

[https://help.ubuntu.com/community/FeistyUpgrades](https://help.ubuntu.com/community/FeistyUpgrades)

---

### Post by flyingsliverfin on 2008-12-23
not working, but have another Q. Is it possible to just update the wireless manager because I don't need any of the other stuff for vacation?

---

### Post by jd4x4 on 2008-12-28
OK, so I was impressed with how much an Ubuntu user didn't need to be a total  geek until I went to upgrade and got these errors. 

Why is there a path on the archive server for all of the dists except feisty? And how was this left out of the "idiot" code loop with the Synaptic Package Manager and/or Upgrade Manager?

Everything is looking for a path that starts with "http://archive.ubuntu.com/ubuntu/dists/feisty/.." but it's not there.

---

### Post by Partyboi2 on 2008-12-28
> **jd4x4 said:**
> OK, so I was impressed with how much an Ubuntu user didn't need to be a total  geek until I went to upgrade and got these errors. 

Why is there a path on the archive server for all of the dists except feisty? And how was this left out of the "idiot" code loop with the Synaptic Package Manager and/or Upgrade Manager?

Everything is looking for a path that starts with "http://archive.ubuntu.com/ubuntu/dists/feisty/.." but it's not there.
Feisty has reached its eol (end of life)  so the ubuntu repositories have been adjusted to reflect this. You can still access feisty repos but you will need to add 
```
deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
``` to your sources.list. In saying all this I would advise if you are still using feisty to upgrade to a more current release of Ubuntu that is supported.

---

### Post by flyingsliverfin on 2008-12-29
ok, I think i managed to update the 6.10, but not all of it. There is (for instance) no pidgin. But when I execute
lsb_release -rd
it gives me:
Description:    Ubuntu 7.04
Release:        7.04
is that the only way to check, or should I try to update to 7.10?

are the 7.10 reps still up?

the way I updated was that I was going to do the manual update, so changed all the occurences of EDGY to FEISTY in the 
sources.list. Then I ran out of battery, so I forgot what I was doing while the laptop was charging. After I started up again, I got an update manager for feisty updates. it said that the system was out of date, and asked me to update it. I did and it seems to work:)


PS: I might not be right about this not being a complete install because i have never ever used 7.04 before. I Started at 7.10 on the desktop at home. I don't know if Pidgin even exists in 7.04 :( so i might be wrong. 


the main thing I want to know is if I have to change anything to update to 7.10 and then to 8.04 or 8.10?

---

### Post by Partyboi2 on 2008-12-29
> **flyingsliverfin said:**
> ok, I think i managed to update the 6.10, but not all of it. There is (for instance) no pidgin. But when I execute
lsb_release -rd
it gives me:
Description:    Ubuntu 7.04
Release:        7.04
is that the only way to check, or should I try to update to 7.10?

are the 7.10 reps still up?

the way I updated was that I was going to do the manual update, so changed all the occurences of EDGY to FEISTY in the 
sources.list. Then I ran out of battery, so I forgot what I was doing while the laptop was charging. After I started up again, I got an update manager for feisty updates. it said that the system was out of date, and asked me to update it. I did and it seems to work:)


PS: I might not be right about this not being a complete install because i have never ever used 7.04 before. I Started at 7.10 on the desktop at home. I don't know if Pidgin even exists in 7.04 :( so i might be wrong. 


the main thing I want to know is if I have to change anything to update to 7.10 and then to 8.04 or 8.10?
No you don't have not have to change anything you should be able to upgrade to gusty>hardy>intrepid  without problem. 
Pidgin in the feisty release is known as Gaim.

---

### Post by flyingsliverfin on 2008-12-29
thank you

---

### Post by flyingsliverfin on 2008-12-29
actually, there is a new problem when upgrading to 7.10 here is the error:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]


AGAINNNNNNNNNNNNNNN!!!!!!!!

here is my sources.list (I messed around with it a bit when starting on the manual upgrade of 7.04. It said to change all the ''edgy's''
 to ''feisty's''. Can you maybe correct it or change it as needed? thanks.
it might not even be that problem     :)

---

### Post by flyingsliverfin on 2008-12-29
interesting I just tried to change all the FEISTY'S to GUTSY'S in the sources.list (I DO have a backup with the EDGY's and the FEISTY's too just incase), and that didn't work. However, I could try what i did before to get to 7.04 from 6.10,which is when I change everything to GUTSY'S, I get the GUTSY updates. Then it said the system was out of date so the updates woulnd't work, then it asked me if I wanted to upgrade (I clicked YES) !!! it worked!!! I could try that with this version, if you don't have any objections or other suggestions, but would not like to do it again, since its what I did before to get to 7.04 and because the method is not mentioned not much or at all by others that have failed to update.

---

### Post by Partyboi2 on 2008-12-29
Try commenting everything out in your sources.list except for
```
deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse

```
then try upgrading to gusty.

---

### Post by flyingsliverfin on 2008-12-30
nope, that didn't work. I think when I find another internet connection while on vacation ill do what I did to get to 7.04 (mentioned on one of my recent posts on this thread). Also, it occured to me that 7.10 is not yet an old-release, so why should I have this in my reps?

deb [http://**old-releases](http://**old-releases)**.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb [http://**old-releases](http://**old-releases)**.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb [http://**old-releases](http://**old-releases)**.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse

---

### Post by Partyboi2 on 2008-12-30
> **flyingsliverfin said:**
> nope, that didn't work. I think when I find another internet connection while on vacation ill do what I did to get to 7.04 (mentioned on one of my recent posts on this thread). Also, it occured to me that 7.10 is not yet an old-release, so why should I have this in my reps?

deb [http://**old-releases**]("http://%3Cb%3Eold-releases%3C/b%3E").ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb [http://**old-releases**]("http://%3Cb%3Eold-releases%3C/b%3E").ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb [http://**old-releases**]("http://%3Cb%3Eold-releases%3C/b%3E").ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
So you can make sure you are up to date before upgrading.
[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

---

### Post by flyingsliverfin on 2008-12-30
when I visit the website you showed me, it said to check to make sure i have everything. then I get this error message

[B]Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz:) 404 Not Found [IP: 91.189.88.46 80]
[/B]

I dont think this has to do the sources.list or does it? I can do a partial update, using my method (changing everything in sources.list to GUTSY and then it shows me the updates for GUTSY. It tells me that the system is not up to date, then asks me to do a partial update. NOT A FULL UPDATE)

---

### Post by LRTIMKEN on 2008-12-30
Content's nice and I support you![FAG](http://www.nskcn.com/product/ShowClass.asp?ClassID=26) [fag](http://www.nskcn.com/product/ShowClass.asp?ClassID=26) [FAG](http://www.9skf.cn/product/ShowClass.asp?ClassID=26) [fag](http://www.9skf.cn/product/ShowClass.asp?ClassID=26)

---

### Post by flyingsliverfin on 2008-12-31
updated partially to 7.10, currently trying to update 8.04

---

### Post by jd4x4 on 2009-01-02
I'm sorry, but this is just absurd. I spent almost an afternoon trying to change preferences, attempting to edit files, and simply gave up.

All because something is "no longer supported" and the files physically moved from the server that an "Upgrade Manager" is programmed to look for?

I have things I wanted to do but so far I'm glad I dual booted my laptop. At least I can carry on with my (auto-updating as I type and WAY past "supported") windoz 2000 OS.

This really isn't intended to be a rant or flame.. simply a "state of the OS" from a user perspective. I was really hoping Ubuntu/Xubuntu was my ticket away from MSoft, but not yet unless I want to put my geek hat back on. I don't. I'm too old to waste time with tweaking an OS.

---

### Post by Partyboi2 on 2009-01-02
Have you thought of backing up your important stuff and doing a clean install of either hardy or intrepid which would save time. :)

---

### Post by flyingsliverfin on 2009-01-03
ok, I got a 8.04 full install, so Im done with this thread. I won't mark it as 'solved' though there is a chance that jd4x4 needs some more help

---

### Post by flyingsliverfin on 2009-01-10
Solved

---

