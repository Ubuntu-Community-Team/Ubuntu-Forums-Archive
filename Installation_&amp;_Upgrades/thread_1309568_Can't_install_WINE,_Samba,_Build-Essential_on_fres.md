---
title: "Can't install WINE, Samba, Build-Essential on fresh Karmic 64 bit"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Freeman88 on 2009-11-01
I did an upgrade from jaunty to karmic (64bit) but many problems occurred so i deleted a partitions and did a completely fresh install of karmic. 
 Most of the problems that i had with upgraded version disappeared but few major new appeared.
 
 I cannot install WINE, Samba, Build-Essential.
 When i check Build-Essential in synaptic click apply i get this error message:
 
 > 
 Could not mark all packages for installation or upgrade.
 The following packages have unresolvable dependencies.
 Make sure that all required repositories are added and enabled in preferences.
 
 build-essential:
  Depends: g++ but it is not going to be installed
  When i try to install WINE i get this:
 
 > 
  Could not mark all packages for installation or upgrade.
  The following packages have unresolvable dependencies.
  Make sure that all required repositories are added and enabled in preferences.
 
 wine1.2:
  Depends: ia32-libs but it is not going to be installed
  Depends: lib32asound2 but it is not going to be installed
  Depends: libc6-i386 but it is not going to be installed
  Depends: lib32nss-mdns but it is not going to be installed
  Recommends: winbind but it is not going to be installed
  And with Samba (ver 2.3.4.0)
 
 > 
   Could not mark all packages for installation or upgrade.
   The following packages have unresolvable dependencies.
   Make sure that all required repositories are added and enabled in preferences.
 
 samba:
   Depends: samba-common (=2:3.4.0-3ubuntu4) but 2:3.4.0-3ubuntu5 is to be installed
  I have enabled (checked) main, universe, multiverse, restricted, partner repo's.
 Updates checked: important security and recommended.
 
 
 I am sorry if this problem already was posted but i was unable to find it.
 I really need wine and samba, please help.
 
 Almost forgot to mention i installed karmic from USB created on previous (karmic upgraded from jaunty) system. 
 Can that be the source of the problem?

I attached some screenshots for more details.

---

### Post by Freeman88 on 2009-11-04
I found the soultion... Prefered server for the main repositories was by default set to "Server for Serbia" witch apparently doesnt have all the packages.
Switched it to "Server for United States" and works like a charm!!!

---

### Post by Shtrk on 2009-11-06
> **Freeman88 said:**
> I found the soultion... Prefered server for the main repositories was by default set to "Server for Serbia" witch apparently doesnt have all the packages.
Switched it to "Server for United States" and works like a charm!!!

Thanks a loot! You solve my problem too!

---

### Post by kb-linux-2 on 2009-11-07
I am experiencing the same problem but I have not been able to identify which file you made the change in.  CJan you please let me now where you made the change you did to resolve the problem.

Thanks in advance for your response.

ll

---

### Post by Freeman88 on 2009-11-07
Go to Synaptic Package Manager -> Settings -> Repositories. 
"Software sources" windows will open and there you can set default server for main repositories.

Set it to "Main Server" or some other. Dont forget to "Reload" packages after that. ;)

---

### Post by kb-linux-2 on 2009-11-07
Thanks Freeman for your quick response.

I made the changes you indicated but I still have unresolved dependencies.  Guess that I have another problem in addition to the one described in your post.  

I will continue working the problem.  

Thankn again for your suggestions.  Have a great day!

---

### Post by H.R.Rambler on 2009-11-14
I had the same problem as I'm setting up a new 9.10 tonight. I finally realized that the information I had looked up from WineHQ before installing was the problem. There I was directed to add this repository:

> For Ubuntu Karmic (9.10):
ppa:ubuntu-wine/ppa

after disabling that repository I installed Wine as usual and it worked.

I'm guessing that the official Wine repository may be experiencing a temporary problem. This doesn't address any problem with Samba or Build-Essential though.

Hope it helps.

---

### Post by Kareeser on 2009-11-15
```
sudo apt-get install wine1.2
```

---

