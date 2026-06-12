---
title: "Could not download all repository indexes"
date: 2009-04-01
forum: Installation &amp; Upgrades
---

### Post by Zekes on 2009-04-01
Hello
I recently switched to ubuntu and I'm receiving this error during updates:

Could not download all repository indexes 

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFFGPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 084AF32EC2A6B0B1Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz)  404 Not Found [IP: 204.9.165.83 80]
Some index files failed to download, they have been ignored, or old ones used instead.

I researched this error and found that other new users get this error also, I believe it has something to do with skype on the amd64, here is what I get in the terminal:

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb [http://apt.wicd.net](http://apt.wicd.net) intrepid extras
# Fingerprint reader support (fprint)
deb [http://ppa.launchpad.net/madman2k/ubuntu](http://ppa.launchpad.net/madman2k/ubuntu) hardy main restricted universe multiverse
# Fingerprint reader support (fprint)
deb [http://ppa.launchpad.net/madman2k/ubuntu](http://ppa.launchpad.net/madman2k/ubuntu) hardy main restricted universe multiverse
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
# deb [http://ppa.launchpad.net/googlegadgets/ubuntu](http://ppa.launchpad.net/googlegadgets/ubuntu) hardy main


Thanks in advance!!!

---

### Post by Partyboi2 on 2009-04-01
For the ppa keys you can add them by opening a terminal and
```
gpg --keyserver keyserver.ubuntu.com --recv 60D11217247D1CFFGPG
gpg --export --armor 60D11217247D1CFFGPG | sudo apt-key add -
```for the 2nd ppa

```
gpg --keyserver keyserver.ubuntu.com --recv 084AF32EC2A6B0B1
gpg --export --armor  084AF32EC2A6B0B1 | sudo apt-key add -
```

---

### Post by Zekes on 2009-04-01
Thanks! The second command worked but the first gave me this error:

zeke@zeke-laptop:~$ gpg --keyserver keyserver.ubuntu.com --recv 60D11217247D1CFFGPG
gpg: "60D11217247D1CFFGPG" not a key ID: skipping
zeke@zeke-laptop:~$ gpg --export --armor 60D11217247D1CFFGPG | sudo apt-key add -
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.
zeke@zeke-laptop:~$

---

### Post by Partyboi2 on 2009-04-01
Sorry my mistake the 2nd one might not be a ppa.

Edit: looking again at the OP they are both PPA's (brain is on holiday)

---

### Post by Zekes on 2009-04-01
Ppa?

---

### Post by Partyboi2 on 2009-04-01
PPA =Personal Package Archives. I am not sure why the first one is not working.

---

### Post by Zekes on 2009-04-01
Oh I see. So will this prevent other updates from installing?

---

### Post by Partyboi2 on 2009-04-01
No it will just tell you that some updates are unable to be authenticated and give you the option to install them without them being authenticated.
I just noticed that you have 2 entries for > deb [http://ppa.launchpad.net/madman2k/ubuntu](http://ppa.launchpad.net/madman2k/ubuntu) hardy main restricted universe multiverse in your sources.list and that they are for hardy. Mixing repos from different ubuntu releases eg hardy with intrepid can cause problems I would suggest deleting one and changing the other too
> deb [http://ppa.launchpad.net/madman2k/ubuntu](http://ppa.launchpad.net/madman2k/ubuntu) intrepid main restricted universe multiversethen try running
```
 sudo apt-get update
```

---

### Post by Zekes on 2009-04-01
sorry to bug but can you walk me through how to do this.

---

### Post by Partyboi2 on 2009-04-01
Sure I can do that, open a terminal (Applications>Accessories>Terminal) and type or paste
```
gksu gedit /etc/apt/sources.list
``` when the file opens look for 
```
deb [http://ppa.launchpad.net/madman2k/ubuntu](http://ppa.launchpad.net/madman2k/ubuntu) [COLOR=Red]hardy[/COLOR] main restricted universe multiverse 
``` and replace the word [COLOR=Red]hardy[/COLOR] with [COLOR=Blue]intrepid[/COLOR] so it will become
                             ```
deb [http://ppa.launchpad.net/madman2k/ubuntu](http://ppa.launchpad.net/madman2k/ubuntu) [COLOR=Blue]intrepid[/COLOR] main restricted universe multiverse                      
```Then look for the 2nd entry of ```
deb [http://ppa.launchpad.net/madman2k/ubuntu](http://ppa.launchpad.net/madman2k/ubuntu) hardy main restricted universe multiverse 
```and delete it, then save the changes and close gedit. Then back in the terminal type
```
sudo apt-get update
```

---

### Post by Zekes on 2009-04-01
This seems to have work, however now when I run the update manager, it downloads the files but does not give me the option to install.

---

### Post by Vico Vicario on 2009-04-01
See next message.

V

---

### Post by Vico Vicario on 2009-04-01
I mean

gpg --keyserver keyserver.ubuntu.com --recv 60D11217247D1CFF
gpg --export --armor 60D11217247D1CFF | sudo apt-key add -

V

---

### Post by Zekes on 2009-04-01
Thanks, the command works but I still am not able to install when I run the update manager.

---

### Post by Partyboi2 on 2009-04-01
> This seems to have work, however now when I run the update manager, it downloads the files but does not give me the option to install. After the updates  have downloaded they should  install automatically.

---

