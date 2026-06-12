---
title: "Sound problem with XFCE4"
date: 2005-04-20
forum: Hardware &amp; Laptops
---

### Post by siebzehn on 2005-04-20
I'm checking out XFCE4.  When I was using gnome, sound worked just fine, but I'm having some problems under xfce.  Sound works when I use a media program (xmms, rythmbox, etc) but I have no sound with Gaim for example.

Any ideas?

Thanx

---

### Post by bored2k on 2005-04-20
[QUOTE=siebzehn]I'm checking out XFCE4.  When I was using gnome, sound worked just fine, but I'm having some problems under xfce.  Sound works when I use a media program (xmms, rythmbox, etc) but I have no sound with Gaim for example.

Any ideas?

Thanx[/QUOTE]
 Go to gaim preferences and make sure its using ESD sound, then from a terminal type
esd &

And retry.

---

### Post by siebzehn on 2005-04-20
[QUOTE=bored2k]Go to gaim preferences and make sure its using ESD sound, then from a terminal type
esd &

And retry.[/QUOTE]
 It worked!  Thank you

---

### Post by Xanf on 2005-05-21
[QUOTE=siebzehn]It worked!  Thank you[/QUOTE]
 Maybe it's better to put the command esd& into autostart.sh ?
:-)

---

### Post by bw32 on 2005-05-26
if you do that. i found that Opera does not sound anymore with esd runing at the back.

---

