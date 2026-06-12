---
title: "Can't enable restricted driver on Nvidia 7600GS"
date: 2008-04-24
forum: Hardware
---

### Post by cogadh on 2008-04-24
Before anyone suggests using Envy, no thanks, I would rather I learned how to make it work properly using the system itself and I usually don't like to pollute my system with scripts or packages not from official repositories.

Basically, the problem is the restricted drivers manager shows that the Nvidia driver is installed, but is not in use. The KDE 4 display options do not allow me to choose what driver to use (which it did with KDE 3). I could manually edit the xorg.conf file to change the settings, but like I said, the system should allow this to work without that kind of intervention. I'm sure I'm just missing something basic, so if anyone has a suggestion (other than Envy), I'd appreciate it.

EDIT - Whoops, I just realized this should be in the Multimedia and Video forum. If a mod/admin could move it there, that would be great.

---

### Post by mikespug on 2008-04-24
This comment won't help you install the drivers without using envy but, rather, is in response to your comment regarding packages in official repositories.  If you do a search through synaptic package manager envy-ng has actually been added to hardy's official repositories.  Again, not helpful but just a note.

---

### Post by Ub1476 on 2008-04-24
Make sure the repos are checked and up to date, also do not use the main server. Then, check the driver and restart X: Control+alt+backspace. Hope that works:)

---

### Post by screaminj3sus on 2008-04-24
Yeah I had to use a different server and refresh the list, then it let me enable the driver. The main servers are f'd right now, click on "choose best server"

---

### Post by cogadh on 2008-04-24
> **mikespug said:**
> This comment won't help you install the drivers without using envy but, rather, is in response to your comment regarding packages in official repositories.  If you do a search through synaptic package manager envy-ng has actually been added to hardy's official repositories.  Again, not helpful but just a note.
Good to know (learn something new every day), but it doesn't change the fact that Envy installs non-official packages which make kernel upgrades a pain to complete.

> **Ub1476 said:**
> Make sure the repos are checked and up to date, also do not use the main server. Then, check the driver and restart X: Control+alt+backspace. Hope that works:)

> **screaminj3sus said:**
> Yeah I had to use a different server and refresh the list, then it let me enable the driver. The main servers are f'd right now, click on "choose best server"
See, I knew I was missing something basic. I completely forgot how choked the main repo servers get on release day. Unfortunately the "choose best server" option doesn't seem to work with Kubuntu Remix, so I just picked one that I happen to know is only a few towns over from me. Worked great, driver installed, everything is cool. Thanks!

---

