---
title: "Active Directory Users"
date: 2008-09-03
forum: General Help
---

### Post by Phaux on 2008-09-03
I've usually been able to just search here and there, and find my answers, like setting the system up so I can log in with AD usernames, and accessing shares, getting IEs4Linux installed, but I have one problem left unanswered.

I need something like a first-time-login userscript that creates their home folder, sets up shares, copies configuration files from a template I've made, changes the layout of the desktop, and adds the correct icons or deletes things from the menus.  It only needs to run once, the first time a user logs in.  I suspose something similar to the little box you see that personalizes Windows when you first log in with an Active Directory account.

---

### Post by HermanAB on 2008-09-03
This may help:
[http://aeronetworks.ca/LinuxActiveDirectory.html](http://aeronetworks.ca/LinuxActiveDirectory.html)

Also see [http://www.likewisesoftware.com/](http://www.likewisesoftware.com/)

The first time setup should be in /etc/skel

Cheers,

Herman

---

### Post by Phaux on 2008-09-05
Ah ok cool.  The magic place I was looking for was /etc/skel.  Thanks.

Is there any major difference between the guide you linked to, and the one I've [been using]("http://ubuntuforums.org/showthread.php?t=91510")?  I noticed that your guide requires the user to type out the domain name in front of their username, whereas the one I'm using now doesn't...

---

