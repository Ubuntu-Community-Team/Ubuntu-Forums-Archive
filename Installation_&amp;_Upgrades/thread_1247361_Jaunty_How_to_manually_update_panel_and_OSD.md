---
title: "Jaunty: How to manually update panel and OSD?"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by kr0m3 on 2009-08-22
ok, when i upgraded from Intrepid to Jaunty, I got the message:

"There is now a combined status menu for instant messaging status, switching user accounts, and exiting Ubuntu"....etc.

but i didn't click update, as i was seriously multitasking at the time.  Well, long story short, i can't reproduce the message prompt and i am stuck with the intrepid logout (as well as everything else on the panel) and my OSD for volume, etc is still old-school as well.  I have removed and replaced the logout applet, etc... i've updated all packages, i've googled till i'm blue in the face, but i can't seem to find the procedure to manually update these elements to the new jaunty versions.

any help is naturally appreciated...
peace
~k

---

### Post by kr0m3 on 2009-08-24
well, i got the OSD problem figured, but still have the same old logout/reboot applets.

thoughts?
~k

---

### Post by qamelian on 2009-08-24
Right-click on the panel and select 'Add to panel'. The applet you are looking for is the Fast User Switcher.

---

### Post by kr0m3 on 2009-08-28
the damn thing wasn't installed, hence me not locating anything useful within the applets listings.

```
sudo apt-get install fast-user-switch-applet
```

and then adding it to the panel did the trick.

thnx
~k

---

