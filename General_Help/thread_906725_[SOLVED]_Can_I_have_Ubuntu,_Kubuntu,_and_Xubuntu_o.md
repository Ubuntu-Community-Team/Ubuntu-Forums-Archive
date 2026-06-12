---
title: "[SOLVED] Can I have Ubuntu, Kubuntu, and Xubuntu on the same computer?"
date: 2008-08-31
forum: General Help
---

### Post by FastMady123 on 2008-08-31
I have Ubuntu (GNOME) and Xubuntu (Xfce) installed. I may want to install Kubuntu (KDE). I know to install it. Can I have Ubuntu, Kubuntu, and Xubuntu on the same computer? is there a limit of how many desktop environments I can install? Will this make my computer slow?

---

### Post by ibuclaw on 2008-08-31
Depends how you want to go about it.

You can shrink your current Ubuntu partition and make two new partitions in it's place for installed Kubuntu and Xubuntu in.
That way, you have a choice of OS at bootup.

Or you can grab the kubuntu-desktop and xubuntu-desktop packages from apt and have them merged with your current one (select them with the "Sessions" menu during login).

As for slowness, no, it shouldn't low down your computer at all, but your applications menu may get bloated with many apps that are for the same task (gedit, mousepad, kwrite), (gnome-terminal, terminale, konsole), etc.

You can install them to try them out, there is no harm in that.
If you feel that yuo don't like KDE or Xfce, there are plently of scripts around which shall bring you back to normality. ;)

Regards
Iain

---

### Post by kjohansen on 2008-08-31
here is a link to a tutorial i used to get back to plain gnome after installing kubuntu-desktop and xubuntu-desktop ontop of gnome.

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

