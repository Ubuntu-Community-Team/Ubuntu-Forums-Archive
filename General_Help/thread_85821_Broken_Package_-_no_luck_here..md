---
title: "Broken Package - no luck here."
date: 2005-11-03
forum: General Help
---

### Post by kylenewton on 2005-11-03
Heyall.

I've been stuck with this problem for a couple weeks now. Apperently I've got a broken package because when I try to update/upgrade in kynaptic/synaptic it tells me I've got a broken package.

When I try to work with apt-get I get funny errors.

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  firefox: Depends: mozilla-firefox but it is not installed
  mozilla-mplayer: Depends: mozilla-browser but it is not installed or
                            mozilla-firefox but it is not installed
E: Unmet dependencies. Try using -f.

sudo apt-get remove mozilla-mplayer
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  firefox: Depends: mozilla-firefox but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  mozilla-firefox
Suggested packages:
  mozilla-firefox-gnome-support latex-xft-fonts xprt-xprintorg
The following NEW packages will be installed:
  mozilla-firefox
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/8802kB of archives.
After unpacking 24.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/status' near line 19522 package `mozilla-firefox':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

And near line 19522 in /var/lib/dpkg/status is the following:

```
Package: mozilla-firefox
Status: purge ok installed
Priority: optional
Section: web
Architecture: all
```

But I have no firefox installed on my system. And I can't use any package managers while this problem exists. Please help. Thanks.

---

### Post by Xian on 2005-11-03
Open the file /var/lib/dpkg/status-old (or even /var/backups/dpkg.status.*) and compare to the status file that you previously opened. Does the entry for mozilla-firefox appear to be different? Check for those differences with the current version before copying the backup into place, and keep a duplicate of the corrupt version at least until your system is back in order.

---

### Post by kylenewton on 2005-11-14
Thanks for the reply, Xian, and sorry for the late reply.

I'd found another thread similar to mine, and decided to much around with 'dpkg' to solve my apt-get problem.

'dpkg -r <dependencies one at a time>' fixed the problem. I removed 'mozilla-mplayer' and 'firefox' with 'dpkg -r ' and viola. 'apt-get install mozilla-firefox' and mplayer and I've got it back. apt-get works and I can now dist-upgrade. Thanks.

[Edit]: I should also say that I had also added a line to the /var/lib/dpkg/status where it showed

Package: mozilla-firefox
Status: purge ok installed
Priority: optional
Section: web
Architecture: all

I added 'Version: 1.0'

I don't know if that did anything, but it satisfied it for a while. Then I dpkg -r the stuff.

---

