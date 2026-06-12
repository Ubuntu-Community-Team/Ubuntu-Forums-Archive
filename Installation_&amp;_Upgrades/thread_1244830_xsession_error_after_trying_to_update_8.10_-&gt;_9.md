---
title: "xsession error after trying to update 8.10 -&gt; 9.04"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by sousedstvi on 2009-08-19
I tried to update 8.10 to 9.04. I got an error saying i didn't have enough disk space in my root / directory. following instructions from the updater, I ran
$sudo apt-get clean

and cleaned up /tmp with
$rm -rf /tmp

I restarted ubuntu and after logging in to gnome, got the "you have been logged in less than 10 seconds" error.
here's ~/.xsession-error:

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to 
/etc/X11/xinit/xinput.d/default.
/usr/bin/xmodmap:  unable to open file /usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
mkdtemp: private socket dir: Permission denied

I also tried failsafe GNOME and got this error:
problem with configuration server
/usr/lib/libgconf2-4/gconf-sanity-check-2
exited with status 256

---

### Post by riazrahaman on 2009-08-20
Try logging into command line mode (ctrl alt f1).

Check the xsession errors under /var/log. I remember seeing this issue long back. Have to search through my old mails.

---

### Post by PmDematagoda on 2009-08-20
If the error about low disk space was shown before the upgrade from 8.10 to 9.04 completed, did you try rerunning the upgrade to ensure that all the required packages had been installed/upgraded?

---

### Post by sousedstvi on 2009-08-20
I did not try rerunning the upgrade after I got the low disk space error. Now I can only access failsafe terminal. Can I run the upgrade from there?

---

### Post by sousedstvi on 2009-08-20
I'll check /var/log for any other xsession errors.

---

### Post by sousedstvi on 2009-08-21
I didn't see any files or directories named "xsession" in /var/log. anything else I should look for in /var/log?

also, any thoughts as to whether I should go ahead and try the upgrade from within failsafe terminal?
some research indicates I can do

$sudo apt-get dist-upgrade

---

### Post by PmDematagoda on 2009-08-23
> **sousedstvi said:**
> I didn't see any files or directories named "xsession" in /var/log. anything else I should look for in /var/log?

also, any thoughts as to whether I should go ahead and try the upgrade from within failsafe terminal?
some research indicates I can do

$sudo apt-get dist-upgrade

Yes, that should do the trick. But please try and ensure that there is at least about 1.5 Gb of free space on the drive so that the upgrade can complete.

---

### Post by Kenno on 2010-01-21
You **need** /tmp
```

sudo mkdir /tmp
sudo chmod 1777 /tmp
```

---

