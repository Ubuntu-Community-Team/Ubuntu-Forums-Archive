---
title: "KDE broke GNOME!!"
date: 2005-11-29
forum: General Help
---

### Post by David Gerard on 2005-11-29
I installed kubuntu-desktop a while ago, because no sensible free software desktop user will be running all-GNOME or all-KDE applications, there's too much good stuff in each. I also installed all the KDE and GNOME salad I could find. (Twenty-gig disk — free software toys? GIMME!)

So Saturday I tried starting the laptop in KDE instead of GNOME. Couldn't find hibernate or suspend, which was annoying (having to shut down completely each session). Got out of KDE, logged into GNOME ... it's broken. The panels flash and have nothing in them. Then they stop flashing and there's no way to start an application. Failsafe GNOME did the same. KDE BROKE GNOME!!

I'm sure this isn't a common occurrence; my girlfriend happily switches between the two with no problems. But it's definitely happened here!

Any ideas what's broken?

I probably prefer KDE to GNOME, but I'd really like the option thanks!

---

### Post by Xian on 2005-11-29
My advice would be to do a Alt+Ctrl+F1 to get to a command line.
Then issue a command to kill the panel and nautilus.

$ killall gnome-panel
$ killall nautilus

Log back in and look for changes.

If no change, then rename all your hidden gnome file prefs in your
/home/username/ directory.

They would include .gconf, .gconfd, .gnome2, .gnome2_private, .nautilus, .metacity. Then restart X or just reboot and log back into Gnome.

If this fails then do the same scenario again and in addition empty the contents of your tmp folder, then restart X & log in.

---

### Post by atoponce on 2005-11-29
[quote=Xian]My advice would be to do a Alt+Ctrl+F1 to get to a command line.
Then issue a command to kill the panel and nautilus.

$ killall gnome-panel
$ killall nautilus

Log back in and look for changes.

If no change, then rename all your hidden gnome file prefs in your
/home/username/ directory.

They would include .gconf, .gconfd, .gnome2, .gnome2_private, .nautilus, .metacity. Then reset X or just reboot and log back into Gnome.

If this fails then do the same scenario again and in addition empty the contents of your tmp folder, then reset X & log in.[/quote] 
I had this exact same issue when I installed KDE. The permissions on my ~/.ICEauthority file where changed. Just change the permissions to include read-all on that file, and you should be able to log back in.

```
sudo chmod 644 ~/.ICEauthority
```

---

### Post by ozorba on 2005-11-29
1. Rename your .gnome and .gnome2 directories to something else.
2. Rename .gtkrc-2.0 file to someting else as well.

That should the trick. Then try to find out where the problem is.

---

