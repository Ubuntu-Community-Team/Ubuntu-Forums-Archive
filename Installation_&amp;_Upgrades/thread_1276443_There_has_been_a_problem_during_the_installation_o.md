---
title: "There has been a problem during the installation of the following applications"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by ferulebezel on 2009-09-27
I installed 9.04, immediately ran the update manager, added my media drive, when I went to install some more applications using the "Add/Remove.." item under the "Applications" menu.

I selected about 10 and hit the apply changes button.  

There was a checking dependencies progress bar for a few seconds and then I got the message in the title of this post.

I then tried again with only one application, Tunderbird, and got the same results.

As error messages go the one I got was pretty useless.

Any ideas as to what is wrong?

---

### Post by kranny on 2009-09-27
Can you be more specific about the error you got?

---

### Post by ferulebezel on 2009-09-27
> **kranny said:**
> Can you be more specific about the error you got?

No, I cant.  The thread title is the message I got verbatim.

---

### Post by oldos2er on 2009-09-27
Can you run **sudo apt-get update && sudo apt-get install thunderbird** in a terminal, and post the output here?

---

### Post by ferulebezel on 2009-09-28
> **oldos2er said:**
> Can you run **sudo apt-get update && sudo apt-get install thunderbird** in a terminal, and post the output here?
```

$ sudo apt-get update
[sudo] password for elmarko: 
Hit http://us.archive.ubuntu.com jaunty Release.gpg
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release.gpg
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release
Hit http://us.archive.ubuntu.com jaunty Release
Hit http://us.archive.ubuntu.com jaunty-updates Release             
Hit http://security.ubuntu.com jaunty-security/main Packages        
Hit http://us.archive.ubuntu.com jaunty/main Packages
Hit http://us.archive.ubuntu.com jaunty/restricted Packages
Hit http://us.archive.ubuntu.com jaunty/main Sources
Hit http://us.archive.ubuntu.com jaunty/restricted Sources
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://us.archive.ubuntu.com jaunty/universe Packages
Hit http://us.archive.ubuntu.com jaunty/universe Sources
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://us.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
Reading package lists... Done
elmarko@elmarko-desktop:~$ sudo apt-get install thunderbird
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  thunderbird-gnome-support latex-xft-fonts
The following NEW packages will be installed:
  thunderbird
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 11.1MB of archives.
After this operation, 33.2MB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com jaunty-updates/main thunderbird 2.0.0.23+build1+nobinonly-0ubuntu0.9.04.1 [11.1MB]
Fetched 11.1MB in 19s (554kB/s)                                                
Selecting previously deselected package thunderbird.
(Reading database ... 121259 files and directories currently installed.)
Unpacking thunderbird (from .../thunderbird_2.0.0.23+build1+nobinonly-0ubuntu0.9.04.1_i386.deb) ...
Processing triggers for man-db ...
Setting up thunderbird (2.0.0.23+build1+nobinonly-0ubuntu0.9.04.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place


```


That sucessfuly installed Thunderbird.

As an experiment I tried using Add/Remove... to install Inkscape and the problem persists.

Also, I'm unable to  launch System->Administration->Synaptic Package Manager or System->Administration->Softwar4e Sources.

---

### Post by oldos2er on 2009-09-28
Not sure why some of those repos are being ignored. Can you run **gksu synaptic **and post the output?

---

### Post by ferulebezel on 2009-09-28
> **oldos2er said:**
> Not sure why some of those repos are being ignored. Can you run **gksu synaptic **and post the output?

```

$ gksu synaptec
$ 

```

In other words, no output.

---

### Post by oldos2er on 2009-09-28
> **ferulebezel said:**
> ```

$ gksu synaptec
$ 

```In other words, no output.

 Please copy and paste:
```
gksu synaptic
```

---

### Post by ferulebezel on 2009-09-29
> **oldos2er said:**
> Please copy and paste:
```
gksu synaptic
```

Oops, I guess spelling counts.

I did that.  It prompted me for the sudo password and ran.  I used it to install inkscape and everything went fine.

It still doesn't launch from the menu nor does "Add/Remove..."

---

### Post by oldos2er on 2009-09-29
If you run **gnome-app-install** in a terminal, does it output anything?

---

### Post by ferulebezel on 2009-09-30
> **oldos2er said:**
> If you run **gnome-app-install** in a terminal, does it output anything?
```

$ gnome-app-install

** (gnome-app-install:30842): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.6/dist-packages/AppInstall/AppInstall.py:1295: GtkWarning: gtk_tree_model_sort_set_sort_column_id: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_sort_column_id(-1, sort_type)
open: Permission denied

** (gksu:30849): WARNING **: Lock taken by pid: -1. Exiting.
$

```

I then proceeded to try sudoing it and got 

```

$ sudo gnome-app-install
[sudo] password for elmarko: 

** (gnome-app-install:30852): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.6/dist-packages/AppInstall/AppInstall.py:1295: GtkWarning: gtk_tree_model_sort_set_sort_column_id: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_sort_column_id(-1, sort_type)
$ 

```

I was able to instal GNU Paint even though I don't really want it.

---

### Post by arrange on 2009-09-30
Could you post the output of```
find ~ /tmp -type f -iname '*gksu*lock*' -exec ls -l '{}' \; 2> /dev/null
```- this will find the *gksu* lockfiles which may be the cause of your trouble :)

---

### Post by ferulebezel on 2009-09-30
> **arrange said:**
> Could you post the output of```
find ~ /tmp -type f -iname '*gksu*lock*' -exec ls -l '{}' \; 2> /dev/null
```- this will find the *gksu* lockfiles which may be the cause of your trouble :)
```

elmarko@elmarko-desktop:~$ find ~ /tmp -type f -iname '*gksu*lock*' -exec ls -l '{}' \; 2> /dev/null
-rw-r----- 1 root root 0 2009-09-26 23:55 /home/elmarko/.gksu.lock
elmarko@elmarko-desktop:~$

```

---

### Post by arrange on 2009-10-01
As you can see, your */home/elmarko/.gksu.lock* lock file is owned by *root*, which may have been caused by running *sudo <graphical programme>* instead of *gksudo*/*gksu*. I would suggest removing the lockfile```
sudo mv /home/elmarko/.gksu.lock /home/elmarko/.gksu.lock.old
```

---

### Post by ferulebezel on 2009-10-01
> **arrange said:**
> As you can see, your */home/elmarko/.gksu.lock* lock file is owned by *root*, which may have been caused by running *sudo <graphical programme>* instead of *gksudo*/*gksu*. I would suggest removing the lockfile```
sudo mv /home/elmarko/.gksu.lock /home/elmarko/.gksu.lock.old
```


That did the trick.  Thanks.

---

