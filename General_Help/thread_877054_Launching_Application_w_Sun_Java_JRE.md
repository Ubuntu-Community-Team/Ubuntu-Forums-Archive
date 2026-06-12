---
title: "Launching Application w/ Sun Java JRE?"
date: 2008-08-01
forum: General Help
---

### Post by CarlosinFL on 2008-08-01
I have the package sun-java6-jre installed on my Ubuntu machine and I am trying to launch a file that requires JRE however it does not know how to associate the file with the application. Can anyone please help me make the association in Ubuntu / Gnome?

---

### Post by tinny on 2008-08-01
> **Carlwill said:**
> I have the package sun-java6-jre installed on my Ubuntu machine and I am trying to launch a file that requires JRE however it does not know how to associate the file with the application. Can anyone please help me make the association in Ubuntu / Gnome?

First try just downloading that viewer.jnlp file to your desktop. The right click > Properties > Open with > Add > "Sun Java 6 Web Start".

If you dont see "Sun Java 6 Web Start" as an option you may have to install the Sun Java 6 browser plug-in (which you should have anyway).

```

sudo apt-get update
sudo apt-get install sun-java6-plugin

```

The browser plugin will allow you to run Java Applets within your browser etc...

---

### Post by CarlosinFL on 2008-08-04
Thanks - I was missing the browser plugin.

---

