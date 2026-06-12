---
title: "Little boxes, on the hillside (only garbage fonts)"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by gdoten on 2009-05-29
So I decided to start doing some GTK development on my main Ubuntu box today. Installed glib, pango, atk-dev, cairo, gtk+. Then installed Boxee (yes, a slight diversion) which I ran and then immediately quit. Sometime shortly after all this the window menus started showing a little box where any character should have been displayed. Then other places on windows started showing the same. It's as if whatever font is active has one glyph, this little box. Rebooted. All of the text on the desktop, in any menus, etc., for the windows are all little boxes. Makes it tough to operate the computer this way.

In hindsight, I'm guessing maybe installing GTK to the latest version might be the culprit, since GNOME uses GTK. What I could use is some assistance in getting the fonts (or whatever may be the problem) fixed up again? Anyone else had this happen? Haven't had any luck searching for a solution yet but will keep looking.

---

### Post by gdoten on 2009-05-31
Here's what I've tried so far (with some other notes):

[LIST=1]
[*]/etc/fonts/ restored from Live CD.
[*]Deleted .fonts.conf in home directory.
[*]/usr/share/fonts/ restored from Live CD.
[*]/use/local/share/fonts/ is empty.
[*]/usr/share/X11/fonts/ does not exist.
[*].fonts/ in home directory doesn't exist.
[*]Renamed .fontconfig in home dir. to .fontconfig.old.
[*]Renamed /var/cache/fontconfig to -.old.
[*]/etc/X11/fonts/ restored from Live CD.
[*]/etc/environment - added to end: LANG="en_US.UTF-8"
[*]No errors in /var/log/fontconfig.log.
[*]Checked out /etc/gdm/ files; nothing pops out.
[/LIST]
Any ideas appreciated!

---

### Post by gdoten on 2009-06-01
Tried to uninstall a bunch of software that was installed just prior to this problem: boxee, Adobe Air, python, fontmatrix. Still the little boxes. dpkg-reconfigure x11-command and console-setup no help. Have been looking at X11-related files all morning, no luck.

Let me ask this: when the login window appears, where does X11 get the fonts to display it with? That window has all little boxes where any text characters should be displayed. How do I troubleshoot a font problem with X11? (Been looking all morning without any luck.)

---

