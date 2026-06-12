---
title: "Removing Evolution Client"
date: 2005-12-28
forum: Installation &amp; Upgrades
---

### Post by Hangetsu on 2005-12-28
I have Ubuntu working pretty well at this point, and I've gone ahead and installed Thunderbird client for email.

In an attempt to keep the clutter down on my machine, I was going to remove the Evolution email client.  However, when I was ready to do this, Synaptic warned that I would also have to remove the GNOME CLIENT!

Are they really linked in this way?  Is there any way to disable Evolution while keeping Gnome intact?

---

### Post by imrumpf on 2005-12-28
The best thing to do is to just use the menu editor (Applications --> System Tools --> Applications Menu Editor) and uncheck the appropriate program. While many progams can be uninstalled using apt-get, ones (such as this) it would be wise to just leave it alone and hide it instead.

---

### Post by dcstar on 2005-12-28
[QUOTE=Hangetsu]I have Ubuntu working pretty well at this point, and I've gone ahead and installed Thunderbird client for email.

In an attempt to keep the clutter down on my machine, I was going to remove the Evolution email client.  However, when I was ready to do this, Synaptic warned that I would also have to remove the GNOME CLIENT!

Are they really linked in this way?  Is there any way to disable Evolution while keeping Gnome intact?[/QUOTE]
On my system you can easily remove the Evolution client, it is only the Evolution-data-server package that links to the Gnome stuff.

---

