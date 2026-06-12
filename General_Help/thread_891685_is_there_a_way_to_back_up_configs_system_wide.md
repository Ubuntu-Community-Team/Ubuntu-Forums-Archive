---
title: "is there a way to back up configs system wide?"
date: 2008-08-16
forum: General Help
---

### Post by epidemiks on 2008-08-16
Hi, I am wondering whether it is possible, or if there exists a command/app/etc which will back up all config files at once?

Should some disaster befall the system a user's preferred settings can be reset without too much hassle, assuming all the same packages are back on the system (or a warning that there is settings for "xxx" package, but it can't be found, so needs to be reinstalled.)

That would be reaaally handy.

---

### Post by Naatan on 2008-08-16
I usually just backup my home directory and the configuration directories for apache, php and mysql.. but it all depends on what you have installed.

Have a look at 

[http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)

To my knowledge there is no simple way of having this done automatically as most apps store their configuration files in different directories.

---

### Post by spacedoggy on 2008-08-16
I save my home directory (including hidden sub directories)

after restoring the system and copying them back, i restore ownership with

sudo chown -R spacedog:spacedog /home/spacedog

after that settings are preserven in my firefox, thunderbird, pidgin, skype.

as well as file associations. and some gnome settings

the only thing I don't see restored are my shortcut icons and applets on the taskbars, no biggie I guess.

---

### Post by jerome1232 on 2008-08-16
If this is a desktop computer backing up /home will backup all user settings, a server is a bit different.

As far as the packages go the only thing I can think of is make a text file that has all installed packages like this
```
dpkg --get-selections >installed.txt
```

Then should you have to reinstall you can see what's not installed that was installed, there's probably a better way than this though

```
dpkg --get-selections >new.txt
diff installed.txt new.txt
```

---

### Post by Vivaldi Gloria on 2008-08-16
Look at nicedude's script:

[http://ubuntuforums.org/showthread.php?t=792639](http://ubuntuforums.org/showthread.php?t=792639)

---

