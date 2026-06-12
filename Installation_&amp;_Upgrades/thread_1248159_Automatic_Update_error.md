---
title: "Automatic Update error"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by dudekaus on 2009-08-23
Hello All, 

The battery on my laptop died in the middle of the update and the next thing I know, there is a update error message. I google it but was unable to find the solution. 

The message says
[B]:Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 69 in source list /etc/apt/sources.list (dist), E:The list of sources could not be read.[/B]

I hope someone here will be kind enough to help me out. I have also attached the screenshot...

Thanks

---

### Post by hansdown on 2009-08-23
Hi dudekaus.

If you have good battery capacity, click system> administation> update manager.

You can check for updates, and if you get any error messages, please post them here.

---

### Post by dudekaus on 2009-08-23
Hey hansdown, 

I have posted the error message and attached the thumbnail as well in my first post. I have access to power chord now so  low battery is no longer a problem for me now.

---

### Post by hansdown on 2009-08-23
> **dudekaus said:**
> Hey hansdown, 

I have posted the error message and attached the thumbnail as well in my first post. I have access to power chord now so  low battery is no longer a problem for me now.

Yes, I saw that.

It's not exactly an error message.

Try the advice from my first post, and see if something more useful is given.

---

### Post by Rocket2DMn on 2009-08-23
Can you please post your sources.list file for us.  You can open it in a text editor:
```
gksudo gedit /etc/apt/sources.list
```
It sounds like line 69 isn't correctly formed, so we'll help you clean it up.

---

### Post by dudekaus on 2009-08-23
Her is the source list:

# Salimane Adjao Moustapha's Ubuntu Jaunty Jackalope 9.04 Sources list
#
# Repository List based on standard Jaunty with many extra packages
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number):
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you have a gpg key URL use (replace URL with the key address):
#
# wget -q [http://lut1n.ifrance.com/repo_key.asc](http://lut1n.ifrance.com/repo_key.asc) -O- | sudo apt-key add -
#
# If you have a gpg key file use (replace FILE with the key file):
#
# sudo apt-key add FILE
# Ubuntu supported packages
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-proposed main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-proposed main restricted universe multiverse
#Canonical Commercial Repository
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-backports partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-updates partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-security partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-proposed partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-backports partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-updates partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-security partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-proposed partner
#gnome-globalmenu
deb [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) jaunty main
#opera
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) lenny non-free
#skype
deb [http://download.skype.com/linux/repos/debian](http://download.skype.com/linux/repos/debian) stable non-free
#firefox
deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) jaunty main
#gnome-do
deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) jaunty main
#compiz-fusion
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) jaunty main
#google
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
#medibuntu
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
# MySQL Workbench
deb [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/) binary/
deb-src [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/) source/
# Depot PlayOnLinux
deb [http://deb.playonlinux.com/](http://deb.playonlinux.com/) jaunty main
# Ubuntu tweak
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) jaunty main
##Themes du ZgegBlog: Project Bisigi
deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main

deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) jaunty/
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/reposit](http://ftp.osuosl.org/pub/pculture.org/miro/linux/reposit)
ories/ubuntu jaunty/

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-free


Thanks a lot guys

---

### Post by drs305 on 2009-08-23
Here is the error:
> 
[COLOR="DarkRed"]deb [http://ftp.osuosl.org/pub/pculture.o...itories/ubuntu](http://ftp.osuosl.org/pub/pculture.o...itories/ubuntu) jaunty/
deb [http://ftp.osuosl.org/pub/pculture.o.../linux/reposit](http://ftp.osuosl.org/pub/pculture.o.../linux/reposit)
ories/ubuntu jaunty/[/COLOR]


Delete the lines or if you know what goes there, correct them.
```

gksudo gedit /etc/apt/sources.list

```

Then run:
```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by dudekaus on 2009-08-24
It worked perfectly thanks all.

---

### Post by dudekaus on 2009-08-28
Problem Help!

When Trying to update ubuntu I get following error message. Please help.

W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: [http://deb.opera.com](http://deb.opera.com) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAA
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE
W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/jaunty/Release.gpg](http://wine.budgetdedicated.com/apt/dists/jaunty/Release.gpg)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/jaunty/main/i18n/Translation-en_US.bz2](http://wine.budgetdedicated.com/apt/dists/jaunty/main/i18n/Translation-en_US.bz2)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.


 I use 9.04

---

### Post by stinger30au on 2009-08-28
> **dudekaus said:**
> Problem Help!

When Trying to update ubuntu I get following error message. Please help.

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/jaunty/main/i18n/Translation-en_US.bz2](http://wine.budgetdedicated.com/apt/dists/jaunty/main/i18n/Translation-en_US.bz2)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.


 I use 9.04

have you added the repo key???

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

read the bit that says trusting wine repos

if you have already done this and you still cant download the updates, the repos might be down for maintenance

---

