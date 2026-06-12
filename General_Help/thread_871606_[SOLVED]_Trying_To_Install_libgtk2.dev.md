---
title: "[SOLVED] Trying To Install libgtk2.dev"
date: 2008-07-27
forum: General Help
---

### Post by Mark76 on 2008-07-27
But every time I do I get this

> libgtk2.0-dev:
  Depends: libgtk2.0-0 (=2.12.9-3ubuntu4) but 2.12.9-4ubuntu3 is to be installed

---

### Post by werries on 2008-07-27
It says a newer version of libgtk2.0 is installed, and libgtk2.0-dev requires the old one. I suppose.
So you would need to also install the libgtk2.12.9-3ubuntu4. which is outdated, apparently.

---

### Post by dexter.deepak on 2008-07-27
synaptic has got a "force-version" option (under preferences), see if that works and you can install an older version.
or
either remove 2.12.9-3ubuntu4 and install 2.12.9-3ubuntu3.

---

### Post by Mark76 on 2008-07-27
I don't see a "Force version" option in Preferences.

Perhaps they removed it from Hardy?

---

### Post by Mark76 on 2008-07-28
Bump.

---

### Post by Bachstelze on 2008-07-28
Did you update your packages list recently?

```
sudo apt-get update
sudo apt-get install libgtk2.0-dev
```

---

### Post by Bachstelze on 2008-07-28
Did you update your packages list recently?

```
sudo apt-get update
sudo apt-get install libgtk2.0-dev
```

---

### Post by Mark76 on 2008-07-28
I finally managed to sort it out.

---

### Post by werries on 2008-07-29
mind posting what you did?

---

### Post by Mark76 on 2008-07-29
I used "force version" to downgrade libgtk-2.0.0 itself

---

### Post by minus198 on 2008-08-03
> **Mark76 said:**
> I used "force version" to downgrade libgtk-2.0.0 itself


Can you explain how you did that?

Edit: I think I solved it myself to.

First install the right version of libgtk2.0-0 by doing:
sudo apt-get install libgtk2.0-0=2.12.9-3ubuntu4

This will also uninstall gnome-themes gtk2-engines-pixbuf gtk2.0-examples gucharmap libgtk2.0-bin

Now install libgtk2.0-dev
sudo apt-get install libgtk2.0-dev

and then reinstall gnome-themes gtk2-engines-pixbuf gtk2.0-examples gucharmap libgtk2.0-bin

sudo apt-get install gnome-themes gtk2-engines-pixbuf gtk2.0-examples gucharmap libgtk2.0-bin

---

### Post by Mark76 on 2008-08-04
It's even easier than that.

Find the package you want to install, mark it for installation and then click on Package on the menu bar, click on Force Version, select your version from the pop up and click on Apply

---

### Post by minus198 on 2008-08-04
> **Mark76 said:**
> It's even easier than that.

Find the package you want to install, mark it for installation and then click on Package on the menu bar, click on Force Version, select your version from the pop up and click on Apply

Never thought of using the graphical tool ^^
I'm a "terminal-dude". :P

---

