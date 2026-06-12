---
title: "Can't sync: &quot;Unknown pilot&quot;"
date: 2005-12-01
forum: General Help
---

### Post by argotnaut on 2005-12-01
Hi,

I am trying to sync a Sony Clie TH55 with Evolution via USB cable. Setup was successful in retrieving the username and ID from the Clie, so I know the device is set correctly.

Every time I press the synch button, though, I get this warning message:

[INDENT]Unknown pilot - no pilots matches ID - [ID# here]
Use gnomecc to set pilot's ID[/INDENT]

Sync is aborted at this point.

I have checked the ID number in the device and the sync configuration, and everything matches.

I have 5.10 and have installed the latest updates.

Does anyone know what might be going on here and how I can fix this?

---

### Post by argotnaut on 2005-12-02
More details.

I deleted ~/.gnome2/gnome-pilot.d/ and started over, watching very carefully.

When setup retrieves the ID, it's _different_ than the one it's complaining about later.

Also, it is _not_ saving the ID in the gpilotd file. This is what shows up:

```
[Pilot0]
name=MyPilot
pilotid=0
creation=0
romversion=0
pilotusername=argotnaut
basedir=/home/argotnaut/MyPilot
```

I tried manually editing the ID in this file with both the ID it complains about, and the one that showed up when it tried to retrieve it. Still nothing! 

Should "creation" and "romversion" have something in there, too? If so, where can I find what needs to go there?

Help! Tearing out hair!

---

### Post by argotnaut on 2005-12-02
Oops -- I guess I should have started this thread in the Hardware section. Sorry.

Anyway, it looks like this problem is related to  [this page]("http://mail.gnome.org/archives/gnome-pilot-list/2003-December/msg00000.html") and [this page]("http://www.pilot-link.org/book/print/27") (footnote under the Sony table says:

> * To make the newer Cli&#233; devices work with gnome-pilot, they must be added to a hardcoded list of devices in gpilotd.c (USB ids in vendor_product_ids and an additional product_net = TRUE)).                                

But I can't find anything named gpilotd.c. Does anyone know if and where it exists in Ubuntu? :confused:

---

