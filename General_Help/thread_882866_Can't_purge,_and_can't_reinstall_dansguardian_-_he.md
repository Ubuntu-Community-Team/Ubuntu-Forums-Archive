---
title: "Can't purge, and can't reinstall dansguardian - help!"
date: 2008-08-07
forum: General Help
---

### Post by pianoboy3333 on 2008-08-07
I don't need dansguardian anymore, but somehow the package broke, and I can't remove it:

```

$ sudo apt-get remove --purge dansguardian
[sudo] password for alex:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  guile-1.8 libxine1-x libxine1-misc-plugins libxcb-xv0 guile-1.8-libs libxcb1
  libxcb-shape0 libxine1-gnome libxine1-plugins python-cups dbus-x11
  libxcb-shm0 texinfo libntfs-3g12 libxine1-console libxine1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  dansguardian*
0 upgraded, 0 newly installed, 1 to remove and 72 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1536kB disk space will be freed.
Do you want to continue [Y/n]? Y
dpkg: error processing dansguardian (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 dansguardian
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
```

$ sudo apt-get install --reinstall dansguardian
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  guile-1.8 libxine1-x libxine1-misc-plugins libxcb-xv0 guile-1.8-libs libxcb1
  libxcb-shape0 libxine1-gnome libxine1-plugins python-cups dbus-x11
  libxcb-shm0 texinfo libntfs-3g12 libxine1-console libxine1
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  dansguardian
1 upgraded, 0 newly installed, 0 to remove and 72 not upgraded.
1 not fully installed or removed.
Need to get 0B/296kB of archives.
After unpacking 0B of additional disk space will be used.
Selecting previously deselected package dansguardian.
(Reading database ... 165593 files and directories currently installed.)
Preparing to replace dansguardian 2.8.0.6-antivirus-6.4.4.1-4 (using .../dansguardian_2.8.0.6-antivirus-6.4.4.1-4build1~gutsy2_i386.deb) ...
Stopping DansGuardian: dansguardian.
/etc/init.d/dansguardian: 71: /usr/local/apps/parental-control/./dansguardian_log.pl: not found
invoke-rc.d: initscript dansguardian, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
Stopping DansGuardian: dansguardian.
/etc/init.d/dansguardian: 71: /usr/local/apps/parental-control/./dansguardian_log.pl: not found
invoke-rc.d: initscript dansguardian, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/dansguardian_2.8.0.6-antivirus-6.4.4.1-4build1~gutsy2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
Starting DansGuardian: Error reading file: /etc/dansguardian/blacklists/ads/urls
Error reading file: /etc/dansguardian/blacklists/ads/urls
Error opening file:/etc/dansguardian/blacklists/ads/urls
Error opening bannedurllist
Error opening filter list:/etc/dansguardian/dansguardianf1.conf
Error reading filter group conf file(s).
Error parsing the dansguardian.conf file or other DansGuardian configuration files
invoke-rc.d: initscript dansguardian, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/dansguardian_2.8.0.6-antivirus-6.4.4.1-4build1~gutsy2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Can anyone help me out?

---

### Post by cariboo on 2008-08-07
This may help with your prblem. Go to System-->Administration-->Synaptic Package Manager-->Edit-->Fix broken packages.

Jim

---

### Post by pianoboy3333 on 2008-08-07
> **cariboo907 said:**
> This may help with your prblem. Go to System-->Administration-->Synaptic Package Manager-->Edit-->Fix broken packages.

Jim

It doesn't help because the package isn't under the broken filter...

---

### Post by pianoboy3333 on 2008-08-07
bump

---

### Post by bodhi.zazen on 2008-08-07
Try :

sudo dpkg --remove --force-remove-reinstreq dansguardian

---

### Post by msimpson3 on 2008-08-07
I'm having the same issue, doesn't matter what I try to install or remove or upgrade, nothing shows up in broken packages.

whenever i try to install anything via apt-get or aptitude or the package manager i get something along the lines of...

```
Setting up initramfs-tools (0.85eubuntu39.1) ...
cp: cannot create regular file `/etc/initramfs-tools/': Is a directory
dpkg: error processing initramfs-tools (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

been searching forums after forums with now luck at all.

please any advice would be awesome, very strange why it stopped working.

---

### Post by pianoboy3333 on 2008-08-07
> **bodhi.zazen said:**
> Try :

sudo dpkg --remove --force-remove-reinstreq dansguardian

didn't work:
```

$ sudo dpkg --remove --force-remove-reinstreq dansguardian
[sudo] password for alex:
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 165592 files and directories currently installed.)
Removing dansguardian ...
Stopping DansGuardian: dansguardian.
/etc/init.d/dansguardian: 71: /usr/local/apps/parental-control/./dansguardian_log.pl: not found
invoke-rc.d: initscript dansguardian, action "stop" failed.
dpkg: error processing dansguardian (--remove):
 subprocess pre-removal script returned error exit status 127
Starting DansGuardian: Error reading file: /etc/dansguardian/blacklists/ads/urls
Error reading file: /etc/dansguardian/blacklists/ads/urls
Error opening file:/etc/dansguardian/blacklists/ads/urls
Error opening bannedurllist
Error opening filter list:/etc/dansguardian/dansguardianf1.conf
Error reading filter group conf file(s).
Error parsing the dansguardian.conf file or other DansGuardian configuration files
invoke-rc.d: initscript dansguardian, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dansguardian

```

---

### Post by bodhi.zazen on 2008-08-07
```
sudo dpkg --purge --force-all dansguardian
```

---

### Post by pianoboy3333 on 2008-08-07
> **bodhi.zazen said:**
> ```
sudo dpkg --purge --force-all dansguardian
```

same error:
```

$ sudo dpkg --purge --force-all dansguardian
[sudo] password for alex:
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 165592 files and directories currently installed.)
Removing dansguardian ...
Stopping DansGuardian: dansguardian.
/etc/init.d/dansguardian: 71: /usr/local/apps/parental-control/./dansguardian_log.pl: not found
invoke-rc.d: initscript dansguardian, action "stop" failed.
dpkg: error processing dansguardian (--purge):
 subprocess pre-removal script returned error exit status 127
Starting DansGuardian: Error reading file: /etc/dansguardian/blacklists/ads/urls
Error reading file: /etc/dansguardian/blacklists/ads/urls
Error opening file:/etc/dansguardian/blacklists/ads/urls
Error opening bannedurllist
Error opening filter list:/etc/dansguardian/dansguardianf1.conf
Error reading filter group conf file(s).
Error parsing the dansguardian.conf file or other DansGuardian configuration files
invoke-rc.d: initscript dansguardian, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dansguardian

```

---

### Post by bodhi.zazen on 2008-08-07
Lets see if we can fool it then :twisted:

```
sudo mdkir -P /etc/dansguardian/blacklists/ads/

# If the forst command give you an error, keep going ...

sudo touch /etc/dansguardian/blacklists/ads/urls
sudo touch /etc/dansguardian/dansguardianf1.conf
[FONT=monospace]
[/FONT]sudo dpkg --purge --force-all dansguardian
```

---

### Post by pianoboy3333 on 2008-08-07
> **bodhi.zazen said:**
> Lets see if we can fool it then :twisted:

```
sudo mdkir -P /etc/dansguardian/blacklists/ads/

# If the forst command give you an error, keep going ...

sudo touch /etc/dansguardian/blacklists/ads/urls
sudo touch /etc/dansguardian/dansguardianf1.conf
[FONT=monospace]
[/FONT]sudo dpkg --purge --force-all dansguardian
```

mkdir -P doesn't exist - what's P supposed to do?

sudo touch /etc/dansguardian/blacklists/ads/urls didn't work, the second touch command did but then the dpkg command ended up just as the other did before

---

### Post by bodhi.zazen on 2008-08-07
the -P is make parent directories, and it is -p (small p), my mistake lol

```
sudo mdkir -p /etc/dansguardian/blacklists/ads/

If the forst command give you an error, keep going ...

sudo touch /etc/dansguardian/blacklists/ads/urls
sudo touch /etc/dansguardian/dansguardianf1.conf

sudo dpkg --purge --force-all dansguardian
```

---

### Post by pianoboy3333 on 2008-08-07
> **bodhi.zazen said:**
> the -P is make parent directories, and it is -p (small p), my mistake lol

```
sudo mdkir -p /etc/dansguardian/blacklists/ads/

If the forst command give you an error, keep going ...

sudo touch /etc/dansguardian/blacklists/ads/urls
sudo touch /etc/dansguardian/dansguardianf1.conf

sudo dpkg --purge --force-all dansguardian
```

still not working...
```

$ sudo mdkir -p /etc/dansguardian/blacklists/ads/
[sudo] password for alex:
sudo: mdkir: command not found
alex@dell9150:~$ sudo mkdir -p /etc/dansguardian/blacklists/ads/
alex@dell9150:~$ sudo touch /etc/dansguardian/blacklists/ads/urls
alex@dell9150:~$ sudo touch /etc/dansguardian/dansguardianf1.conf
alex@dell9150:~$ sudo dpkg --purge --force-all dansguardian
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 165592 files and directories currently installed.)
Removing dansguardian ...
Stopping DansGuardian: dansguardian.
/etc/init.d/dansguardian: 71: /usr/local/apps/parental-control/./dansguardian_log.pl: not found
invoke-rc.d: initscript dansguardian, action "stop" failed.
dpkg: error processing dansguardian (--purge):
 subprocess pre-removal script returned error exit status 127
Starting DansGuardian: Error reading file: /etc/dansguardian/blacklists/adult/urls
Error reading file: /etc/dansguardian/blacklists/adult/urls
Error opening file:/etc/dansguardian/blacklists/adult/urls
Error opening bannedurllist
Error opening filter list:/etc/dansguardian/dansguardianf1.conf
Error reading filter group conf file(s).
Error parsing the dansguardian.conf file or other DansGuardian configuration files
invoke-rc.d: initscript dansguardian, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dansguardian

```

---

### Post by damoxc on 2008-08-07
Looks to me like it's not removing because the init script is broken. Try ```
sudo touch /etc/init.d/dansguardian
```

Edit:
And then of course:
```
sudo dpkg --purge --force-all dansguardian
```

---

### Post by pianoboy3333 on 2008-08-07
> **damoxc said:**
> Looks to me like it's not removing because the init script is broken. Try ```
sudo touch /etc/init.d/dansguardian
```

Edit:
And then of course:
```
sudo dpkg --purge --force-all dansguardian
```

Still a no-go
```

$ sudo touch /etc/init.d/dansguardian
$ sudo dpkg --purge --force-all dansguardian
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 165592 files and directories currently installed.)
Removing dansguardian ...
Stopping DansGuardian: dansguardian.
/etc/init.d/dansguardian: 71: /usr/local/apps/parental-control/./dansguardian_log.pl: not found
invoke-rc.d: initscript dansguardian, action "stop" failed.
dpkg: error processing dansguardian (--purge):
 subprocess pre-removal script returned error exit status 127
Starting DansGuardian: Error reading file: /etc/dansguardian/blacklists/adult/urls
Error reading file: /etc/dansguardian/blacklists/adult/urls
Error opening file:/etc/dansguardian/blacklists/adult/urls
Error opening bannedurllist
Error opening filter list:/etc/dansguardian/dansguardianf1.conf
Error reading filter group conf file(s).
Error parsing the dansguardian.conf file or other DansGuardian configuration files
invoke-rc.d: initscript dansguardian, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dansguardian

```

---

### Post by damoxc on 2008-08-07
hmm, ok try:
```
nano /etc/init.d/dansguardian
```

and stick `exit 0` on the first line. This will guarantee a successful return so the script won't fail and dpkg will think it's stopped and it should remove then. The init script is what's causing the issue.

---

### Post by pianoboy3333 on 2008-08-07
> **damoxc said:**
> hmm, ok try:
```
nano /etc/init.d/dansguardian
```

and stick `exit 0` on the first line. This will guarantee a successful return so the script won't fail and dpkg will think it's stopped and it should remove then. The init script is what's causing the issue.

bingo! Thank you all for helping me, the problem is now solved.

---

