---
title: "No ALSAMIXER?!"
date: 2005-11-30
forum: General Help
---

### Post by Mosey on 2005-11-30
When I go into terminal and type "alsamixer" I recieve this error:

"alsamixer: function snd_ctl_open failed for default: No such file or directory"

Why wouldn't I have this? I tried sudo apt-get install snd_ctl_open but it told me that that package didn't exist in my repositories....

I've been trying to get my damn soundblaster LIVE 24bit card to work all freaking night.

And now this?

What do I do?

---

### Post by Kapre on 2005-11-30
[QUOTE=Mosey]When I go into terminal and type "alsamixer" I recieve this error:

"alsamixer: function snd_ctl_open failed for default: No such file or directory"

Why wouldn't I have this? I tried sudo apt-get install snd_ctl_open but it told me that that package didn't exist in my repositories....

I've been trying to get my damn soundblaster LIVE 24bit card to work all freaking night.

And now this?

What do I do?[/QUOTE]

Mosey - Maybe this [thread]("http://www.ubuntuforums.org/showthread.php?t=27186&highlight=soundblaster+live") will be of interest to you.

K

---

### Post by Mosey on 2005-11-30
I followed all the steps...but when I finaly get to the end where you must restart ALSA I get this error in terminal:

sudo /etc/init.d/alsa restart
/etc/init.d/alsa: Warning: The 'restart' method is deprecated and will be removed.
/etc/init.d/alsa: Warning: Use the alsa-utils initscript instead.

Huh?!

GRRRRRRR!:mad:

---

### Post by Kapre on 2005-11-30
[QUOTE=Mosey]I followed all the steps...but when I finaly get to the end where you must restart ALSA I get this error in terminal:

sudo /etc/init.d/alsa restart
/etc/init.d/alsa: Warning: The 'restart' method is deprecated and will be removed.
/etc/init.d/alsa: Warning: Use the alsa-utils initscript instead.

Huh?!

GRRRRRRR!:mad:[/QUOTE]

Mosey - I know this maybe a dumb idea...but can you restart your pc and try it again.

K

---

### Post by Mosey on 2005-11-30
Hey! Minor sucesses! I can now view ALSAmixer (still can't hear a damn thing)...

But when I attempt to restart ALSA, per the instructions I still get the same warning.

Any Ideas K?

---

### Post by Mosey on 2005-11-30
When I go to Multimedia System Selector and test ALSA I get this error:

Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'

I don't know what to do....

---

### Post by Mosey on 2005-12-01
bump

---

### Post by ryan76 on 2006-01-07
Is there a fix for this? I'm having identical problems.

---

