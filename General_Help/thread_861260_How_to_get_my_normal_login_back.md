---
title: "How to get my normal login back"
date: 2008-07-16
forum: General Help
---

### Post by ggore on 2008-07-16
I have messed up my login on Hardy.  The Select Sessions button had disappeared on my Gnome login screen, so I changed to the Chooser option using one of the configuration applications in Gnome.   Now I have the Chooser login but I do not want that.  I would like to know how to get my system back to the regular login screen.  Is there a way to do this by editing the gdm.conf file?

---

### Post by bodhi.zazen on 2008-07-16
Did you try :

```
gksu gdmsetup
```

[http://library.gnome.org/admin/gdm/stable/gdmsetupusage.html.en](http://library.gnome.org/admin/gdm/stable/gdmsetupusage.html.en)

---

### Post by ggore on 2008-07-16
Yes, I tried that but I get the message "cannot open display" since I am having to do all this from a terminal.  The Chooser screen does not give me the option to log into my system graphically and I don't know how to log into it using the Chooser screen.  I am reaching a terminal by hitting Ctl-Alt-F2 and logging in that way.

---

### Post by bodhi.zazen on 2008-07-16
Is X working ?

If so, ```
startx
```

Or you could boot to recovery mode and "startx" from there.

If X is broken, boot to recovery mode, select "xfix" -> reboot.

---

### Post by tamoneya on 2008-07-16
ive found that ```
sudo dpkg-reconfigure ubuntu-desktop
``` usually clears out this sort of problem.

---

