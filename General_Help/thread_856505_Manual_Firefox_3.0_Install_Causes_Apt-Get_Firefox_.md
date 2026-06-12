---
title: "Manual Firefox 3.0 Install Causes Apt-Get Firefox 2.0 update to croak"
date: 2008-07-11
forum: General Help
---

### Post by escragg on 2008-07-11
Hey Guys,

I installed Firefox 3.0 Manually a few weeks ago (I'm kicking myself for not bookmarking the instructions that I used, because now I can't find them).  Then, a few days ago, my Update Manager triggers and I do the trained monkey thing and just hit 'update all' without noticing that firefox 2.0 was one of the applications to update.

Now the firefox 2.0.deb update package will not run, and without it, all package management on my machine is fubar.

Here is what I get when I run $sudo apt-get install -f


```
escragg@escragg-laptop:~$ sudo apt-get install -f
[sudo] password for escragg:
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
escragg@escragg-laptop:~$ 

```

Any suggestions for the quickest fix?

Thank you so much! Sorry about what I'm sure is a fairly novice question.

-ESC

---

### Post by balaknair on 2008-07-11
I used the instructions here [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox) to install Firefox 3.0 on Ubuntu 7.10, and I too just clicked 'update all' when FF-2.0.0.15 was available. I don't recall having any trouble as you have though. Could be that you installed using a different method.

I think you might try opening Synaptic and select Firefox- if it shows Firefox 3.0 is installed hit Ctrl+E to force the version you have now(FF3.0), if that is the issue. Otherwise, just check this link on how to remove FF-3.0 [http://www.psychocats.net/ubuntu/firefox#remove](http://www.psychocats.net/ubuntu/firefox#remove) 

Another thing that occured to me on reading the output you got- shouldn't it be "/usr/bin/firefox" instead of "./usr/bin/firefox"? I think you might have accidentally inserted that little "." when installing the FF-3.0 version manually from the terminal.
Maybe manually creating a ./usr/bin/firefox folder if it isn't there will get things working, but I'm not sure how safe/effective that will be. I suggest you check the link I posted above, remove the new version, and reinstall FF-2. Then using the instructions in the link [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox) , reinstall FF-3 manually. This method worked flawlessly for me, so I know for sure it works.

---

### Post by escragg on 2008-07-11
I used the synaptic package manager to force removal of the most recent firefox update and the package manager is working again... I will try uninstalling firefox and re-installing it later tonight (whatever I did, obviously didn't fix core issue, but at least I have functionality again).

Thanks for your help!:)

-ESC

---

### Post by balaknair on 2008-07-11
Glad to hear that. Hope you manage to fix the underlying cause as well. 

All the best.

---

