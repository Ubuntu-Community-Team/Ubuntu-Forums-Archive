---
title: "Feisty 3000 N100 Sound"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by Donnieb on 2007-04-20
For some reason sound isn't working at all in feisty, even doing the acpi=ht on boot no longer renders sound, I've tryed adding the ```
option snd-hda-intel model=laptop-eapd
``` to the modprobe.d/alsa-base file. Still no luck, any other possible fixes that have came about or information needed?

---

### Post by Donnieb on 2007-04-20
I forgot to mention that it was a lenovo, and has anyone had any success with the sound card, sound blaster audigy 2 zs pcmcia type card. Also, is there any way to get the old wireless network manager back, as this one in feisty is... gross,

---

### Post by ashridah on 2007-04-20
I'm getting the same sound issues with the same laptop model. 

Looking through launchpad.net there's a few bugs about sound issues mentioning that a bug got introduced by some patches they were trying to add just before release (sigh, feature freeze much?)

See some of the bugs in launchpad with the search terms [https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=hda-intel+audio&orderby=-datecreated&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=]("https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=hda-intel+audio&orderby=-datecreated&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=")

i'm not sure if there's a workaround yet, although it's something i'll be watching carefully myself ;)

---

### Post by Donnieb on 2007-04-21
This has been fixed, I don't even need the acpi=ht for it to work anymore see alsa bugtracker [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2725]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2725") for fix. It involves recompileing the alsa drivers with 2 modified files, hdaproc.c from realtek1.tar.gz and patch_realtek.c from realtek3.tar.gz. Hope this helps anyone else haveing this problem.

---

