---
title: "UTF8 problems"
date: 2005-11-18
forum: General Help
---

### Post by pickarooney on 2005-11-18
I use emelfm2 as my file manager and recently I've been getting stange UTF8 errors. The main two are:

1) every time I open an image in gqview, I get the message:
```

(gqview:26901): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()
*** attempt to put segment in horiz list twice

```

2) accented characters in filenames are not displayed, and all characters after the accent are ignored. e.g., a file named **björk - hunter.mp3** displays simply as **bj**.

The output of locale is 

LANG=en_IE.UTF-8
LC_CTYPE="en_IE.UTF-8"
LC_NUMERIC="en_IE.UTF-8"
LC_TIME="en_IE.UTF-8"
LC_COLLATE="en_IE.UTF-8"
LC_MONETARY="en_IE.UTF-8"
LC_MESSAGES="en_IE.UTF-8"
LC_PAPER="en_IE.UTF-8"
LC_NAME="en_IE.UTF-8"
LC_ADDRESS="en_IE.UTF-8"
LC_TELEPHONE="en_IE.UTF-8"
LC_MEASUREMENT="en_IE.UTF-8"
LC_IDENTIFICATION="en_IE.UTF-8"
LC_ALL=

Any idea what I can do?

---

### Post by ubuntu_demon on 2005-11-18
Do these links help you ? 

[https://wiki.ubuntu.com/UTFEightMigrationTool](https://wiki.ubuntu.com/UTFEightMigrationTool)

[https://wiki.ubuntu.com/BMPInvalidUTF8](https://wiki.ubuntu.com/BMPInvalidUTF8)

---

### Post by pickarooney on 2005-11-18
Wow, excellent idea, that tool. Although, it crashes on me after the first step (locale change), when it starts to convert the filenames
```

/usr/share/utf8-migration-tool/pylib/wizard/wizard.py:546: DeprecationWarning: Class Wizard is already GObject-registered; Please note that classes containing any of the attributes __gtype_name__, __gproperties__, or __gsignals__ are now automatically registered.
  gobject.type_register(Wizard)
Traceback (most recent call last):
  File "/usr/bin/utf8migrationtool", line 91, in change_setup
    os.rename(oldfile, newfile)
OSError: [Errno 2] No such file or directory

```

If I had to guess, I'd say the script is trying to rename

**/path/to/c?rr?pt?d_f?l?/c?rr?pt?d_file.mp3** to 
**/path/to/c?rr?pt?d_f?l?/corrupted_file.mp3**

and it's not understanding the corrupted path name and so telling me it's not found.

I could be off the mark though.

---

### Post by pickarooney on 2005-11-18
When I edit the filenames manually within my file manager, and rerun the migration tool, the names display with corrupted/is08859-1 coding. 
I'm not sure why that is - surely now that the locale is fixed, everythign I type in should be in UTF8?

---

### Post by ubuntu_demon on 2005-11-18
Let's make sure everything is upgraded and configured and post your .xsession-errors afterwards. I don't know what else to try. Maybe your .xsession-errors gives a hint.

This will upgrade your system :
$ sudo apt-get update ; sudo apt-get upgrade

If any package doesn't get upgraded do :
$sudo apt-get dist-upgrade

This will configure all the packages that aren't configured properly yet :
$ sudo dpkg --configure -a

-remove your ~/.xsession-errors
-log out
-log in
-post your ~/.xsession-errors

---

### Post by adamkane on 2006-03-05
convmv Nautilus script
[http://www.ubuntuforums.org/showthread.php?t=139154](http://www.ubuntuforums.org/showthread.php?t=139154)

---

