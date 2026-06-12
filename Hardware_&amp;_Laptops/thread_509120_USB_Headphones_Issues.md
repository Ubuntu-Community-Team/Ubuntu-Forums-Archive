---
title: "USB Headphones Issues"
date: 2007-07-25
forum: Hardware &amp; Laptops
---

### Post by bahdom on 2007-07-25
Hi, i have a pair of usb 5.1 headphones [LTB HSMT-UD Mentor True 5.1 Surround Sound USB Headphone] and Linux Ubuntu Feisty. Anyhow, when i go to the sound control panel and press test, i am able to hear the beep clearly and without trouble, but any other sound i cannot hear [except for movies/songs played in VLC].

Any ideas on how to solve this?

---

### Post by mohnkern on 2007-07-25
If you're using Alsa (which unless you changed it, and  you're using Feisty is likely) start by trying the following:


**[INDENT]asoundconf list[/INDENT]**


This will list the sound devices available to you, on my machine it looks like this:

Names of available sound cards:
Live
V8237
U0x46d0x8d7
Headset


Now type:

**[INDENT]asoundconf set-default-card <device>[/INDENT]**

Likely It will be:

**[INDENT]asoundconf set-default-card Headset[/INDENT]**

Some people have said they have to type the above command several times and reboot x (or sometimes their machine) to get it to work.

---

### Post by bahdom on 2007-07-25
> **mohnkern said:**
> If you're using Alsa (which unless you changed it, and  you're using Feisty is likely) start by trying the following:

im not, when i plugged in the headphones the option "USB Headphones" appeared, since that one allowed me to listen to music n stuff i've been using that one. Games still wont play any music though

---

### Post by TorchlightJay on 2007-07-25
Install the new ALSA. My stuff didn't work but I was using 1.0.13 but when I installed 1.0.14 (like everything that they list on the site, plugins, libs, firmware, drivers, and utils) and did an alsaconf, everything worked fine.

---

### Post by bahdom on 2007-07-25
how do i update alsa? synaptic reports it as up to date though

anyway, tried selecting it in the sound control panel and got this error:

[img]http://img527.imageshack.us/img527/7950/screenshotxe3.jpg[/img]

edit: alsa is in fact in version 1.0.13

---

### Post by bahdom on 2007-07-26
anyone? :D

---

### Post by TorchlightJay on 2007-07-31
google alsa and download from the website. Then untar all the packages into a directory. In Konsole or Terminal or whatever you are using, navigate to the directory that you untared the tarballs into. in each one, you will do a ./configure then a make then a SUDO MAKE INSTALL. That will isntall them. Once you install all packages, do sudo alsaconf and go through the motions. You should then be fine.

---

### Post by bahdom on 2007-07-31
it worked :D thanks

---

