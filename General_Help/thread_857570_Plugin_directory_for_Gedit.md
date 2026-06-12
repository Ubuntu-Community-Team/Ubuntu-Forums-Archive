---
title: "Plugin directory for Gedit?"
date: 2008-07-12
forum: General Help
---

### Post by Melindrea on 2008-07-12
I've been trying to install HTML-tidy Gedit Plugin (instructions found [here]("http://www.eng.tau.ac.il/~atavory/gedit-plugins/html-tidy/")). Problem is this: There is no such directory, and I have no idea how to find the directory for plugins.

So. Suggestions? =)

---

### Post by Vivaldi Gloria on 2008-07-12
> **Melindrea said:**
> I've been trying to install HTML-tidy Gedit Plugin (instructions found [here]("http://www.eng.tau.ac.il/~atavory/gedit-plugins/html-tidy/")). Problem is this: There is no such directory, and I have no idea how to find the directory for plugins.

So. Suggestions? =)

```
/usr/share/gedit-2/plugins
```

---

### Post by Melindrea on 2008-07-12
Many thanks.
*marks as solved*

---

### Post by Vivaldi Gloria on 2008-07-12
> **Melindrea said:**
> Many thanks. 

You're welcome.

---

### Post by jomex on 2010-07-11
i'm using 10.04 and the only directory that works for me is: /usr/lib/gedit-2/plugins/

from [http://live.gnome.org/Gedit/PythonPluginHowTo](http://live.gnome.org/Gedit/PythonPluginHowTo)

---

### Post by JMJMJM on 2011-01-28
When I install the plugin to /usr/lib/gedit-2/plugins, the plugin appears in gedit >edit > preferences > plugins and can be selected but none of the advertised new menu items (like tools > Tidy Check) appear and when I try to configure the plugin (edit > pref > plugins > HTML Tidy > Configure Plugin) nothing happens.

I suspect I have a permissions/ownership problem.  Can someone who has this working share the ownership and permissions for the plugin files and folders in their installation?

FTR, I am running Ubuntu 10.04

---

### Post by JMJMJM on 2011-01-28
I figured it out.  I had installed the plugin into /usr/lib/gedit-2/plugins per a post as opposed to following the developer's installation instructions which say to install to ~/.gnome2/gedit/plugins

I went back and installed to ~/.gnome2/gedit/plugins and EVERYTHING works as advertised.

---

### Post by RonCam on 2011-01-28
I'm trying to install Autocomplete, and am encountering the same problem: it's not appearing in Gedit's menu.  

...
[edit: directory in question has been located]

The problem remains with the entry not being in Gedit's menu, however.  Autocomplete's version 11 was released very recently.  I'm going back to version 10 to see if the problem lies there.

OS: Leeenux 4.1 (Ubuntu modified for the ASUS EeePC)

P.S.: Probably best if I start a new thread?

---

