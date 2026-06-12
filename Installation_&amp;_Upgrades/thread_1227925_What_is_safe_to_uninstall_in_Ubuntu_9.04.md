---
title: "What is safe to uninstall in Ubuntu 9.04"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by fenrisW0lf on 2009-07-31
Hi all!

I am a new user to Ubuntu (a little over a week now) and I am really enjoying my experience.

I have a question - what software is safe to uninstall? The reason that I ask is that I went willy-nilly last Sunday uninstalling software that I didn't use (f-spot, tomboy, evolution email and a few other things that I can't quite recall). Suffice it to say that I some how messed up my desktop as I couldn't boot back into the GUI after restarting the system. I think I may have removed something I shouldn't have.

Well I am back up and running and this time I am asking for advice. How can I tell what is safe to remove?

Cheers and thanks,
Troy

---

### Post by Mark Phelps on 2009-07-31
Actually, the short answer is "anything which does not have dependencies", but even there, you can get into trouble.

Unless you're really tight on disk space, there's no downside to just leaving the stuff alone.

---

### Post by wojox on 2009-07-31
Use Synaptic Package Manager and find the application you want to remove. Right click the box and select Mark for complete removal. It will show you any dependencies it will take with it.

---

### Post by vinutux on 2009-07-31
Synaptic is the best way..advanced too

**System>administration>Synaptic Pakage Manager**

---

### Post by slakkie on 2009-07-31
Basically you can delete every package but ubuntu-standard and ubuntu-minimal, which are metapackages that will leave you with a basic CLI system. Run (in a terminal) aptitude -D show ubuntu-standard and aptitude -D show ubuntu-minimal to see which packages will remain.

You will have the ubuntu-desktop package installed (or any other *tu-desktop package depending on your Ubuntu flavor), but I assume you have a Gnome desktop. If you remove some essential Gnome packages you will have problems when starting your GUI sessions. You can easily restore to this by reinstalling the ubuntu-desktop package. This will make sure that all dependencies are met.

---

### Post by fenrisW0lf on 2009-07-31
Thanks for the replies!

I am using the default gnome desktop.

I noticed in synaptic if I take a look at dependencies it sometimes lists recommended dependencies. Are they safe to remove?

Or am I just better off just deleting the launchers out of the application menu?

---

### Post by Zero++ on 2009-07-31
If you just want a cleaner menu go to System>Preferences >Main Menu and can delete the launchers you don't want by simply un checking them. This will keep the program on you hard drive however. Re checking them will put them back on the menu if you decide you need to use it at a later date.

Also if you are just trying to declutter your menus you could get the AWN manager dock and put commonly used programs on the dock and leave your Application menu full access just in case you need that odd program every once and a while.

---

### Post by fenrisW0lf on 2009-08-01
> **Zero++ said:**
> If you just want a cleaner menu go to System>Preferences >Main Menu and can delete the launchers you don't want by simply un checking them. This will keep the program on you hard drive however. Re checking them will put them back on the menu if you decide you need to use it at a later date.

Also if you are just trying to declutter your menus you could get the AWN manager dock and put commonly used programs on the dock and leave your Application menu full access just in case you need that odd program every once and a while.

Those are both good ideas - I really like the AWN dock. In windows I used a program called Rocket dock which looks similar for frequently used applications.

Are there any security issues with leaving programs on you system that you do not use? For me space isn't the issue. Are there any disadvantages? I don't know, I am probably overly worried because I am from windows and not used to the way linux works.

---

