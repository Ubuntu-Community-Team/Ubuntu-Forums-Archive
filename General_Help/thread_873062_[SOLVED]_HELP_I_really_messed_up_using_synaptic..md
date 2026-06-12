---
title: "[SOLVED] HELP I really messed up using synaptic."
date: 2008-07-28
forum: General Help
---

### Post by easybake on 2008-07-28
Yesterday I tried to uninstall kde through synaptic. Being the genius that I am I quickly went through and was un-marking everything that said kde on it. Long story short, I wasn't paying attention and it removed my entire Gnome environment and a bunch of other things like firefox, terminal, and a ton of others. 

I restarted and was met with a black terminal like screen. I was only able to install kde though it. It wouldn't let me install normal ubuntu. I am now using a live cd so I can use firefox.

When using kde, in terminal i tried to run ```
sudo apt-get install ubuntu-desktop
``` it said that I can't and I should run ```
apt-get -f install
``` When I try that, it says that I should run ```
apt-get autoremove
``` When I run that, it then it tells me to run ```
apt-get -f install
``` It's like a big circle.

I would stick with kde but it won't let me install firefox.

I would use the live cd to install Gnome again but I am hesitant because it botched the partitioning step last time and I was forced to do a clean install. 

I would really like gnome back.

Anyone know what I should do?

---

### Post by kuja on 2008-07-28
The apt-get autoremove part isn't essential, it's just a suggestion. The apt-get -f install however,, suggests that it has run into an error of some sort, and/or there are broken packages. 

Another command that might be worth running, if it stopped in the middle of an operation, might be ```
sudo dpkg --configure -a
```

P.S. Reinstalling the "ubuntu-desktop" package should do the trick, as soon as you fix your probable broken package situation.

---

### Post by zvacet on 2008-07-28
```
sudo dpkg --configure -a
sudo apt-get -f install
```

You can also try in **synaptic>edit tab>fix broken packages**.

---

### Post by easybake on 2008-07-29
I haven't tried the repair broken packages in synaptic. I ran the configure -a, it downloaded a few things, but after tried again and got this:
```
easybake@easybake-desktop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of konq-plugins:
 konq-plugins depends on konqueror (>= 4:3.5.8-1); however:
  Package konqueror is not installed.
dpkg: error processing konq-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of strigi-applet:
 strigi-applet depends on konqueror; however:
  Package konqueror is not installed.
dpkg: error processing strigi-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of konqueror-nsplugins:
 konqueror-nsplugins depends on konqueror; however:
  Package konqueror is not installed.
dpkg: error processing konqueror-nsplugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kmplayer-konq-plugins:
 kmplayer-konq-plugins depends on konqueror; however:
  Package konqueror is not installed.
dpkg: error processing kmplayer-konq-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kubuntu-desktop:
 kubuntu-desktop depends on konq-plugins; however:
  Package konq-plugins is not configured yet.
dpkg: error processing kubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 konq-plugins
 strigi-applet
 konqueror-nsplugins
 kmplayer-konq-plugins
 kubuntu-desktop
easybake@easybake-desktop:~$
```

when I run the install -f i get this.
```
easybake@easybake-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  anyevent-perl libsdl-ttf2.0-0 menu libwxbase2.6-0 libxml-sax-perl
  libevent-perl envyng-core nspluginwrapper libevent-rpc-perl
  python-compizconfig libgtk1.2 fb-music-high libfame-0.9 libsvga1
  libsdl-mixer1.2 libswscale1d libcrypt-ssleay-perl libpvm3
  libxml-namespacesupport-perl libiso9660-5 libpixman-1-dev
  libcommons-cli-java snes9x-x libxml-libxml-perl libxml-libxml-common-perl
  libdvbpsi4 libglitz-glx1 libxosd2 libevent-execflow-perl libvlc0
  recordmydesktop libsdl-image1.2 libgdl-1-common libenca0 mplayer-skins
  libxml-simple-perl vlc-nox libglib1.2ldbl libggi2 libnetfilter-queue1
  ogmtools libnfnetlink0 libgii1 libmatroska0 lsdvd ffmpeg libglitz1
  libsdl-console libgda3-common fping libsdl-gfx1.2-4 cabextract libdvdnav4
  libgii1-target-x frozen-bubble-data libfreezethaw-perl libsdl-net1.2
  libmozjs0d libsdl-perl libgtk1.2-common libnetpbm10 libgda3-3
  libcrypt-blowfish-perl libcommons-lang-java libtar libintl-perl libimlib2
  libvcdinfo0 libebml0 vlc-plugin-pulse libseda-java libsmpeg0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  konqueror
Suggested packages:
  gij-4.1 libgcj7-awt libjessie-java
The following NEW packages will be installed:
  konqueror
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
5 not fully installed or removed.
Need to get 0B/2072kB of archives.
After this operation, 6083kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 157522 files and directories currently installed.)
Unpacking konqueror (from .../konqueror_4%3a3.5.9-0ubuntu7.2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/konqueror_4%3a3.5.9-0ubuntu7.2_amd64.deb (--unpack):
 trying to overwrite `/usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop', which is also in package kio-umountwrapper
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/konqueror_4%3a3.5.9-0ubuntu7.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
easybake@easybake-desktop:~$ 
```

Any more help?

---

### Post by kuja on 2008-07-29
Maybe ....

```
sudo apt-get clean
sudo apt-get remove konq-plugins  strigi-applet  konqueror-nsplugins  kmplayer-konq-plugins  kubuntu-desktop konqueror
sudo apt-get autoremove
sudo apt-get install ubuntu-desktop
```

---

### Post by easybake on 2008-07-29
> **kuja said:**
> Maybe ....

```
sudo apt-get clean
sudo apt-get remove konq-plugins  strigi-applet  konqueror-nsplugins  kmplayer-konq-plugins  kubuntu-desktop konqueror
sudo apt-get autoremove
sudo apt-get install ubuntu-desktop
```

F-ing awesome man thank you. I was expecting to have to start from scratch on gnome but almost all my stuff is still there. I've only lost a couple things. Thanks a lot.

---

### Post by kuja on 2008-07-29
You're welcome :)

---

