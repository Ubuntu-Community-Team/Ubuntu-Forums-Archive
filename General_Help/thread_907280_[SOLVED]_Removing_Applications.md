---
title: "[SOLVED] Removing Applications"
date: 2008-09-01
forum: General Help
---

### Post by Evolution-06 on 2008-09-01
So I have compiled and installed several applications.
I would like a guide on how to remove such apps.

I tried a brief google search and forum search, but this is the guide I used to install: [http://nagios.sourceforge.net/docs/3_0/quickstart-ubuntu.html](http://nagios.sourceforge.net/docs/3_0/quickstart-ubuntu.html)

Thanks!

---

### Post by tuxxy on 2008-09-01
anything you installed using apt-get you can search for in synaptic and select remove or reuse the commands you already entered into terminal but change the install to remove.

Anything else depending on what you installed, there could be an uninstaller script located in the applications installation folder

---

### Post by oldos2er on 2008-09-01
If you installed these compiled programs with "sudo make install,' go to the same directory and use the command "sudo make uninstall".

---

### Post by Evolution-06 on 2008-09-01
> **oldos2er said:**
> If you installed these compiled programs with "sudo make install,' go to the same directory and use the command "sudo make uninstall".

this is what i wanted to hear, however it didnt work.

```
make: *** No rule to make target `uninstall'.  Stop.
```

```
spillman@MINDKILLER:~/downloads/nagios-3.0.2$ ls -la
total 700
drwxrwxr-x 11 nagios nagios   4096 2008-08-29 19:23 .
drwxr-xr-x  4 root   root     4096 2008-08-28 22:18 ..
drwxrwxr-x  2 nagios nagios   4096 2008-08-29 19:23 base
drwxrwxr-x  2 nagios nagios   4096 2008-08-29 19:23 cgi
-rw-rw-r--  1 nagios nagios  24727 2008-05-19 14:42 Changelog
drwxrwxr-x  2 nagios nagios   4096 2008-08-29 19:23 common
-rwxrwxr-x  1 nagios nagios  44483 2006-12-14 00:25 config.guess
-rw-r--r--  1 root   root    58252 2008-08-29 19:23 config.log
-rwxr-xr-x  1 root   root    39632 2008-08-29 19:23 config.status
-rwxrwxr-x  1 nagios nagios  32619 2006-12-14 00:25 config.sub
-rwxrwxr-x  1 nagios nagios 236317 2008-05-19 14:42 configure
-rw-rw-r--  1 nagios nagios  26097 2008-05-19 14:42 configure.in
drwxrwxr-x  3 nagios nagios   4096 2008-08-29 19:23 contrib
-rw-rw-r--  1 nagios nagios    114 2007-10-18 14:25 .cvsignore
-rw-r--r--  1 root   root     5172 2008-08-29 19:23 daemon-init
-rw-rw-r--  1 nagios nagios   5152 2007-12-13 12:29 daemon-init.in
-rwxrwxr-x  1 nagios nagios   7025 2002-02-25 23:03 functions
-rw-rw-r--  1 nagios nagios    115 2007-10-21 09:24 .gitignore
drwxrwxr-x  8 nagios nagios   4096 2008-08-29 19:23 html
drwxrwxr-x  2 nagios nagios   4096 2008-08-29 19:23 include
-rw-rw-r--  1 nagios nagios    422 2007-03-06 14:55 INSTALLING
-rwxrwxr-x  1 nagios nagios   5869 2007-10-20 17:32 install-sh
-rw-rw-r--  1 nagios nagios    519 2007-10-31 13:35 LEGAL
-rw-rw-r--  1 nagios nagios  18002 2002-02-25 23:03 LICENSE
-rw-r--r--  1 root   root    10980 2008-08-29 19:23 Makefile
-rw-rw-r--  1 nagios nagios  10952 2008-04-13 14:34 Makefile.in
-rwxrwxr-x  1 nagios nagios    461 2002-08-13 01:18 make-tarball
-rwxrwxr-x  1 nagios nagios    818 2002-02-25 23:03 mkpackage
drwxrwxr-x  2 nagios nagios   4096 2008-08-29 19:23 module
-rw-rw-r--  1 nagios nagios  14899 2008-05-19 14:01 nagios.spec
-rw-rw-r--  1 nagios nagios    745 2002-02-25 23:03 OutputTrap.pm
-rw-rw-r--  1 nagios nagios  31878 2008-05-19 14:01 p1.pl
-rw-r--r--  1 root   root      202 2008-08-29 19:23 pkginfo
-rw-rw-r--  1 nagios nagios    210 2002-02-25 23:03 pkginfo.in
-rw-rw-r--  1 nagios nagios   1025 2007-03-06 14:55 README
drwxrwxr-x  3 nagios nagios   4096 2008-08-29 19:23 sample-config
-rw-r--r--  1 root   root     1258 2008-08-29 19:23 subst
-rwxrwxr-x  1 nagios nagios   1195 2007-04-17 17:52 subst.in
-rw-rw-r--  1 nagios nagios   3981 2008-05-19 14:01 THANKS
-rwxrwxr-x  1 nagios nagios   2389 2008-05-19 14:42 update-version
-rw-rw-r--  1 nagios nagios    331 2007-03-06 14:55 UPGRADING
drwxrwxr-x  2 nagios nagios   4096 2008-08-29 19:23 xdata

```

---

### Post by drs305 on 2008-09-01
Do you still have the folders created during the install. There is often a "postinst" folder or another with an uninstall script within it.

---

### Post by Evolution-06 on 2008-09-01
> **drs305 said:**
> Do you still have the folders created during the install. There is often a "postinst" folder or another with an uninstall script within it.

I have not removed any of the install directories yet.

```
spillman@MINDKILLER:/$ sudo find -name postinst
./usr/share/hwtest/install/postinst
./usr/share/doc/ucf/examples/postinst
./usr/share/doc/sgml-base/examples/postinst
spillman@MINDKILLER:/$ 

```

I guess i could do a search for the word nagios and then remove every trace that way?

---

### Post by drs305 on 2008-09-01
There is not always a postinst folder, just on occasion. I'd try a search for nagios folders first and inspect any that you find. Then nuke any 'nagios' if that doesn't work...

```
sudo find / -type d -iname *nagios*
```

Added: nagios2 is in synaptic. You can't get the installed files locations until you install it but you might do that and see where the files are installed.

---

### Post by Evolution-06 on 2008-09-01
> **drs305 said:**
> There is not always a postinst folder, just on occasion. I'd try a search for nagios folders first and inspect any that you find. Then nuke any 'nagios' if that doesn't work...

```
sudo find / -type d -iname *nagios*
```

Ill just do that, thats my old way of removing stuff that doesnt just apt or have uninstall script.  i am still relatively new to ubuntu.

everycouple months i have botched my install pretty bad and i reinstall ubuntu from scratch again.

I wish I was more careful of what i install on this thing, i seem to run into all sorts of conflicts.

---

### Post by knattlhuber on 2008-09-01
It won't help you a bit now, but in the future you could try 'checkinstall':

"Checkestall keeps track of all files installed by a "make install" or equivalent, creates a Slackware, RPM, or Debian package with those files, and adds it to the installed packages database, allowing for easy package removal or distribution."

See here: [https://help.ubuntu.com/community/CheckInstall]("https://help.ubuntu.com/community/CheckInstall")

---

### Post by Evolution-06 on 2008-09-01
> **knattlhuber said:**
> It won't help you a bit now, but in the future you could try 'checkinstall':

"Checkestall keeps track of all files installed by a "make install" or equivalent, creates a Slackware, RPM, or Debian package with those files, and adds it to the installed packages database, allowing for easy package removal or distribution."

See here: [https://help.ubuntu.com/community/CheckInstall]("https://help.ubuntu.com/community/CheckInstall")

thats a good tip too. thanks!

---

