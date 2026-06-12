---
title: "Reset Repositories"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by z|x on 2009-05-12
I'm having some trouble with the GPG keys that are saved on my system. I receive errors whenever I run the Update manager. Is there anyway in which I could revert back to the Default repositories and Signatures provided in the clean Jaunty Installation?

Thanks

---

### Post by _Purple_ on 2009-05-12
You can go to System > Administration > Software Sources. In Third-Party Softwares tab, you can remove the tick from the sources that you have added manually or you can add the GPG keys for the sources you are getting error for and then run 
```
sudo apt-get update
```

You can also replace your /etc/apt/sources.list with the list from a fresh jaunty install and run sudo apt-get update.

---

### Post by z|x on 2009-05-12
I'm specifically having a problem with the canonical repositorie for Jaunty Releases. Is there any way to get an updated/original key for that repository?

---

### Post by _Purple_ on 2009-05-12
Can you post the exact error message?

---

### Post by z|x on 2009-05-12
this is the error that i am receiving

```
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures were invalid: BADSIG 5A9BF3BB4E5E17B5 Launchpad PPA for chromium-daily
```

---

### Post by z|x on 2009-05-12
I just enabled another repository and i receive this error too:

```
W: GPG error: http://archive.ubuntu.com jaunty-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```

---

### Post by _Purple_ on 2009-05-12
Can you post the content of 
```
gedit /etc/apt/sources.list
```

---

### Post by z|x on 2009-05-12
```
# added by the release upgrader
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ jaunty main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ jaunty-security main universe restricted multiverse

#AUTOMATIX REPOS START







#AUTOMATIX REPOS END
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe main multiverse restricted

deb http://ppa.launchpad.net/tualatrix/ubuntu jaunty main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu jaunty main
deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
deb http://archive.ubuntu.com/ubuntu/ jaunty-backports universe main multiverse restricted
deb http://dl.google.com/linux/deb/ stable non-free #google
deb http://ppa.launchpad.net/transmissionbt/ubuntu jaunty main #transmission-gtk
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
```

---

### Post by _Purple_ on 2009-05-12
Try to run this command
```
sudo apt-get update -o Acquire::http::No-Cache=true
```

---

### Post by z|x on 2009-05-12
Thank you!

Also, some of the packages (e.g. chromium and a few others) are not able to recognize my distribution. So, under description of update, all i see is **_Failed to detect distribution_**.

Is there a way to fix that too?

---

### Post by _Purple_ on 2009-05-12
Do you need these repositories? If not, you can comment them.
```
deb http://ppa.launchpad.net/tualatrix/ubuntu jaunty main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu jaunty main
deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
deb http://dl.google.com/linux/deb/ stable non-free #google
deb http://ppa.launchpad.net/transmissionbt/ubuntu jaunty main #transmission-gtk
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
```

---

### Post by z|x on 2009-05-12
> **_Purple_ said:**
> Do you need these repositories? If not, you can comment them.
```
deb http://ppa.launchpad.net/tualatrix/ubuntu jaunty main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu jaunty main
deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
deb http://dl.google.com/linux/deb/ stable non-free #google
deb http://ppa.launchpad.net/transmissionbt/ubuntu jaunty main #transmission-gtk
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
```
yes, I use those softwares frequently. I need to keep them.

---

### Post by _Purple_ on 2009-05-12
> **z|x said:**
> Thank you!

Also, some of the packages (e.g. chromium and a few others) are not able to recognize my distribution. So, under description of update, all i see is **_Failed to detect distribution_**.

Is there a way to fix that too?

Aren't you using jaunty? Which packages are showing that error and can you please post the exact message?

---

### Post by z|x on 2009-05-12
Yes, i'm using jaunty. Its the chromium package that shows the error. It just says **_Failed to detect distribution_**.

That message comes after it tries to get the information. It could also be a problem with the server.

---

### Post by _Purple_ on 2009-05-12
May be you are getting these errors because they are still updating it. I think it's not stable yet.

---

### Post by z|x on 2009-05-12
yea that could be possible. thanks for the help!!

---

### Post by jhodge on 2009-12-11
I recently made a mistake in trying to add a wine repository souce.list.  Now I can't get any updates or download anything. In the terminal i keep getting a message 
"  E: Type '--2009-12-10'  is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list  " 

How do I reset my repositories to their original state?

---

### Post by Techrocket9 on 2011-04-12
I also seem to be having some repository problems. When I attempt a sudo apt-get update I get this at the end:
```
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```


My sources.list is as follows:
```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release Candidate amd64 (20100928)]/ maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick restricted universe main
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick restricted multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates restricted universe main
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates restricted multiverse #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security restricted universe main
deb-src http://security.ubuntu.com/ubuntu maverick-security restricted multiverse #Added by software-properties
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
```

I attempted sudo apt-get update -o Acquire::http::No-Cache=true because it seemed to help Z|X, but I get the same error.

I would appreciate some advice for fixing this.


(Also yes, I am running Maverick)

---

