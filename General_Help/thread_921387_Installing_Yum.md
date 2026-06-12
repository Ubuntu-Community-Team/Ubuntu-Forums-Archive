---
title: "Installing Yum?"
date: 2008-09-16
forum: General Help
---

### Post by rugbert on 2008-09-16
I just noticed that I can use apt-get to install yum in ubuntu.

Thats kind of awesome because I dont really care for this apt stuff. I really like the output that searching gives you (if its installed or not) but I really dont like having to modify the command to use a search feature.


But before I go ahead and install it, what does it change? Does it change the same repos and features (esp the output of searching), that wouldnt make much sense but just asking. Im assuming it just lets me use the yum commands

---

### Post by mali2297 on 2008-09-17
[QUOTE="Package description"]Yum (Yellow dog Updater, Modified) is an automatic updater and package installer/remover for rpm systems. It automatically computes dependencies and figures out what things should occur to install packages. It makes it easier to maintain groups of machines without having to manually update each one using rpm.[/QUOTE]

My interpretation is that you can only use it to install rpm packages. Since the Ubuntu repositories use the debian package system, I don't think this app is very useful.

---

### Post by tommygunner on 2008-09-19
Maybe if you just want to type "yum" instead of apt-get you can create an alias or something. I prefer typing "yum" as opposed to "apt-get".

---

### Post by LowSky on 2008-09-19
Yum and apt-get/aptitude are very simular these days, with only the  files extension being the differences

Synaptic is very simular to Yum Extender

If you are so inclinded to Yum, why not use Fedora?

---

### Post by bingoUV on 2008-09-19
LowSky, yum and apt-get are very different to use. They use a whole different language of regular expressions if you want to search for an installed/available package. The insistence of apt-get to treat upgrade and update as totally different sometimes gets on my nerves ;). I still don't remember which is which.

Suffice to say, yum "skills" don't transfer very easily to deb based distros. Though some guys might have the same problems dealing with rpm based distros.

---

