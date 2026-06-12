---
title: "Parse error when trying to update / driver activation problems."
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by Admiral_deLorei on 2008-12-09
From one problem to another...

Anyways, I recently got my sound working thanks to one of the guides on Pulseaudio on here. But now, when I try to update the system, I can't do it from either the update manager or from the terminal.

The error I get when I try sudo apt-get upgrade is:

```
dpkg: parse error, in file `/var/lib/dpkg/status' near line 9305 package `dbus':
 value for `conffiles' has malformatted line `/etc/dbus-1/"'
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Also, I can't activate drivers for some reason anymore. I click activate and they start to activate, but then it just returns me to the driver listing.

Sorry for the double questions, but I figure it's better than making two topics.

---

### Post by Admiral_deLorei on 2008-12-09
Well, I think I figured out the problem. The file /var/lib/dpkg/status does have an error in it (some really random string of symbols), as I saw when viewed in the terminal window. However, I can't go in to edit the file because the computer can't render the fonts. I don't know if there's a way to edit it or not, but I know about where the error is.

Is there any way to view this file?

Edit: I got it. There's a back up of /var/lib/dpkg/status called status-old. I deleted the corrupted file and replaced it with status-old (renamed to status). Updates work now.

---

