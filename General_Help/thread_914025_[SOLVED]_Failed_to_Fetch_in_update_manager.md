---
title: "[SOLVED] Failed to Fetch in update manager"
date: 2008-09-08
forum: General Help
---

### Post by hokiesparkles on 2008-09-08
***Let's try this again. Sorry for not using a more descriptive title. Hope this one works. :) Thanks for the tip! :) I'll delete the previous post if can.

Ok....So every time is run the Update Manager and hit the "check" button to get new updates, this is what I get:

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updacotes/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updacotes/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updacotes/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updacotes/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updacotes/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updacotes/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updacotes/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updacotes/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Some index files failed to download, they have been ignored, or old ones used instead.

Someone please help! I'm at a loss. I've searched other forums and tried things others have suggested and haven't been able to fix it. Thanks so much for your help in advance!

---

### Post by drs305 on 2008-09-08
You can try another server via System, Admin,, Software Sources or via Synaptic, Settings, Repositories, Ubuntu Software tab. Toward the bottom, select Download From window, select Other and then Select Best Server or any listed server.

You could also check System, Preferences, Network Proxy, and see if Direct Internet connection is selected.

---

### Post by Oldsoldier2003 on 2008-09-08
> **hokiesparkles said:**
> ***Let's try this again. Sorry for not using a more descriptive title. Hope this one works. :) Thanks for the tip! :) I'll delete the previous post if can.

Ok....So every time is run the Update Manager and hit the "check" button to get new updates, this is what I get:

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updacotes/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updacotes/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updacotes/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updacotes/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updacotes/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updacotes/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updacotes/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updacotes/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Some index files failed to download, they have been ignored, or old ones used instead.

Someone please help! I'm at a loss. I've searched other forums and tried things others have suggested and haven't been able to fix it. Thanks so much for your help in advance!

post the output of ```
cat /etc/apt/sources.list
```

It appears your sources are malformed. Alternatively you could just change the sources to another server using the gui as stated above.

---

### Post by hokiesparkles on 2008-09-08
> **drs305 said:**
> You can try another server via System, Admin,, Software Sources or via Synaptic, Settings, Repositories, Ubuntu Software tab. Toward the bottom, select Download From window, select Other and then Select Best Server or any listed server.

You could also check System, Preferences, Network Proxy, and see if Direct Internet connection is selected.


I did the option of Select Best Server. I did it twice because the first time, I got the same error so I thought I'd try it again. Still got the same error:
"The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updacotes/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updacotes/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updacotes/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updacotes/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updacotes/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updacotes/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updacotes/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updacotes/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Some index files failed to download, they have been ignored, or old ones used instead."

I checked that the Network Proxy was set to Direct Internet Connection and it was so I didn't change anything.

Any other ideas? :confused:

---

### Post by hokiesparkles on 2008-09-08
> **Oldsoldier2003 said:**
> post the output of ```
cat /etc/apt/sources.list
```

It appears your sources are malformed. Alternatively you could just change the sources to another server using the gui as stated above.


What do you mean "change the sources to another server"? Please, clarify and tell me the steps I need to take. Thanks!

---

### Post by Oldsoldier2003 on 2008-09-08
> **hokiesparkles said:**
> What do you mean "change the sources to another server"? Please, clarify and tell me the steps I need to take. Thanks!

in software sources, select another server by name, not best server. If you get the same problems with another server its likely a proxy configuration error on your end.

---

### Post by Elfy on 2008-09-08
It's not the servers - I'd say there was something a bit odd going on in the sources - the page it can't find is

[http://archive.ubuntu.com/ubuntu/dists/hardy-](http://archive.ubuntu.com/ubuntu/dists/hardy-)[COLOR="Red"]updacotes[/COLOR]/multiverse/binary-i386/Packages.gz

If you open you're sources list for editing I suspect you'll find some "updacotes" - which should be "updates"

If you're not sure then run the command oldsoldier gave above from a terminal and someone will help.

---

### Post by hokiesparkles on 2008-09-08
This is the output of "cat /etc/apt/sources.list"

"
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://archive.ubuntu-rocks.org/ubuntu/](http://archive.ubuntu-rocks.org/ubuntu/) hardy-security main universe multiverse restricted #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updacotes restricted main universe multiverse
deb [http://archive.ubuntu-rocks.org/ubuntu/](http://archive.ubuntu-rocks.org/ubuntu/) hardy main universe multiverse restricted
deb-src [http://archive.ubuntu-rocks.org/ubuntu/](http://archive.ubuntu-rocks.org/ubuntu/) hardy main universe multiverse restricted #Added by software-properties
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb [http://archive.ubuntu-rocks.org/ubuntu/](http://archive.ubuntu-rocks.org/ubuntu/) hardy-proposed universe main multiverse restricted
deb-src [http://archive.ubuntu-rocks.org/ubuntu/](http://archive.ubuntu-rocks.org/ubuntu/) hardy-proposed universe main multiverse restricted
deb [http://archive.ubuntu-rocks.org/ubuntu/](http://archive.ubuntu-rocks.org/ubuntu/) hardy-updates universe main multiverse restricted
deb-src [http://archive.ubuntu-rocks.org/ubuntu/](http://archive.ubuntu-rocks.org/ubuntu/) hardy-updates universe main multiverse restricted"


forestpixie, you said to change the "updacotes" to "updates" right? Sorry, I didn't see the post output of cat /etc/apt/sources.list, OldSoldier2003... :(

---

### Post by Elfy on 2008-09-08
Ok - that's a bit of a mess :) - are you running gutsy or hardy, not a good idea to have the repos from both.

9th line from the bottom - hardy-updacotes should be hardy-updates

If you are using hardy - 8.04.1 then delete the gutsy lines, to leave only hardy, obvioulsy if you're using gutsy -7.10 then remove the hardy lines.

To backup and then edit the file run these 2, it will open the file in a text editor

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.0809
gksudo gedit /etc/apt/sources.list
```

Save and close then run
```
sudo apt-get update
```

If you get errors rerun the cat command and paste the errors and the edited sources list.

---

### Post by hokiesparkles on 2008-09-08
YAY! I don't get that error anymore. You know, as I was posting the sources.list, I realized that I had both hardy and gutsy...I'm not sure how that happened...

Thanks so much! Really appreciate it! :KS

---

### Post by Elfy on 2008-09-08
welcome :)

---

### Post by Sanlion on 2008-09-09
TYVM my Ubuntu now is ok after selecting the best server for me :D

---

