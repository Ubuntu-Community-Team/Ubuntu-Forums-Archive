---
title: "Question Regarding Themes"
date: 2008-09-07
forum: General Help
---

### Post by Mongo5000 on 2008-09-07
Im looking for a bit of clarification regarding this.

I just upgraded to ubuntu HH and am looking for a nice theme.

I know about openbox, gnome, kde, etc... but found this and uncertain what this means.

Found this theme
[http://www.gnome-look.org/content/show.php/Royalty?content=67866](http://www.gnome-look.org/content/show.php/Royalty?content=67866)

It says "gtk-xfce-engine".  That means it won't run in gnome will it?  Only Xfce right? or is it just an engine I need to install in gnome .... ?

---

### Post by billgoldberg on 2008-09-07
No, that theme will work in gnome.

It could be that you will need to install that engine using synpatic, I'm not sure.

If you need some good themes, I'm currently using these two on my computers:

[http://www.gnome-look.org/content/show.php/Mire+v2+themepack?content=51023](http://www.gnome-look.org/content/show.php/Mire+v2+themepack?content=51023)

and this one:

[http://www.gnome-look.org/content/show.php/ClearGlow?content=88122](http://www.gnome-look.org/content/show.php/ClearGlow?content=88122)

--

Also, you might find my guide on customizing Ubuntu's look and feel useful.

The link is in my signature.

--

Gnome and KDE are DE's (desktop environment).

A DE is everything that comes with your preinstalled desktop.

The panels, the apps, the themes, ...

Openbox, fluxbox, ... are WM's (Window Manager).

A window manager simply manages the apps on your desktop. (the WM on Gnome is metacity or Compiz Fusion).

You can install as many WM's or DE's as you want, but you can only use one at the time.

You can pick which one to use in your login screen.

---

### Post by urukrama on 2008-09-07
> **Mongo5000 said:**
> It says "gtk-xfce-engine".  That means it won't run in gnome will it?  Only Xfce right? or is it just an engine I need to install in gnome .... ?

Yes, you can use that theme in Gnome (or with window managers like Openbox). It is a Gtk theme that uses the Xfce (and Mist) engines. The Xfce engine is the one used by default in Xfce, but does not depend on it. It is like any other Gtk engine (Murrine, Clearlooks, Rezlooks, etc.) You can install the Xfce engine with the following command:

```
sudo aptitude install gtk2-engines-xfce
```

The Mist engine, which is also used by the royalty theme, is installed by default (it is part of the gtk2-engines package).

See [this page]("http://art.gnome.org/faq.php#q5") for more info on Gtk engines.

---

### Post by Mongo5000 on 2008-09-07
awesome, thx for the info!

Im coming up quickly on my 1 year anniversary of 100% linux and I think I know a few things, but this one just stumped me. 

I just remember installing themes a while ago and some not working, now it hit me that perhaps I didn't have the proper engines installed to make them work and was wondering if gtk-xfce-engine was just another one I never ran across.

Perhaps its that it said xfce ... not sure.

Im a fan of dark themes too :)

---

