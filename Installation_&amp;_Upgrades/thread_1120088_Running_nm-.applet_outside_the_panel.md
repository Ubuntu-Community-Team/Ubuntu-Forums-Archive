---
title: "Running nm-.applet outside the panel?"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by saltydog on 2009-04-08
Is there any way to run the NetworkManager-applet outside from the panel? I am trying to setup a minimal environment, with just one graphical application running, without any panel but I am missing NetworkManager as I need it to join a wireless access point before running the application.

How can I select the access point to join, without panels? Is there a standalone application for gnome which behaves as NetworkManager applet?

---

### Post by Jose Catre-Vandis on 2009-04-08
You can set up your interfaces file manually and do without network manager altogether. Do you have all the information you need to connect to the wireless network? You may also need to install some stuff; definitely "wireless-tools" anbd possibly ndiswrapper, wpa-supplicant etc.

---

### Post by saltydog on 2009-04-09
Thanks Jose,
I know this but it doesn't work for a simple setup I am trying to put on for first-time users. Just one icon to click on to choose the wireless access point, and another icon to start the application....

---

### Post by Jose Catre-Vandis on 2009-04-09
OK, could you do similar to what i sugest but using launchers and bash scripts?

---

