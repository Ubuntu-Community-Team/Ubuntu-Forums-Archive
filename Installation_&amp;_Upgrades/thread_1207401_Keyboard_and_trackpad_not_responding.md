---
title: "Keyboard and trackpad not responding"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by RipRapRob on 2009-07-08
Yesterday, the update manager told me updates was available for my computer (Dell Latitude D610).

I got an error and an information that I had to install a package manually via terminal (just typed the command dpgk command given in the Updater, in terminal) and continued the update - and everything seemed to work fine (I used the computer for at couple of hours).

Shut down the computer and went to bed.

This morning, I can't type my username or use the trackpad or the mouse, when i get to the logon window.

I can boot into Windows where the keyboard and mouse works fine, and it works fine in the boot menu too.

I've tried selecting the 'recovery mode' and I have tried all the options listed in the 'Recovery Menu' - no problems detected and the keyboard works fine.

So it's NOT a hardware issue.

I've tried booting to root ('Drop to root shell prompt') where I've tried:

```
dpkg-reconfigure console-setup
```

but no change :(

How do I get my keyboard to function again, so I can log on to Ubuntu?

Thanks.


Rob, Denmark

---

### Post by RipRapRob on 2009-07-08
Looks like the problem is, that my '/etc/X11/xorg.conf' is more or less empty.

How do I recreate it?

I've tried "dpkg-reconfigure --all" which takes me thru a series of questions, but the xorg.conf still only contains a few lines.

I've then tried "dpkg-reconfigure -phigh xserver-xorg", but i then get a

**Gtk-WARNING **: cannot open display:  at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 54**

Help?

---

### Post by wojox on 2009-07-08
Go to 

```
/etc/X11/
```

and see if there's a backup copy of xorg.conf

---

### Post by RipRapRob on 2009-07-08
There is two - both containing no more than the primary :-(

---

### Post by RipRapRob on 2009-07-09
Thread closed - I've re-installed Ubuntu :(:(

---

