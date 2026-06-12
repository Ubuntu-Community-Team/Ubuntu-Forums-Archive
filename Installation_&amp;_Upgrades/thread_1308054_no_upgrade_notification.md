---
title: "no upgrade notification"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by ehababoud on 2009-10-31
hi,
i've got ubuntu 9.10 beta and i'm trying to upgrade to the stable release but the update manager has not yet told me about the upgrade. i always update the manager and (at times) the updates are larger than 100MB so i am aware that the default software on the 9.10 beta was being improved, i just don't get the same notification as i got in my older computer when i transferred from 8.10-9.04. that was very smooth. could it be an issue with the sources?

when i use the update manager it refers to i think 81 source files (i think). i don't know if that information may help.

i'd love to get the stable release as this one has a few issues with RAM usage (plus the normal one is always better) and i'd prefer to just click the button to upgrade rather than downloading then burning a whole new disc. 

thanks in advance

ehababoud

---

### Post by lemming465 on 2009-11-01
The beta should update (install new packages) smoothly as it transitions from beta to release candidate to final version; updates use the same repositories.  Upgrades change to new repositories (e.g. jaunty -> karmic), among other things.  81 source files sounds like you have a lot of 3rd party stuff enabled, and it's possible some of that is blocking key packages.  You might try temporarily disabling all the non-Ubuntu repositories.

If you aren't getting timely updates, you could try using a different mirror (System -> Administration -> Software Sources; change the "Download from:" dropdown).

At the command line you could try:```

sudo aptitude clean
sudo aptitude update
sudo aptitude full-upgrade
```
and see if that either works, or yields some informative error messages.

---

### Post by 5nak3 on 2009-11-04
I'm not quite sure if my problem is related but I noticed on Karmic the update manager will not startup automatically despite there being updates to be had.

I went into gconf-editor and selected apps->update manager and changed the update notification to 0 from the default 7 meaning that updates should be notified asap.

This is not the case however, and I'm forever having to do manual updates. Any ideas how to correct this?

---

### Post by grandtoubab on 2009-11-04
According to [http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910) 
**Change in notifications of available updates**

  Ubuntu 9.10 launches update-manager directly to handle package updates, instead of displaying a notification icon in the GNOME panel. [COLOR=Red]Users are notified of security updates on a daily basis, but for updates that are not security-related, users will only be prompted once a week.[/COLOR] 
 Users who wish to continue receiving update notifications in the previous manner can restore the earlier behavior using the following command: 
 
 gconftool -s --type bool /apps/update-notifier/auto_launch false  (This change was made in Ubuntu 9.04.)


Maybe you have only to wait, the process don't show the update icone so quickly, but it works I have seen it at least one time:lolflag:

---

