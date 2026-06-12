---
title: "[SOLVED] Error Message"
date: 2008-08-14
forum: General Help
---

### Post by Farajamo on 2008-08-14
It appears in my top toolbar and I have no idea what it is. When I hover over it, it says:

An error occured, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error: Opening the cache (E:Type '--15:58:12--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not have been read.)'This usually means that your installed packages have unmet dependencies.

When I open Package Manager, I get:

E:Type '--15:58:12--' is not known on line1 in source list /etc/apt/sources.list.d/medibuntu.list
E:The list of sources could not be read.
Go to the repository dialog to correct the problem.
E:_cache->open() failed, please report.

If I click the button reporting the error, I get:

**Could not initialize the package information**
A unresolvable problem occurred while initializing the package information.
Please report this bug against the 'update-manager' packer and include the following message:
'E:Type '--15:58:12--' is not known on line 1 in the source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.'

Any ideas? Thanks

---

### Post by jpeirce on 2008-08-14
Post your /etc/apt/sources.list.d/medibuntu.list file here and I'll see if I can help.

---

### Post by Farajamo on 2008-08-14
--15:58:12--  [http://www.medibuntu.org/sources.list.d/hard.list](http://www.medibuntu.org/sources.list.d/hard.list)
           => `hard.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
15:58:18 ERROR 404: Not Found.

---

### Post by Farajamo on 2008-08-14
Anything yet?

---

### Post by Farajamo on 2008-08-14
Can someone please help? I can't apt-get, synaptic, or add/remove anything!

---

### Post by jerome1232 on 2008-08-15
Well that is obviously messed up try renaming it and rerunning apt-get, if that doesn't solve it you can put it back.

```
sudo mv /etc/apt/sources.list.d/medibuntu.list ~/.medibuntu.list.bck
/etc/apt/sources.list.d/medibuntu.list
```
you can restore the old repostiory like this
```
sudo mv ~/.medibuntu.list.bck /etc/apt/sources.list.d/medibuntu.list
```

perhaps posting your /etc/apt/sources.list file will be of use if the above doesn't solve it

edit fixed typo in commands

---

### Post by Farajamo on 2008-08-15
Both of those got me that the file or directory doesn't exist.

my etc/apt/sources.list shows:

#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by jerome1232 on 2008-08-15
Hmmm your sources.list looks fine try my commands again I made a typo and have corrected it.

```
mv /etc/apt/sources.list.d/medibuntu.list ~/.mediubuntu.list.bck
```

I accidentally added a directory to the destination, forgetting that mv won't just create it for you.

---

### Post by Farajamo on 2008-08-15
I didn't have permission, so I did "sudo mv" and it worked! All better now. Thanks a bunch!

---

### Post by jerome1232 on 2008-08-15
Well since it worked unless you have some reason to keep that file that broke apt, you can safely remove it.

You can give yourself ownership then remove it (just to not use sudo and rm together) the only reason I do it this way is I really try and steer away from using sudo and rm together, a typo could be dire.

```
sudo chown $USER:$USER ~/.medibuntu.list.bck
rm ~/.medibuntu.list.bck
```

of course you could just sudo rm ~/.medibuntu.list.bck but I stay away from that.

---

