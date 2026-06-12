---
title: "Please help!"
date: 2008-11-21
forum: General Help
---

### Post by 2handband on 2008-11-21
I recently installed Ubuntu 8.04 on my Toshiba Satellite A215-S4697 laptop. I cannot find wireless card drivers that work (it's an Atheros AR5007EG). The installation included a movie player called Totem. Upon attempting to play a DVD movie it informed me that I needed to install some pluggins in order to do so, which I proceeded to do. Now Totem just locks up when I try to play a DVD. 

If anyone can help me with these issues it would be greatly appreciated. I am new to Linux and open source software in general and am completely clueless. Thanks!
Gene

---

### Post by whollycow on 2008-11-21
Not sure what to tell you about wireless, but the movie problem may be fixed by trying a different movie-viewing program.  My personal favorite is VLC.  You can find it in Synaptic.  Give that a try and see if it still locks things up.

edit: P.S. Synaptic is in the 'System' menu under 'Administration', if you were wondering.

---

### Post by StOoZ on 2008-11-21
use I used ndiswrapper and WICD for the wifi issue

---

### Post by doas777 on 2008-11-21
ok, for your DVD problem, first open a terminal and run this:

```
sudo apt-get install ubuntu-restricted-extras vlc
```

then go to this site an follow the respoitory how-to:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

in the process you will be installing common codecs, and a library to decode dvds. vlc is an alright mediaplayer (weak on ergonomics and usability) that will play almost anything. try totem first, but if you can;t get it to run, fall back to vlc.

good luck,
franklin

---

### Post by joseangelini on 2008-11-21
Look at this for your wifi card [http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

To resolve your your video problem you have to add medibuntu repositories. Look at this guide
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by 2handband on 2008-11-22
Thanks for the responses. I got the DVD player working, but when I tried the code provided at ubuntugeek for the wireless I got the following output:

gene@gene-laptop:~$ wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
--11:17:01--  [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
           => `madwifi-ng-r2756+ar5007.tar.gz'
Resolving snapshots.madwifi.org... 217.24.1.134
Connecting to snapshots.madwifi.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://snapshots.madwifi-project.orgspecial/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi-project.orgspecial/madwifi-ng-r2756+ar5007.tar.gz) [following]
--11:17:01--  [http://snapshots.madwifi-project.orgspecial/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi-project.orgspecial/madwifi-ng-r2756+ar5007.tar.gz)
           => `madwifi-ng-r2756+ar5007.tar.gz'
Resolving snapshots.madwifi-project.orgspecial... failed: Name or service not known.
gene@gene-laptop:~$ 
gene@gene-laptop:~$ tar xfz madwifi-ng-r2756+ar5007.tar.gz
tar: madwifi-ng-r2756+ar5007.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
gene@gene-laptop:~$ 
gene@gene-laptop:~$ cd madwifi-ng-r2756+ar5007
bash: cd: madwifi-ng-r2756+ar5007: No such file or directory
gene@gene-laptop:~$ 
gene@gene-laptop:~$ make
make: *** No targets specified and no makefile found.  Stop.
gene@gene-laptop:~$ 
gene@gene-laptop:~$ sudo make install
[sudo] password for gene: 
make: *** No rule to make target `install'.  Stop.
gene@gene-laptop:~$ 



Either I'm doing something wrong or there's something wrong with my machinery. Any thoughts?

---

### Post by PocketDog on 2008-11-22
I'd download that tar.gz to an empty folder on your Desktop and install it from there instead of using wget. (Get into the habit of opening files you've downloaded from sources other than the official repository from inside a fresh, empty directory for security reasons). It looks like the installation process is failing on download

---

### Post by ugm6hr on 2008-11-22
Try this instead: [http://ubuntuforums.org/showthread.php?t=792158](http://ubuntuforums.org/showthread.php?t=792158)

The ubuntugeek guide has an out of date link.

---

### Post by hyper_ch on 2008-11-22
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by joseangelini on 2008-11-22
here is the link for the file:
 [http://snapshots.madwifi-project.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi-project.org/special/madwifi-ng-r2756+ar5007.tar.gz)
or  here [http://snapshots.madwifi-project.org/special/](http://snapshots.madwifi-project.org/special/)  you can download the file with firefox

try with it.

Good luck

---

### Post by 2handband on 2008-11-25
Thanks for all the advice so far. I got everything working using the link that ugm6hr posted, but now it's stopped working again. I tried reinstalling from that link without success. Any ideas?

---

### Post by ugm6hr on 2008-11-26
> **2handband said:**
> Thanks for all the advice so far. I got everything working using the link that ugm6hr posted, but now it's stopped working again. I tried reinstalling from that link without success. Any ideas?

Have you recently updated your kernel?

If so, you have to recompile the driver again.

---

