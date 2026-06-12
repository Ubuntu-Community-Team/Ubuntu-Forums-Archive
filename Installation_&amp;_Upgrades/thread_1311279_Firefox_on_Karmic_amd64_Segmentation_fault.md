---
title: "Firefox on Karmic amd64 Segmentation fault"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by NEUR0M4NCER on 2009-11-02
Firefow crashes every time I try to go to Facebook's 'My Profile' page. Running from a terminal starts with errors like this:
```

(firefox:4513): Gdk-WARNING **: XID collision, trouble ahead

(firefox:4513): Gdk-WARNING **: XID collision, trouble ahead

(firefox:4513): Gdk-WARNING **: XID collision, trouble ahead

(firefox:4513): Gdk-WARNING **: XID collision, trouble ahead

(firefox:4513): Gdk-WARNING **: XID collision, trouble ahead

(firefox:4513): Gdk-WARNING **: XID collision, trouble ahead

(firefox:4513): Gdk-WARNING **: XID collision, trouble ahead

(firefox:4513): Gdk-WARNING **: XID collision, trouble ahead

```
Then when I try to open the page in question, it gives me this:
```

(firefox:4513): Gdk-WARNING **: XID collision, trouble ahead
Segmentation fault (core dumped)

```
Is this actually a bug, or have I done something daft in the upgrade process (like still booting from the old kernel - fixed that one!)?

---

### Post by mcbarron on 2009-11-02
It's a real bug: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/401823](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/401823)

I'm seeing it too.  Fix of removing the logging messages should come along shortly (according to the bug report).

---

### Post by michaelzap on 2009-11-02
Sounds exactly like the infamous Gmail crash caused by the latest alpha of Flash from Adobe's website. I had this and I ended up deleting my Flash plug-in and installing the (older and also buggy) version using Synaptic. That fixed the crashes, although it does come with UI problems while running Compiz.

---

### Post by NEUR0M4NCER on 2009-11-03
Nuts. How might I go about removing said buggy Flash?

---

### Post by michaelzap on 2009-11-03
> **NEUR0M4NCER said:**
> Nuts. How might I go about removing said buggy Flash?

Depends on how you installed it, but usually it's in /usr/lib/mozilla/plugins. In that case you just need to delete it (using sudo or gksudo nautilus). You might have also copied it to your local .mozilla directory in your home folder, in which case you just delete it there.

Then use Synaptic to install flashplugin-nonfree from the repos.

---

### Post by lessoffensive on 2009-11-30
This XID bug has been long standing for the past 6 months without a clear fix.  The best patch I've found so far has been from Gnome for GTK--I've patched gtk and put it onto a PPA.  That PPA can be found here:

[https://launchpad.net/~lessoffensive/+archive/lessoffensive/]("https://launchpad.net/%7Elessoffensive/+archive/lessoffensive/")

The author of the patch says that he hasn't experienced anymore crashes after this patch, but says that it's a quick and dirty hack that doesn't fix the underlying problem.  I'm going to test this on my system shortly.

---

