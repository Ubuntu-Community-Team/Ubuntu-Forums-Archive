---
title: "Gutsy Gibbons : Firefox 2.0 update unable to complete after manual firefox3 install."
date: 2008-07-11
forum: General Help
---

### Post by escragg on 2008-07-11
Hey Guys,

A few weeks ago I manually installed Firefox 3.0 on my current box (running Gutsy).

Two days ago I was presented with an update notification, and I'll admit I did the 'trained monkey' thing and just hit 'update all'... Whoops: firefox is one of the things that was due to be updated, and now the firefox debian update package will not execute.  Worse still, all package management is now essentially stuck until this firefox package install resolves.

When I run:
```
$sudo apt-get install -f
```
I get
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libemeraldengine0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  firefox
Suggested packages:
  latex-xft-fonts
The following packages will be upgraded:
  firefox
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/9203kB of archives.
After unpacking 20.5kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 163240 files and directories currently installed.)
Preparing to replace firefox 2.0.0.14+2nobinonly-0ubuntu0.7.10 (using .../firefox_2.0.0.15+1nobinonly-0ubuntu0.7.10_i386.deb) ...
Unpacking replacement firefox ...
dpkg: error processing /var/cache/apt/archives/firefox_2.0.0.15+1nobinonly-0ubuntu0.7.10_i386.deb (--unpack):
 error creating symbolic link `./usr/bin/firefox': No such file or directory
Please restart any running Firefoxes, or you will experience problems.
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_2.0.0.15+1nobinonly-0ubuntu0.7.10_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I can see that it has something to do with the symbolic links that were modified when I manually installed firefox 3.0.  (I'm kicking myself for not saving the link of the instructions that I used to do the firefox 3.0 install, I can't find it).  Any suggestions on the best way to resolve this so I can get apt functionality back and get on with my happy Ubuntu experience?

Thanks guys!

-Scott

---

### Post by fragos on 2008-07-11
The fact that Linux lets me doesn't mean I should. As long as you install .deb files your system has a centralized data base of installed applications. When you compile or install unpackaged binaries the data base no longer has an accurate picture of what's installed. Updates depend on the data base being acurate. Perhaps this is a good time to upgrade with a clean install to 8.04.

---

