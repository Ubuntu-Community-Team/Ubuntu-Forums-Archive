---
title: "another gpg agent already running msg"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by albesan on 2008-12-09
hello team,

I'm getting the above message.
The full xsession-errors is:

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
** Message: Another GPG agent already running


I have trying fixes for a couple of days now, among them re-installing GDM, gnome-session, ubuntu-desktop and a number of other solutions to no avail.

Found posts about similar issues but none seems to match mine.

I have recently rebuild the whole computer. I restored the ubuntu system from a zipped file and it all seemed fine but on reboot I got that message and I can only log in on failsafe gnome session.

Any help appreciated.

regards


a.

---

### Post by albesan on 2008-12-10
also tried creating a new user but that didn't help either :(

---

### Post by mangal on 2009-01-22
today (21-01-2009) I also have faced the Problem. I found that the following two files having the same contents in /etc/X11/Xsession.d/ (means its running seahorse-agent two times).
         60seahorse
         60seahorse-agent
so i just removed 60seahorse file. now its working ok

---

### Post by albesan on 2009-01-22
hey,

Thanks for the reply.
It's too late for me because I already did a new install, a number of other issues cropped up and decided to rebuild the system.
But now I know what it is if it happens again.

a.

---

