---
title: "[SOLVED] scim doesn't work in gtk apps anymore"
date: 2008-10-22
forum: General Help
---

### Post by ichigo on 2008-10-22
Since I've done the usual updating a few days ago, SCIM doesn't work on any app using gtk (e.g. gedit, firefox, openoffice...) anymore.
In kde apps (e.g. Amarok, KWrite...) SCIM still works like a charm.
When I start a gtk app from the terminal, I get the following messages:
```
$ gedit
/usr/bin/scim
The messenger is now down
The messenger is now down
/usr/bin/scim
The messenger is now down
An IOException occurred at scim_bridge_client_imcontext_set_cursor_location ()
/usr/bin/scim
The messenger is now down
An IOException occurred at scim_bridge_client_imcontext_set_cursor_location ()
The messenger is now down
The messenger is now down

```

I run the intrepid beta (upgrade from 8.04) on my machine. I know I should file a bug report because of this, but haven't done so because I don't know which package causes the problem...

Any ideas how to fix this?

Edit:
I've just googled a bit more and found that the bug is already posted at launchpad.
As suggested there, launching firefox (or other programs) with the command ```
XMODIFIERS='@im=SCIM' GTK_IM_MODULE="scim" LC_CTYPE=en_US.UTF-8 firefox
```
works as a workaround...

---

### Post by ichigo on 2008-10-23
Arne Goetje's packages (repo posted on [https://bugs.launchpad.net/ubuntu/+source/scim-bridge/+bug/276159](https://bugs.launchpad.net/ubuntu/+source/scim-bridge/+bug/276159)) have solved my problem!

...Hope this may help anybody, who has the same problem...

---

