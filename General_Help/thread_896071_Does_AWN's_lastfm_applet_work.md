---
title: "Does AWN's lastfm applet work?"
date: 2008-08-20
forum: General Help
---

### Post by Washer on 2008-08-20
[[IMG]http://img149.imageshack.us/img149/9691/screenshotyi9.png[/IMG]](http://imageshack.us)
[[IMG]http://g.imageshack.us/g.php?h=149&i=screenshotyi9.png[/IMG]](http://g.imageshack.us/g.php?h=149&i=screenshotyi9.png)

That's all it shows. It logs in with my password, but it won't play.

I'm using hardy's AWN 0.3.1 & lastfm applet v0.3 from [this site]("http://wiki.awn-project.org/index.php?title=Last.Fm_Applet#Bugs_and_feedback"). 

When running it from terminal, it gives a number of weird errors i can't parse.


eg when adding the applet from the manager:
```
(avant-window-navigator:8446): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `GObject'

(avant-window-navigator:8446): GLib-GObject-CRITICAL **: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed

(avant-window-navigator:8446): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `GObject'

(avant-window-navigator:8446): GLib-GObject-CRITICAL **: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
Creating new applet :/home/ubuntuuser/.config/awn/applets/lastfm.desktop uid:1219279395

** (awn-applet-activation:8565): WARNING **: Please inform the developer(s) of the applet 'Last.fm Player Applet (v0.3)' that the .desktop file associated with their applet need to be updated per the Applet Development Guidelines on the AWN Wiki.


```


Copy-pasting the stream URL works so i think it's purely a AWN issue.

---

### Post by Washer on 2008-08-21
bump halp?

---

### Post by moonbeam on 2008-08-22
Remove the LastFM you have installed and use the one that is included in Awn-Extras.  

It works here.  If the one in awn-extras has any issues please file a bug at [https://bugs.launchpad.net/awn-extras/](https://bugs.launchpad.net/awn-extras/)

Thanks,

---

### Post by Washer on 2008-08-23
Tried that already, no dice. I even got to using the trunk versions of everything & lastfm still doesn't work.

---

### Post by moonbeam on 2008-08-23
> **Washer said:**
> Tried that already, no dice. I even got to using the trunk versions of everything & lastfm still doesn't work.

My suggestion is to run awn from a terminal, file a bug report and copy and paste any terminal output into the bug report.

---

### Post by Washer on 2008-08-24
Yeah, thanks but i'll pass. Sometimes i wonder how much we lose by making people create an account.

---

### Post by nmcgrew on 2010-02-20
I can't make this work either.  I've removed the applet and then added [activated] from the AWN manager and still nothing.  I grow so weary of things not working in Ubuntu or having to do all kinds of crazy coding things to make something work.  I've been using Ubuntu for two months now and am so disappointed.  It is not user friendly nor ready for mainstream users.  *growl*  Can anyone help with THIS issue?  Thanks!

---

### Post by IcarianVX on 2010-03-03
Maybe the licensing thing is why it is still broken?

[http://wiki.awn-project.org/LastFm_Applet](http://wiki.awn-project.org/LastFm_Applet)

---

