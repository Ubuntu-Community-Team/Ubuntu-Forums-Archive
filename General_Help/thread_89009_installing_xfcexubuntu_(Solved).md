---
title: "installing xfce/xubuntu (Solved)"
date: 2005-11-11
forum: General Help
---

### Post by pickarooney on 2005-11-11
Not too impressed with GNOME currently and wanted to try out xfce.
I apt-got xubuntu-desktop but then got a dependency error 
```

The following packages have unmet dependencies:
  xubuntu-desktop: Depends: libglib2.0-data but it is not going to be installed

```

tried to install libglib2.0-data the same way and:
```

The following packages have unmet dependencies:
  libglib2.0-data: Depends: libglib2.0-0 (= 2.8.3-0ubuntu1) but 2.8.3-1 is to be installed

```

anyone know what I need to do?

---

### Post by Kyral on 2005-11-11
What repos do you have active...

NM....try

```
sudo apt-get -f install
```

---

### Post by pickarooney on 2005-11-11
I have these activated, **sudo apt-get -f install** didn't help.


```

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb http://nl.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nl.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://nl.archive.ubuntu.com/ubuntu breezy universe
deb-src http://nl.archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb http://nl.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
#deb-src http://nl.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ breezy main universe multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ breezy-updates main universe multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ breezy-security main universe multiverse restricted
deb http://acm.cs.umn.edu/ubp/ breezy-extras main universe multiverse restricted
deb ftp://ftp.nerim.net/debian-marillat/ sarge main
deb http://www.fs.tum.de/~bunk/debian woody/bunk-1 main contrib non-free

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

---

### Post by aysiu on 2005-11-11
Read the first link in my sig.
Then, ```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```

---

### Post by pickarooney on 2005-11-12
I get the exact same error after changing the sources.list file.
```

sudo apt-get install xubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xubuntu-desktop: Depends: libglib2.0-data but it is not going to be installed
E: Broken packages

```

---

### Post by aysiu on 2005-11-12
Did you follow the exact directions (i.e., paste **over** your entire old list--not just tack on)? And did you ```
sudo apt-get update
``` before trying to install xubuntu-desktop?

---

### Post by eyebrowman92 on 2005-11-12
xubuntu is xfce right? 

p.s. how is xubuntu pronounced? like zubuntu?

---

### Post by Xian on 2005-11-12
[QUOTE=eyebrowman92]p.s. how is xubuntu pronounced? like zubuntu?[/QUOTE]
I pronouce it, "Ex-Ubuntu". :)

---

### Post by eyebrowman92 on 2005-11-12
hah oh ok. i thought maybe it was pronounced like xcylaphone would be. alright i get it.

---

### Post by kelsey23 on 2005-11-12
A clean install of Breezy should have XFCE in it, and there should not be any package issues. 

sudo apt-get install xubuntu-desktop

It worked great for me :-)

---

### Post by andlinux21 on 2005-11-12
when you do the sudo apt-get install xubuntu-desktop will it replace the gnome as default?

---

### Post by aysiu on 2005-11-12
[QUOTE=kelsey23]A clean install of Breezy should have XFCE in it, and there should not be any package issues.[/QUOTE] That's not true. [xubuntu-desktop](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=breezy&release=all&keywords=xubuntu&sourceid=mozilla-search) is in the Universe repositories, which are not enabled by default.

[quote=andlinux21]
when you do the sudo apt-get install xubuntu-desktop will it replace the gnome as default?[/quote] No. It will just install it alongside Gnome. You'll need to log out, select the XFCE session, and log back in. When you log back in, it'll ask if you want to make XFCE your default session or not.

---

### Post by pickarooney on 2005-11-13
I appreciate your input, but if everyone is just going to keep telling me to do the same thing (which I've done, and it doesn't work), I'm not going to get this resolved.

To try another tack, how can I install this via synaptic?

---

### Post by taurus on 2005-11-13
I can tell you that "sudo apt-get install xubuntu-desktop" worked fine on my Breezy so that command should work unless there is something funny in your /etc/apt/sources.list!!!  You can also try to install Xfce4 with synaptic.  Fire it up and in the search field, type "xfce" and it will give you a list of files related to xfce...

---

### Post by Xian on 2005-11-13
[QUOTE=pickarooney]I appreciate your input, but if everyone is just going to keep telling me to do the same thing (which I've done, and it doesn't work), I'm not going to get this resolved.[/QUOTE]
Your sources.list is not compatable. 
Use the source list below instead.

Then do an 'apt-get update' session.
Next try the install xubuntu-desktop command again.

```
## Breezy Primary Repositories
deb http://archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

## Codecs & DVD
deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

```

---

### Post by taurus on 2005-11-13
breezy-backports is up now!!!  :confused:

---

### Post by pickarooney on 2005-11-13
Jesus wept, but you guys are stubborn! :D
Do I have to film myself doing the above and post it as an attachment or what is it going to take for you to understand that DOING THIS DOES NOT WORK FOR ME.

I'm going to try it through synaptic and let you know how I get on.

---

### Post by taurus on 2005-11-13
[QUOTE=pickarooney]Jesus wept, but you guys are stubborn! :D
Do I have to film myself doing the above and post it as an attachment or what is it going to take for you to understand that DOING THIS DOES NOT WORK FOR ME.

I'm going to try it through synaptic and let you know how I get on.[/QUOTE]
Do you know that you are NOT supposed to mix ubuntu breezy with debian sarge so better comment out the line with sarge in your /etc/apt/sources.list...    :rolleyes:

---

### Post by Xian on 2005-11-13
If the same source list won't produce the same result on different computers then there might be an ongoing incompatability with a package already installed from a non-standard source. Open Synaptic and goto the Status > Installed (Local or Obsolete) field. Look for packages that could be conflicting with your base system. Anything in that field is a possibility.

Other than this, you can always download the files which are needed directly from [Ubuntu Packages](http://packages.ubuntu.com/) and just install them locally by hand.

---

### Post by Xian on 2005-11-13
[QUOTE=taurus]Do you know that you are NOT supposed to mix ubuntu breezy with debian sarge so better comment out the line with sarge in your /etc/apt/sources.list...    :rolleyes:[/QUOTE]
The member is apparently telling us that they have used the fixed source list that has been provided instead of the one which was offered initially as an example.

---

### Post by pickarooney on 2005-11-13
Thanks Xian. Synaptic seems to have done the trick - I'm typing this from within XFCE. 
There's probably still some resident incompatibility, but I'll sort that out at a later date.

---

