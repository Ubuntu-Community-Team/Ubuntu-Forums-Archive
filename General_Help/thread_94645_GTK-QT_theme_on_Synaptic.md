---
title: "GTK-QT theme on Synaptic"
date: 2005-11-24
forum: General Help
---

### Post by Licaon on 2005-11-24
i have breezy+kubuntu desktop

in KDE how can i get Synaptic to use the gtk-qt theme??

it now uses some ugly theme that does not look like my gnome themes or my kde themes

any ideas??

10x

---

### Post by invalid on 2005-11-24
Try```
sudo apt-get install gtk2-engines-gtk-qt
```and restart X.

Cheers,
Cb

---

### Post by ltmon on 2005-11-24
I assume from your posts that the gtk-qt theme is working for your other gnome apps?

The reason it isn't working for synaptic in this case is that synaptic runs as root  user and uses your root user settings.  The gtk-qt theme is only set up for your unpriviledged user.

Type:

> sudo kcontrol

and then go set up gtk-qt again.

You should be fine now.

L.

(p.s. why not try adept instead -- I have grown to like it better than synaptic :))

---

### Post by kairu0 on 2005-11-24
[QUOTE=ltmon]
Type:

> sudo kcontrol
[/QUOTE]

I think it would be wiser to run "kdesu kcontrol."

---

### Post by ltmon on 2005-11-24
[QUOTE=kairu0]I think it would be wiser to run "kdesu kcontrol."[/QUOTE]

There's no difference at all in the operation of the program.  Just typing at the command line as opposed to getting a dialog box.

L.

---

### Post by Licaon on 2005-11-24
i thought about running sudo kcontrol (i'm not on that machine now)... i'll try it today...

but (scroll down to the last post):
Adept problem: [http://ubuntuforums.org/showthread.php?t=93169](http://ubuntuforums.org/showthread.php?t=93169)

Synaptic problem: [http://ubuntuforums.org/showthread.php?t=67523](http://ubuntuforums.org/showthread.php?t=67523)

10x

---

### Post by kairu0 on 2005-11-25
[QUOTE=ltmon]There's no difference at all in the operation of the program.  Just typing at the command line as opposed to getting a dialog box.

L.[/QUOTE]

There is a big difference between the two: sudo changes .ICEauthority permissions. I ruined one of my user accounts by doing a "sudo kcontrol" this last week.

Take a look at this thread:

[http://www.ubuntuforums.org/showthread.php?t=92914](http://www.ubuntuforums.org/showthread.php?t=92914)

---

### Post by Licaon on 2005-11-25
that worked... kdesu kcontrol 

10x

i still have those synaptic/adept problems...

---

