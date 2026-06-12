---
title: "[SOLVED] command called from System&amp;gt;Shut Down?"
date: 2008-11-23
forum: General Help
---

### Post by moore.bryan on 2008-11-23
for the life of me, i can't figure this one out on ibex... i know 
"gnome-session-save --gui --kill" worked back in the day, but that only brings-up a log-out dialog. all i'm trying to do is figure-out the command to make the shutdown/reboot/suspend/hibernate dialog pop-up. any help, much appreciated!

---

### Post by Chunky Dunk on 2008-11-23
Try this one: "gnome-session-save --shutdown-dialog". I'm on Hardy, so I can't vouch for it, but according to the this post in [http://ubuntuforums.org/showpost.php?p=6057090&postcount=7]("http://ubuntuforums.org/showpost.php?p=6057090&postcount=7"), it works in Intrepid.

---

### Post by moore.bryan on 2008-11-23
thanks for the reply, chunk, but all i get is this:
```
bryan@dell:~$ gnome-session-save --shutdown-dialog
Unknown option --shutdown-dialog
Run 'gnome-session-save --help' to see a full list of available command line options.

```

---

### Post by Chunky Dunk on 2008-11-25
> **moore.bryan said:**
> thanks for the reply, chunk, but all i get is this:
```
bryan@dell:~$ gnome-session-save --shutdown-dialog
Unknown option --shutdown-dialog
Run 'gnome-session-save --help' to see a full list of available command line options.

```

Hmm... I finally upgraded to Intrepid and tried this out. It worked for me.
when I type "gnome-session-save --help", I get this:
```
$ gnome-session-save --help
Usage:
  gnome-session-save [OPTION...]

Help Options:
  -?, --help                  Show help options
  --help-all                  Show all help options
  --help-gtk                  Show GTK+ Options

Application Options:
  -s, --session-name=NAME     Set the current session name
  --logout                    Log out
  --force-logout              Log out, ignoring any existing inhibitors
  --logout-dialog             Show logout dialog
  --shutdown-dialog           Show shutdown dialog
  --kill                      Kill session
  --gui                       Use dialog boxes for errors
  --silent                    Do not require confirmation
  --display=DISPLAY           X display to use

```

It lists the --shutdown-dialog, for me, do you get anything different?

---

### Post by moore.bryan on 2008-11-26
strange... it's there now, but wasn't there before. could it possibly have been a "hiccup" a recent upgrade fixed?

---

### Post by ohmysql on 2011-10-28
FYI in 11.10 it's a new command:

/usr/lib/indicator-session/gtk-logout-helper --shutdown

[http://askubuntu.com/questions/65965/what-is-the-command-to-open-the-shutdown-dialog](http://askubuntu.com/questions/65965/what-is-the-command-to-open-the-shutdown-dialog)

OMS!!!

---

### Post by ohmysql on 2012-11-01
Also, it may now be   ```
gnome-session-quit --power-off
```

---

