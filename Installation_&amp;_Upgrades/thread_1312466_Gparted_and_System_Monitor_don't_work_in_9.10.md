---
title: "Gparted and System Monitor don't work in 9.10"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by the8thstar on 2009-11-03
The title says it all... I get weird error messages which I can't report with Apport.

Here you are :

> the8thstar@the8thstar-desktop:~$ sudo **gparted**
[sudo] password for the8thstar: 
======================
libparted : 1.8.8.1.159-1e0e
======================

GLib-GObject-ERROR **: Attempt to add property GtkMenuBar::local to class after it was derived
aborting...

and :

> the8thstar@the8thstar-desktop:~$ sudo **gnome-system-monitor**

** (gnome-system-monitor:26573): WARNING **: SELinux was found but is not enabled.


GLib-GObject-ERROR **: Attempt to add property GtkMenuBar::local to class after it was derived
aborting...
Aborted (core dumped)

So, what could be the problem here? It occurs on two machines (one upgraded from 9.04, the other with a clean 9.10 install. Thanks for your help.

---

### Post by the8thstar on 2009-11-03
Bump

---

### Post by Ginsu543 on 2009-11-03
Are you by any chance running the Global Menu applet? I had exactly the same problem as you until I got rid of Global Menu.

---

### Post by drs305 on 2009-11-03
Also, run those GUI apps with "gksu" - i.e. "gksu gparted".

---

### Post by the8thstar on 2009-11-04
> **Ginsu543 said:**
> Are you by any chance running the Global Menu applet? I had exactly the same problem as you until I got rid of Global Menu.

Yes, I am actually. Getting rid of the applet doesn't solve the problem or bring the actual menus back btw. Is there a workaround?

---

### Post by the8thstar on 2009-11-04
> **drs305 said:**
> Also, run those GUI apps with "gksu" - i.e. "gksu gparted".

Why? How should it be different than invoking them from the main menu?

---

### Post by drs305 on 2009-11-04
> **the8thstar said:**
> Why? How should it be different than invoking them from the main menu?

It wouldn't be different from running it from the main menu. It *would* be different than running them with "sudo", as was mentioned. It may not be the cause of the problem, it is just good practice.

Here is a link that explains it:
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by szerencsefia on 2009-11-04
> **drs305 said:**
> Also, run those GUI apps with "gksu" - i.e. "gksu gparted".

Did not help. The problem remains.

But when disable global-menu gparted start up with no fail.

More: [https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/471295](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/471295)

---

### Post by drs305 on 2009-11-04
Are you by chance using the Global Menu applet? I have found lots of reported problems with symptoms similar to what you are describing. I don't use it and don't even know you access it, but if it is enabled you can use this command to scroll through your applets, looking for one that says "OAFIID:GNOME_GlobalMenuApplet"

```

gconf-editor /apps/panel/applets

```

---

### Post by szerencsefia on 2009-11-04
Is it me who you are writing to?

---

### Post by drs305 on 2009-11-04
> **szerencsefia said:**
> Is it me who you are writing to?

Hah! Yes, actually it was. I started searching for an answer and left the post open while I looked around for an answer. Apparently you had discovered this without any need of my assistance.

---

### Post by Ginsu543 on 2009-11-04
Did you just remove Global Menu from the Gnome panel or did you go into its Preferences and click on Disable before you removed it from the panel? When I simply removed it from the panel my problems persisted but they went away once I actually disabled Global Menu before removing it.

---

### Post by szerencsefia on 2009-11-07
> **Ginsu543 said:**
> Did you just remove Global Menu from the Gnome panel or did you go into its Preferences and click on Disable before you removed it from the panel? When I simply removed it from the panel my problems persisted but they went away once I actually disabled Global Menu before removing it.

I only disabled for the time period I worked with Gparted. I did not remove it.

---

### Post by Tallguitarguy on 2011-12-05
Not meaning to bring an old thread back from the grave, but if anyone needs to know, I had the same problem in 11.04 and simply disabling global menu in the preferences worked.

---

### Post by coffeecat on 2011-12-05
Old thread - closed.

---

