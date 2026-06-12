---
title: "Add/Remove... Freezes"
date: 2008-10-17
forum: General Help
---

### Post by Spitphire on 2008-10-17
Hello,

The Package Manager works fine.

When I try Applications - Add/Remove...

It freezes (see screenshot)

Any thoughts?  If more info needed please ask. I'm stumped.

Thanks,
spit

---

### Post by Mark_in_Hollywood on 2008-10-17
Try

sudo apt-get clean

and do the add/remove again

---

### Post by Spitphire on 2008-10-18
Didn't work I still get the same results.  Any other ideas?  Is there a log file generated i could look at for more info?  I checked all the system logs and there is no info..

Spit

---

### Post by geirha on 2008-10-18
Sounds like it's having problem downloading the package lists from one of the repositories. Try running this in a terminal: ```
sudo aptitude update
```

---

### Post by Spitphire on 2008-10-18
Didn't work either, same results :popcorn: - any other ideas?

---

### Post by geirha on 2008-10-18
sudo aptitude update didn't produce any warnings or errors? 

Are there any files inside /var/lib/apt/lists/partial/ ? Try removing them, and run ```
sudo aptitude update
``` again. The output of that command may also be helpful.

---

### Post by Spitphire on 2008-10-18
More info:

1) I ran gnome-app-install from term to see if anything pops out, here's what i get before i terminate program with ctrl-c
```

am@lb:~$ /usr/bin/gnome-app-install

** (gnome-app-install:21873): WARNING **: return value of custom widget handler was not a GtkWidget
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 30, in <module>
    main()
  File "/usr/lib/python2.5/site-packages/AppInstall/activation.py", line 447, in main
    app = AppInstall(options, style)
  File "/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py", line 263, in __init__
    self.updateCache(filter_to_restore)
  File "/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py", line 947, in updateCache
    self.cache = MyCache(progress)
  File "/usr/lib/python2.5/site-packages/AppInstall/Cache.py", line 13, in __init__
    apt.Cache.__init__(self, progress)
  File "/usr/lib/python2.5/site-packages/apt/cache.py", line 49, in __init__
    self.open(progress)
  File "/usr/lib/python2.5/site-packages/apt/cache.py", line 76, in open
    progress.update(i/float(size)*100)
  File "/usr/lib/python2.5/site-packages/AppInstall/Progress.py", line 49, in update
    gtk.main_iteration()
KeyboardInterrupt

```

2) Output of aptitude update

```

Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Hit http://de.archive.ubuntu.com hardy Release.gpg
Ign http://de.archive.ubuntu.com hardy/main Translation-en_US
Ign http://de.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://de.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://de.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://de.archive.ubuntu.com hardy-updates Release.gpg
Ign http://de.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://de.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://de.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://de.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://de.archive.ubuntu.com hardy Release
Hit http://de.archive.ubuntu.com hardy-updates Release
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://de.archive.ubuntu.com hardy/main Packages
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://de.archive.ubuntu.com hardy/restricted Packages
Hit http://de.archive.ubuntu.com hardy/main Sources
Hit http://de.archive.ubuntu.com hardy/restricted Sources
Hit http://de.archive.ubuntu.com hardy/universe Packages
Hit http://de.archive.ubuntu.com hardy/universe Sources
Hit http://de.archive.ubuntu.com hardy/multiverse Packages
Hit http://de.archive.ubuntu.com hardy/multiverse Sources
Hit http://de.archive.ubuntu.com hardy-updates/main Packages
Hit http://de.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://de.archive.ubuntu.com hardy-updates/main Sources
Hit http://de.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://de.archive.ubuntu.com hardy-updates/universe Packages
Hit http://de.archive.ubuntu.com hardy-updates/universe Sources
Hit http://de.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://de.archive.ubuntu.com hardy-updates/multiverse Sources
Reading package lists...

```

3) There are no files in /var/lib/apt/lists/partial/ 

I appreciate the help, I hope this helps you figure out whats wrong here :)

Spit

---

### Post by Spitphire on 2008-10-18
I just removed/re-installed gnome-app-install - still same results..

---

### Post by Spitphire on 2008-10-18
Half Solved:

I changed the visual theme back to default and it seems to work now.

I was using the 'shiki' theme...

Spit

---

### Post by geirha on 2008-10-18
Ouch, themes shouldn't be able to make applications stop working. This is definitely worth a bug report on launchpad ...

---

### Post by Spitphire on 2008-10-18
Submitted:
[URL="https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/285438"]
https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/285438[/URL]

---

