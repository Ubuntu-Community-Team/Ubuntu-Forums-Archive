---
title: "[SOLVED] GTK engines - how to check which are installed?"
date: 2008-11-04
forum: General Help
---

### Post by pablopancho on 2008-11-04
Hi everyone!

I'm a little confused with gtk themes and engines. I installed several themes on my ibex but some of them apparently aren't displayed as intended because there's gtk engine missing (that's what theme manager tells me - it must be a new feature in intrepid because I haven't noticed it earlier), e.g. ubuntulooks engine is missing. 

I checked Synaptic and I can install ubuntulooks but that means uninstalling several things (human-theme, ubuntu-artwork, ubuntu-desktop). Why? I want to keep many options so I can change the themes easily. I don't want to uninstall ubuntu-desktop!

And btw. how can I check which engines are installed? It seems strange that you can see and manage various themes, which are based on clearlooks or murrine but there's no evident place for managing the engines themselves.

If anyone can give me some info or link to any useful article I'd be grateful. I hate being ignorant :D

---

### Post by cupevampe on 2008-12-17
i'd love to know the answer to this..
anyone?
thx!

---

### Post by Mahinva on 2008-12-17
After upgrading to Ubuntu 8.10, I too was unable to select certain themes. I am not sure if this will take care of your problem specifically, but I hope it's pertinent information.

[http://ubuntuforums.org/showpost.php?p=6148824&postcount=14](http://ubuntuforums.org/showpost.php?p=6148824&postcount=14)

From thread:

[http://ubuntuforums.org/showthread.php?t=971469](http://ubuntuforums.org/showthread.php?t=971469)

I unfortunately have no answer to your question about finding what engines are installed - sorry!

---

### Post by Prefader on 2008-12-17
Ubuntu-desktop is just a metapackage.  Basically, it's just a collection of dependencies.  Removing this package doesn't remove the dependencies, so it's safe to uninstall it.

Ubuntu-artwork appears to be the same, only it also includes the distributor logo (the ubuntu logo you see next to "applications" on your panel).  Removing this should also be harmless.

Human-theme is the default ubuntu theme.  If you aren't going to use it anymore, it's also safe to remove.  Again, it's mostly dependencies, so removing it won't remove the dependencies.

By the way, you can use the command "apt-cache show <packagename>" to view information on packages, or you can also check their properties in synaptic to find out exactly what a package does for a living.

As far as your main question - a utility for managing gtk engines - I can't help you there, sorry!

---

### Post by pablopancho on 2008-12-18
Thanks guys, I didn't remove any packages from synaptic, I just downloaded blubuntu theme from gnome-look.org and installed it, and it works fine. There is no conflict apparently.

Link posted by Mahinva tells me that I can safely ignore theme manager's complaints about missing "" engine or I can edit theme configuration file (I think I will do the first option - I'm lazy :P )

I poked around my file system and found that some engines can be found in /usr/share/gtk-engines (there are xml files). If those are all of them - beats me. The themes can be found in /usr/share/themes and in /home/username/.themes folders. That's how we can find out what is installed.

I don't think there is any utility to manage gtk engines but sure it would be useful. 

I think we can safely say that the problem is solved.

---

