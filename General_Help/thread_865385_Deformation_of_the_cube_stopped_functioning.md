---
title: "Deformation of the cube stopped functioning"
date: 2008-07-20
forum: General Help
---

### Post by bp1509 on 2008-07-20
It seems no matter what I do I cannot get the sphere or cylinder back.  I have removed/purged the following:

```
compiz compizconfig-backend-gconf  compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins emerald compiz-core
```

Deleted the .compiz folder from my home directory, rebooted.  Reinstalled all of the above, and I will select Desktop Cube, Rotate Cube, and Cube Reflection/Deformation.  And I'm right back at the initial problem.

The odd thing is, it seems even through all of this, certain settings are saving.  Such as the background image the sits behind the spinning cube and various other settings. 

I just need a way to get back to defaults and erase ALL saved settings I'm thinking and start from scratch b/c lord knows I can't figure out what's breaking the sphere.  

Btw, even when the sphere is on, all i get is a spinning cube.

---

### Post by Dynaflow on 2008-07-20
Did you reinstall Compiz using the default version for Hardy (what the package manager would automatically give you), or did you reinstall the new version (0.7.6) from the Compiz people's repositories?  You need the new version to get the nifty sphere thing.

---

### Post by bp1509 on 2008-07-20
> **Dynaflow said:**
> Did you reinstall Compiz using the default version for Hardy (what the package manager would automatically give you), or did you reinstall the new version (0.7.6) from the Compiz people's repositories?  You need the new version to get the nifty sphere thing.

I have the new version from:

```
##Compiz Unstable
deb http://ppa.launchpad.net/compiz/ubuntu hardy main
deb-src http://ppa.launchpad.net/compiz/ubuntu hardy main

```

And it was working at one time.  It simply, randomly stopped working and now only gives me the cube.

---

### Post by Dynaflow on 2008-07-20
Make sure Desktop Cube, Rotate Cube, and Cube Reflection and Deformation are all enabled.  In the Reflection and Deformation submenu, there's a Deformation tab.  Is Deformation set to Sphere and are all the boxes there checked?

---

### Post by bp1509 on 2008-07-20
> **Dynaflow said:**
> Make sure Desktop Cube, Rotate Cube, and Cube Reflection and Deformation are all enabled.  In the Reflection and Deformation submenu, there's a Deformation tab.  Is Deformation set to Sphere and are all the boxes there checked?

Yup.  All are enable, and the deformation has been set to sphere, and it has been set to cylinder.  Neither work

---

### Post by Dynaflow on 2008-07-20
Hrm.  Did you recently change settings for anything else tangentially related to the desktop manager(s)?

You may have better luck asking about this at the Compiz forums, since the Compiz version you're using isn't a standard Ubuntu package yet.  You're more likely to run into someone with similar problems (and, with luck, a solution) over there.  [http://forum.compiz-fusion.org/]("http://forum.compiz-fusion.org/")

---

### Post by bp1509 on 2008-07-20
by the way, the deformaiton plugin works just fine and dandy when i created another user and turned the effect on.  

Purging again, all of the packages listed above.
Deleting the /home/username/.compiz folder, the /home/username/.config/compiz folder

and reinstalling everything doesn't seem to do anything.  And somewhere the settings from my previous install (backgrounds when the cube spins) are still set.  Where can i delete the old install / config files if not those 2 directories?

---

### Post by steveneddy on 2008-07-20
Silly question, but did you try a restart?

---

### Post by bp1509 on 2008-07-20
Sure did, numerous times.

And like i stated as well, this still works for newly created user accounts.  Just not mine.

---

### Post by steveneddy on 2008-07-20
> **bp1509 said:**
> Sure did, numerous times.

And like i stated as well, this still works for newly created user accounts.  Just not mine.

Interesting.....

---

### Post by bp1509 on 2008-07-21
Well issue is fixed by migrating to another user account.  Issue was never fixed but I guess this will do :)

---

### Post by Dynaflow on 2008-07-22
That's definitely weird.  If you ever figure out what happened and how to fix it, would you mind posting back here in case someone else has the issue and is searching for an answer?  

Thanks.  :wink:

---

### Post by chemik4ever on 2008-07-22
Hi!
I'm new to the forum, but i managed to solve similar problem.

I just used howto about removing compiz along with configuration:
[http://www.ubuntugeek.com/howto-remove-compiz-fusion-including-config-files.html]("http://www.ubuntugeek.com/howto-remove-compiz-fusion-including-config-files.html")

Just do the part about removing config files.
I deleted all .gconf and .gconfd folders and lost all settings in gnome, so be carefull ;)

---

### Post by MattJ100 on 2008-08-02
Got it :)

I had exactly the same problem. It worked when I removed .gconf, but I wanted to know exactly what the problem was. After testing settings one-by-one, I can reveal the problem...

apps/nautilus/preferences/show_desktop

It tells Nautilus whether to manage the desktop. If you have it disabled, cube deformation simply won't work.

Alt+F2 to run gconf-editor, navigate to the key above, and place a tick next to show_desktop.

After enabling it again you need to Alt+F2 again, and run "nautilus". This will cause all those icons cluttering your desktop to re-appear, but at least compiz should be working \\:D/

---

### Post by MattJ100 on 2008-08-04
Update...

It isn't necessary to turn on Nautilus if you enable the Compiz "Wallpaper" plugin. Thanks to coz in #compiz-fusion for leading me to discover this :)

---

### Post by techturkey on 2009-01-18
I had the same problem and going into the gconf-editor and found the nautilus in the apps menu, turned on the show desktop and it worked again. Thanks.

---

