---
title: "Help upgrading Firefox"
date: 2008-08-05
forum: General Help
---

### Post by kramer2718 on 2008-08-05
Hi.  I'm trying to upgrade Firefox using apt-get.  So I run the following:

$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  firefox
1 upgraded, 0 newly installed, 0 to remove and 139 not upgraded.
Need to get 65.9kB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main firefox 3.0.1+build1+nobinonly-0ubuntu0.8.04.3 [65.9kB]
Fetched 65.9kB in 1s (60.1kB/s)
(Reading database ... 142604 files and directories currently installed.)
Preparing to replace firefox 3.0+nobinonly-0ubuntu0.8.04.1 (using .../firefox_3.0.1+build1+nobinonly-0ubuntu0.8.04.3_all.deb) ...
Unpacking replacement firefox ...
Setting up firefox (3.0.1+build1+nobinonly-0ubuntu0.8.04.3) ...


Looks like success, right?  So I start up ff and see that the version is still 3b5.  So I check the executable and see:

$ ls -l /usr/bin/firefox-3.0
lrwxrwxrwx 1 root root 31 2008-06-03 00:38 /usr/bin/firefox-3.0 -> ../lib/firefox-3.0b5/firefox.sh

So I thought that I could just point the symlink somewhere else, but:

$ find /usr/bin /usr/lib -name firefox*
/usr/bin/firefox
/usr/bin/firefox-3.0
/usr/lib/firefox
/usr/lib/firefox-addons
/usr/lib/firefox-3.0b5
/usr/lib/firefox-3.0b5/firefox.sh
/usr/lib/firefox-3.0b5/firefox-3.0-restart-required.update-notifier
/usr/lib/firefox-3.0b5/firefox
/usr/lib/firefox-3.0b5/defaults/preferences/firefox-branding.js
/usr/lib/firefox-3.0b5/defaults/preferences/firefox.js
/usr/lib/firefox-3.0b5/defaults/preferences/firefox-l10n.js
/usr/lib/firefox-3.0b5/firefox.cfg


and nothing else.  Did I miss something?  Don't tell me I have to reboot.  I'm running 64 bit Ubuntu Server 8.04 with kubuntu desktop installed not Windblows.

Any help would be apprectiated.

---

### Post by kahlil88 on 2008-08-05
How strange...perhaps you should try reinstalling it: **sudo apt-get --reinstall install firefox**
You might also consider switching to [Swiftweasel]("http://swiftweasel.tuxfamily.org"), which is an optimized build of Firefox. Starts up quite a bit faster!

---

### Post by kramer2718 on 2008-08-08
Didn't work.  Tried all of these:

sudo apt-get update
sudo apt-get --reinstall install firefox
sudo apt-get upgrade as well
sudo apt-get install firefox-3.0



I'd rather use the main package than swift weasel.  Manual package dl not required, etc. Anyone else have any ideas?

---

### Post by gjoellee on 2008-08-08
remove firefox and click on the link below:
[apt://firefox3]("apt://firefox")

---

### Post by kramer2718 on 2008-08-12
apt://firefox ... finally worked.

Thanks very much.  What did that do different any way?

---

