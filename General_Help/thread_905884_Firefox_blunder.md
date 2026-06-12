---
title: "Firefox blunder"
date: 2008-08-30
forum: General Help
---

### Post by enzodad on 2008-08-30
Hi i dont know what i did. but tried to upgrade firefox cause wasent letting me theme or anything and i used a guide and no i cant even use it, i uninstall reboot reinstall and nothing works wont let me use it error message says

ERROR CANNOT LAUNCH MENUE ITEM
Failed to execute child process "firefox" (No such file or directory)

---

### Post by fooman on 2008-08-30
what happens if you try it from a terminal?  ...open a terminal and type:

```
firefox
```

post back with any error messages you see.

---

### Post by enzodad on 2008-08-30
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0
bash: firefox: command not found


But when i do that the same error comes up after i try to launch

---

### Post by retrovertigo on 2008-08-30
> **enzodad said:**
> The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0
bash: firefox: command not found


But when i do that the same error comes up after i try to launch

You installed the firefox-3.0 package, right?  Ubuntu puts firefox in /usr/lib/firefox-whatevertheversionnumberis, and puts a symbolic link in /usr/bin to point to whatever version is installed, so maybe your symbolic link is gone.  Please post the output of the following 2 commands:

```
ls -l /usr/bin/firefox*
ls -l /usr/lib | grep firefox
```

---

### Post by enzodad on 2008-08-30
lrwxrwxrwx 1 root root 20 2008-08-30 17:49 /usr/bin/firefox -> /opt/firefox/firefox
lrwxrwxrwx 1 root root 24 2008-08-30 20:07 /usr/bin/firefox-2 -> ../lib/firefox/firefox-2
lrwxrwxrwx 1 root root 31 2008-08-30 20:06 /usr/bin/firefox-3.0 -> ../lib/firefox-3.0.1/firefox.sh
lrwxrwxrwx 1 root root 11 2008-08-30 20:06 /usr/bin/firefox.ubuntu -> firefox-3.0


drwxr-xr-x  5 root root     4096 2008-08-30 20:07 firefox
drwxr-xr-x  7 root root     4096 2008-08-30 20:06 firefox-3.0.1
drwxr-xr-x  5 root root     4096 2008-08-30 20:06 firefox-addons

---

