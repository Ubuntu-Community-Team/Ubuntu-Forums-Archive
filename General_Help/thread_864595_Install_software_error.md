---
title: "Install software error"
date: 2008-07-19
forum: General Help
---

### Post by princekinTOT on 2008-07-19
an error is showed when I install 
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  unrar
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 97.6kB of archives.
After this operation, 246kB of additional disk space will be used.
Get:1 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy/multiverse unrar 1:3.7.8-1 [97.6kB]
Fetched 97.6kB in 0s (106kB/s)
(Reading database ... dpkg: error processing /var/cache/apt/archives/unrar_1%3a3.7.8-1_amd64.deb (--unpack):
 files list file for package `totem-plugins' contains empty filename
Errors were encountered while processing:
 /var/cache/apt/archives/unrar_1%3a3.7.8-1_amd64.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Pro-reason on 2008-07-19
Try this:

```

sudo apt-get -f install

```

---

### Post by Rocket2DMn on 2008-07-19
If that doesn't work, run
```
sudo rm /var/cache/apt/archives/unrar_1%3a3.7.8-1_amd64.deb
```
Then update/upgrade and try to reinstall
```
sudo apt-get update
sudo apt-get upgrade
```
Now try to install the package again.

---

### Post by princekinTOT on 2008-07-19
not work

---

### Post by Rocket2DMn on 2008-07-19
Can you please post the output of
```
cat /var/lib/dpkg/info/totem-plugins.list
```

---

### Post by Pro-reason on 2008-07-19
> **princekinTOT said:**
> not work

We need a bit more information than that.

---

### Post by princekinTOT on 2008-07-19
/.
/usr
/usr/lib
/usr/lib/totem
/usr/lib/totem/plugins
/usr/lib/totem/plugins/thumbnail
/usr/lib/totem/plugins/thumbnail/thumbnail.totem-plugin
/usr/lib/totem/plugins/thumbnail/libthumbnail.so
/usr/lib/totem/plugins/screensaver
/usr/lib/totem/plugins/screensaver/screensaver.totem-plugin
/usr/lib/totem/plugins/screensaver/libscreensaver.so
/usr/lib/totem/plugins/ontop
/usr/lib/totem/plugins/ontop/ontop.totem-plugin
/usr/lib/totem/plugins/ontop/libontop.so
/usr/lib/totem/plugins/lirc
/usr/lib/totem/plugins/lirc/lirc.totem-plugin
/usr/lib/totem/plugins/lirc/liblirc.so
/usr/lib/totem/plugins/media-player-keys
/usr/lib/totem/plugins/media-player-keys/media-player-keys.totem-plugin
/usr/lib/totem/plugins/media-player-keys/libmedia_player_keys.so
/usr/lib/totem/plugins/properties
/usr/lib/totem/plugins/properties/movie-properties.totem-plugin
/usr/lib/totem/plugins/properties/libmovie-properties.so
/usr/lib/totem/plugins/skipto
/usr/lib/totem/plugins/skipto/skipto.totem-plugin
/usr/lib/totem/plugins/skipto/libskipto.so
/usr/lib/totem/plugins/skipto/skipto.ui
/usr/lib/totem/plugins/bemused
/usr/lib/totem/plugins/bemused/libbemused.so
/usr/lib/totem/plugins/youtube
/usr/lib/totem/plugins/youtube/youtube.totem-plugin
/usr/lib/totem/plugins/youtube/youtube.py
/usr/lib/totem/plugins/youtube/youtube.ui
/usr/lib/totem/plugins/tracker
/usr/lib/totem/plugins/tracker/tracker.totem-plugin
/usr/lib/totem/plugins/tracker/libtracker.so
/usr/lib/totem/plugins/totem
/usr/lib/totem/plugins/totem/__init__.py
/usr/share
/usr/share/doc
/usr/share/doc/totem-plugins
/usr/share/doc/totem-plugins/README
/usr/share/doc/totem-plugins/copyright
/usr/share/doc/totem-plugins/NEWS.gz
/usr/share/doc/totem-plugins/changelog.Debian.gz

---

### Post by Rocket2DMn on 2008-07-19
OK, that didn't show us anything helpful since it looks OK (not your fault).  Please post the complete output of the following commands:
```
dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by princekinTOT on 2008-07-19
> **Rocket2DMn said:**
> OK, that didn't show us anything helpful since it looks OK (not your fault).  Please post the complete output of the following commands:
```
dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

princekin@princekin-desktop:~$ sudo dpkg --configure -a
princekin@princekin-desktop:~$ sudo apt-get undate
E: Invalid operation undate
princekin@princekin-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Rocket2DMn on 2008-07-19
The command is "sudo apt-get update", check your spelling.  Please run the commands again, then post the output.  After that, try to install your program again and post the output of that here, too.

---

### Post by princekinTOT on 2008-07-19
> **Rocket2DMn said:**
> The command is "sudo apt-get update", check your spelling.  Please run the commands again, then post the output.  After that, try to install your program again and post the output of that here, too.

```
princekin@princekin-desktop:~$ sudo dpkg --configure -a
princekin@princekin-desktop:~$ sudo apt-get update
Hit http://security.ubuntu.com hardy-security Release.gpg
Hit http://nz.archive.ubuntu.com hardy Release.gpg
Ign http://nz.archive.ubuntu.com hardy/main Translation-en_NZ
Ign http://nz.archive.ubuntu.com hardy/restricted Translation-en_NZ
Ign http://nz.archive.ubuntu.com hardy/universe Translation-en_NZ
Ign http://security.ubuntu.com hardy-security/main Translation-en_NZ
Ign http://nz.archive.ubuntu.com hardy/multiverse Translation-en_NZ
Hit http://nz.archive.ubuntu.com hardy-updates Release.gpg
Ign http://nz.archive.ubuntu.com hardy-updates/main Translation-en_NZ
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_NZ
Ign http://nz.archive.ubuntu.com hardy-updates/restricted Translation-en_NZ
Ign http://nz.archive.ubuntu.com hardy-updates/universe Translation-en_NZ
Ign http://security.ubuntu.com hardy-security/universe Translation-en_NZ
Ign http://nz.archive.ubuntu.com hardy-updates/multiverse Translation-en_NZ
Hit http://nz.archive.ubuntu.com hardy Release
Hit http://nz.archive.ubuntu.com hardy-updates Release
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_NZ
Hit http://security.ubuntu.com hardy-security Release
Hit http://nz.archive.ubuntu.com hardy/main Packages
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://nz.archive.ubuntu.com hardy/restricted Packages
Hit http://nz.archive.ubuntu.com hardy/main Sources
Hit http://nz.archive.ubuntu.com hardy/restricted Sources
Hit http://nz.archive.ubuntu.com hardy/universe Packages
Hit http://nz.archive.ubuntu.com hardy/universe Sources
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://nz.archive.ubuntu.com hardy/multiverse Packages
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://nz.archive.ubuntu.com hardy/multiverse Sources
Hit http://nz.archive.ubuntu.com hardy-updates/main Packages
Hit http://nz.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://nz.archive.ubuntu.com hardy-updates/main Sources
Hit http://nz.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://nz.archive.ubuntu.com hardy-updates/universe Packages
Hit http://nz.archive.ubuntu.com hardy-updates/universe Sources
Hit http://nz.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://nz.archive.ubuntu.com hardy-updates/multiverse Sources
Reading package lists... Done
princekin@princekin-desktop:~$ su do apt-get upgrade
Unknown id: do
princekin@princekin-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
princekin@princekin-desktop:~$ sudo apt-get install unrar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  unrar
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/97.6kB of archives.
After this operation, 246kB of additional disk space will be used.
(Reading database ... dpkg: error processing /var/cache/apt/archives/unrar_1%3a3.7.8-1_amd64.deb (--unpack):
 files list file for package `totem-plugins' contains empty filename
Errors were encountered while processing:
 /var/cache/apt/archives/unrar_1%3a3.7.8-1_amd64.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
princekin@princekin-desktop:~$ 

```

---

### Post by Rocket2DMn on 2008-07-19
OK, I'm assuming you ran the "rm" command I gave earlier, so let's try this.
```
sudo apt-get clean
sudo rm /var/cache/apt/archives/unrar*
sudo apt-get install unrar
```
If that doesn't work, purge and reinstall totem-plugins.
```
sudo apt-get remove --purge totem-plugins
sudo apt-get clean
sudo apt-get install totem-plugins
sudo apt-get install unrar
```

---

