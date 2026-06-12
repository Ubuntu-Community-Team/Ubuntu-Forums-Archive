---
title: "¨Could not download the upgrades.¨"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by captain_conrad on 2009-05-27
I cannot get my system do upgrade!](*,):x
It just spits out this message to me.

¨Could not download the upgrades

The upgrade is now aborted. Please check your Internet connection or installation media and try again. All files downloaded so far are kept.

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-emailmerge_3.0.1-9ubuntu3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-emailmerge_3.0.1-9ubuntu3_all.deb) 302 Redirect [IP: 91.189.88.40 80]¨



this oppenoffice.org thing has forever given me hassles every time I do an upgrade, the emailmerge thing.

here´s what it says:


¨W: Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/pool/main/o/openoffice.org/openoffice.org-emailmerge_3.1.0-1ubuntu1~intrepid1_all.deb](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/pool/main/o/openoffice.org/openoffice.org-emailmerge_3.1.0-1ubuntu1~intrepid1_all.deb)
  302 Redirect¨



please help, what on earth do I have to do to just get the newest ubuntu???????????????????????????????????????????

---

### Post by taurus on 2009-05-27
Why don't you edit your /etc/apt/sources.list and place a # in front of the repo from ppa.launchpad.net to comment it out?  Then, you don't have to worry about it anymore.

---

### Post by captain_conrad on 2009-05-28
ok kewl.

question is, how on earth do I do that?

---

### Post by _Purple_ on 2009-05-28
Can you post the contents of 
```
gedit /etc/apt/sources.list
```

---

### Post by captain_conrad on 2009-06-15
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted universe multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free #Medibuntu
deb [http://ppa.launchpad.net/gnome-terminator/ubuntu](http://ppa.launchpad.net/gnome-terminator/ubuntu) intrepid main #Terminator
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #Wine
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free #Google
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) intrepid main #Compiz Fusion
deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) intrepid main #Firefox
deb [http://download.skype.com/linux/repos/debian](http://download.skype.com/linux/repos/debian) stable non-free #Skype
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main #OpenOffice.org
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed main restricted universe multiverse
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free

---

### Post by Therion on 2009-06-15
Happened to me this morning.  Running ```
sudo apt-get dist-update
``` and ```
sudo apt-get dist-upgrade
``` a time or two got everything sorted out.

---

### Post by captain_conrad on 2009-06-29
hey

well i tried running that and it ran for almost an hour, but eventually spat out this message:






Fetched 161MB in 1h9min39s (38.6kB/s)                                                                                                                   
Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/pool/main/o/openoffice.org/openoffice.org-emailmerge_3.1.0-5ubuntu1~intrepid1_all.deb](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/pool/main/o/openoffice.org/openoffice.org-emailmerge_3.1.0-5ubuntu1~intrepid1_all.deb)  302 Redirect
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
conrad@Conrad:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
conrad@Conrad:~$ 





did it update anything at all????
am i doing it right / wrong????
confused.

---

### Post by captain_conrad on 2010-05-31
update:

I just left it, and I think with time it just sorted itself out... ? Still no idea what was wrong.

Its now a year later, and managed to update 9.04 to 9.10 to 10.04 just fine. (just had to free about 1GB of disk space to meet the requirements).

So i guess this thread is now obsolete, so I am marking it as solved.

---

