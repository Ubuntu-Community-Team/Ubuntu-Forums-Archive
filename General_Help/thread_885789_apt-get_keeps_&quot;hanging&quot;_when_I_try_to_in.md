---
title: "apt-get keeps &quot;hanging&quot; when I try to install/remove a package!  Help!"
date: 2008-08-10
forum: General Help
---

### Post by duckdown on 2008-08-10
Greetings all

I am having one heck of a problem..  I have a new VPS virtual server I just paid for, and it is running Ubuntu 8.04 I believe, but I am having a massive headache, and as a novice user I am not sure what to do.

I was trying to just simply get a very fast FTP daemon installed so a friend of mine could FXP me some files, so I tried doing 'apt-get install pure-ftpd'

Well it goes and starts to do its thing as usual, but when it gets down to the "Installing pure-ftpd ...." line, it just hangs!  I let it sit for an entire hour and it was still hanging so I had to ctrl+c to abort.

Then, I said, "well something must have obviously screwed up here" so I tried to REMOVE the package -- and would you believe the same damn thing is happening?  and, on top of it all, I can't even install any other packages now because it keeps trying to install this broken one causing it to hang every single time!

Here is the output.

```

root@61471:~# apt-get remove pure-ftpd-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  pure-ftpd-common
0 upgraded, 0 newly installed, 1 to remove and 26 not upgraded.
Need to get 0B of archives.
After unpacking 438kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 18053 files and directories currently installed.)
Removing pure-ftpd-common ...
 
**(HERE is where it just hangs forever, so I press CTRL+C)**
 
dpkg: error processing pure-ftpd-common (--remove):
 subprocess pre-removal script killed by signal (Interrupt)
 
Errors were encountered while processing:
 pure-ftpd-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It never tells me what is going on, and what the reason for it hanging is, and I am losing my mind here!

Any help would be greatly appreciated ASAP because this box is all but useless right now since it keeps trying to install that package and freezes

Cheers guys :(

---

### Post by duckdown on 2008-08-10
bump for help :(

---

### Post by Ryadt on 2008-08-10
Try 
sudo apt-get -f install
then
sudo apt-get upgrade

---

### Post by SunnyRabbiera on 2008-08-10
Sometimes the repositories hang, be patient and try again.

---

