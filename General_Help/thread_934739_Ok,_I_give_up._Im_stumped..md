---
title: "Ok, I give up. Im stumped."
date: 2008-09-30
forum: General Help
---

### Post by Rival904 on 2008-09-30
I get 
```
checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.17.6    atk >= 1.13.0    pango >= 1.20    cairo >= 1.6) were not met:

Requested 'glib-2.0 >= 2.17.6' but version of GLib is 2.16.4

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

``` 

When trying to install GTK. Now if I am reading correctly, I have the latest version of glib. What do I do from here?

---

### Post by Meow27 on 2008-09-30
are you using a libgtk.deb ?

---

### Post by Rival904 on 2008-09-30
Considering I have no idea, I will say no.

---

### Post by anjilslaire on 2008-10-01
> 
checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= **2.17.6**    atk >= 1.13.0    pango >= 1.20    cairo >= 1.6) were not met:

Requested '**glib-2.0 >= 2.17.6' but version of GLib is 2.16.4**


It says you need to have Glib 2.17.6 or higher, but you only have 2.16.4. You may need to manually upgrade glib before proceeding. Try here:
[https://launchpad.net/ubuntu/intrepid/i386/libglib2.0-0/2.17.6-0ubuntu1]("https://launchpad.net/ubuntu/intrepid/i386/libglib2.0-0/2.17.6-0ubuntu1")

---

### Post by ryanhaigh on 2008-10-01
> **Rival904 said:**
> Considering I have no idea, I will say no.

How are you trying to install gtk? Are you using apt-get/adept?

---

### Post by mc4man on 2008-10-01
Requested 'glib-2.0 >= [COLOR="Red"]2.17.6[/COLOR]' but version of GLib is 2.16.4
That minimum version number is suggesting you've downloaded a package and are trying to install it. If so just delete it and use adept package manager as was mentioned in previous post.

(i would think that min. ver. # would only show up on a libgtk2.0 package for mipsel architecture

---

### Post by Rival904 on 2008-10-01
I dont get anything that relates to GTK when I search it in add/remove programs.

---

### Post by damis648 on 2008-10-01
Are you using/installed MacMenu?

---

### Post by Yellow Pasque on 2008-10-01
How are you trying to install gtk? Have you added 3rd-party or (K)Ubuntu 8.10 repos?
```
sudo apt-get install libgtk2.0
```
I personally would not recommend trying to install a later version of libglib. Mixing and matching libs from different releases (e.g. 8.04 and 8.10) is a great way to hose your install and waste hours trying to get all the package versions to agree again.

---

### Post by louieb on 2008-10-01
> **Rival904 said:**
> I dont get anything that relates to GTK when I search it in add/remove programs.
use System>Administration>Synaptic 

Probably looking for libgtk2.0-dev

---

### Post by Rival904 on 2008-10-01
> **Temüjin said:**
> How are you trying to install gtk? Have you added 3rd-party or (K)Ubuntu 8.10 repos?
```
sudo apt-get install libgtk2.0
```
I personally would not recommend trying to install a later version of libglib. Mixing and matching libs from different releases (e.g. 8.04 and 8.10) is a great way to hose your install and waste hours trying to get all the package versions to agree again.

I get an error, couldnt find package

---

### Post by anjilslaire on 2008-10-01
So what is it you're trying to install that requires this, anyway?

---

### Post by Yellow Pasque on 2008-10-01
Please post output of:
```
cat /etc/apt/sources.list
```

---

### Post by mc4man on 2008-10-02
@ Rival904
Why don't you take a moment and post if you are using Kubuntu (as the tag on your thread suggests) or Ubuntu.

Also post as suggested your sources list.

And what is the *exact name* of the package your trying to install and how *exactly how are you trying to install it.* (and why

> sudo apt-get install libgtk2.0
That can't work, the name is libgtk2.0-0

---

### Post by Yellow Pasque on 2008-10-02
> That can't work, the name is libgtk2.0-0
/me double checks. Indeed, it is. Thanks for the correction.

---

### Post by Rival904 on 2008-10-02
I am using Kubuntu, and will post the output in an hour or so when I get home.

---

### Post by Rival904 on 2008-10-02
> **Temüjin said:**
> Please post output of:
```
cat /etc/apt/sources.list
```

```

deb cdrom:[Kubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701.2)]/ hardy main
 restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted u                                                                                                                          niverse multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
matt@matt-desktop:~$


```

---

### Post by Yellow Pasque on 2008-10-02
It looks like you have all the oficial repos in there. It really puzzles me why you can't find libgtk2.0-0 or libgtk2.0-dev

---

### Post by Rival904 on 2008-10-02
> **Temüjin said:**
> It looks like you have all the oficial repos in there. It really puzzles me why you can't find libgtk2.0-0 or libgtk2.0-dev

When I did libgtk2.0-0 I got

```

[sudo] password for matt:
Reading package lists... Done
Building dependency tree
Reading state information... Done
libgtk2.0-0 is already the newest version.


```

---

### Post by Yellow Pasque on 2008-10-02
Ok, so is your issue solved?

---

### Post by Rival904 on 2008-10-02
> **Temüjin said:**
> Ok, so is your issue solved?

Yes, it appears my problems with gtk are fixed but I still cant get airsnort to install for whatever reason. I cd'd to the directory, then ran sudo ./configure, then tried to launch it by cd'ing out of the dir and typing "airsnort" with no luck, then went back to the dir and tried to run "make" and "make install" both resulting in errors. :confused:

---

### Post by Yellow Pasque on 2008-10-02
What are you doing with airsnort? Sniffing out WEP passwords seems a bit shady to me, even if the flaw is well-known.

---

