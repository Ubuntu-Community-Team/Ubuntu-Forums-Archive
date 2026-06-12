---
title: "Clean or reinstal Ubuntu?"
date: 2008-10-07
forum: General Help
---

### Post by raysa on 2008-10-07
Somehow I've messed up the Mozilla apps Firefox and Thunderbird, which were working fine until a couple of days ago. I've tried uninstalling them and reinstalling (with reboots in between) but they still don't work. One or two other things aren't working as they used to - there's obviously an upset in the system.  All this is after installing some nice-to-have but not essential stuff using the Add/Remove feature or Synaptic.  I've tried to remember what I installed and uninstal it, but I suspect I've forgotten something.

Can I now get back to where I was by re-installing, or cleaning up, Ubuntu itself, without losing docs and data?  Or what would be better advice?

Thanks, Ray

---

### Post by Idefix82 on 2008-10-07
Have you made a separate /home partition or is everything on one partition?
If you have a separate /home partition then you can do a clean install but keep the data on the /home partition. On the other hand you will then also keep all the user specific configuration files for Mozilla etc. If they are the ones causing the problem then this procedure won't solve it.

On a related note: when you reinstalled the malfunctioning things, did you also delete the relevant hidden settings folders from your folder? You can see them by pressing Ctrl+h in Synaptic.

---

### Post by geirha on 2008-10-07
I suspect firefox & co will work again if you remove the .mozilla directory in your home folder. Rename it with ```
mv ~/.mozilla ~/.mozilla.old
``` and see if firefox behaves better.

---

### Post by Sylvertwyst on 2008-10-07
when uninstalling, also add the --purge option, this will make sure all config files are erased, if that is what is causing your problem

i.e.:
```
sudo apt-get --purge remove <package name>
```

---

### Post by raysa on 2008-10-08
Thanks all. Answers/comments:

The whole ubuntu installation is on the same partition I assume - it was just a standard instal and I haven't made a separate /home partition (didn't know you could).

Tried the mv command and declined to let it import anything, so it opened up as if I was a completely new user. Called up a couple of websites with Firefox and the problem is still there - half the page invisible, big chunks of text missing (although the same sites render perfectly in Opera and Konqueror).

Control+h doesn't have any effect in my Synaptic (version o.61ubuntu9), but it offers 'Removal' or 'Complete removal'. I used the latter, assuming it also removes hidden stuff, settings, etc.  Still no joy.

thanks, Ray

---

### Post by justleen on 2008-10-08
as a tip if you do decide to reinstall:
```

sudo cat /var/log/apt/term.log |grep "Setting up"

```
will give a quick overview on what you installed..

---

### Post by Fevrin on 2009-01-05
> **raysa said:**
> The whole ubuntu installation is on the same partition I assume - it was just a standard instal and I haven't made a separate /home partition (didn't know you could).

It's usually a good idea to make /home a separate partition for cases like this where you might want to reinstall Ubuntu while keeping your personal data intact.  There are several tutorials on the web on how to make /home its own partition; a quick search should suffice.

> **raysa said:**
> Control+h doesn't have any effect in my Synaptic (version o.61ubuntu9), but it offers 'Removal' or 'Complete removal'. I used the latter, assuming it also removes hidden stuff, settings, etc.  Still no joy.

Ctrl+h should be used in Nautilus, not Synaptic; Idefix82 made a simple (but confusing) mistake.  Pressing Ctrl+h in Nautilus allows you to view all hidden files (those whose names are preceded by a period, like ".bash_history").  Most program settings are hidden in this manner to avoid unnecessary clutter, while still being available in one place for convenience.

---

