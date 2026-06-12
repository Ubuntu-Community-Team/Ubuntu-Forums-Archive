---
title: "wine: &quot;unable to find a volume for file extraction...&quot;"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by v1nsai on 2009-06-21
I'm trying to install the zune software under wine and I'm getting smacked with the error "unable to find a volume for file extraction, do you have the proper permissions?".  I've done some research and found that windows installers won't always install to network drives, so I tried the workaround suggested _[here](http://www.winehq.org/pipermail/wine-users/2007-March/024682.html)_ but to no avail.

I then found some information _[here](http://bugs.winehq.org/show_bug.cgi?id=5351)_ on the way certain windows installers make calls to the disk drives, apparently they don't all use the assigned drive letters, but a schema like harddiskdrive1 etc.

I'm not quite getting how to use this fix though....I tried changing the name of ~/.wine/drive_c to harddiskdrive1 but it had no effect.  I looked up the mapping of the drives in wine config but you can't change the location of drive c, it's static and set to .wine/drive_c by default.  Can someone explain how to use this fix or any other solutions to this problem?

<edit>
grabbed the latest deb directly from the site and now I'm getting the error 'Bad EXE format for zunesetup.exe'.  Still researching, its getting late though.  Who the hell can sleep when there's compatibility issues to troubleshoot??
</edit>

---

### Post by Squirrel E. Doom on 2009-08-26
Same problem. Much less experience with Ubuntu. Trying to get Zune to work with 9.4 so I don't ever have to fall out of an open Window(s) again. I will continue to sit here and stare blankly at the screen until it works but if anyone comes up with something in the meantime help would be greatly appreciated. It's really the only thing I would need windows for now.

---

### Post by Mark Phelps on 2009-08-27
Maybe the following link the the CodeWeavers Application Compatibility database page will answer your questions:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=5741]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=5741")

Wine is a useful tool for installing SOME Windows apps.  It's worthless if you need to install any device drivers.  That could be why the Zune stuff simply won't work.

---

