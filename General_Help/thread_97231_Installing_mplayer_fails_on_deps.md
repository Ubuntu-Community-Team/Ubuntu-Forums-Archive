---
title: "Installing mplayer fails on deps"
date: 2005-11-30
forum: General Help
---

### Post by kamagurka on 2005-11-30
Now I went to all this trouble of adding extra repositories, yadda yadda yadda so I could install mplayer (seriously, totem? What were you thinking?), and now apt-get is giving me lip about libdirectfb-0.9-20 not  being "installable". Huh?

And while we're at it, is there some secret codec I have to install to get totem to play divx files so that the video and the sound doesn't drift apart? Mplayer on my other box plays that file flawlessly, by the way.

---

### Post by Xian on 2005-11-30
Did you follow the wiki: [How-To Install Mplayer](https://wiki.ubuntu.com/MplayerInstallHowto)?

---

### Post by kamagurka on 2005-11-30
Gah. Sorry. I just realized the place where I pasted my additional repositories from still had references to Hoary in them; Changed them to Breezy, now everything works fine (and mplayer indeed plays the files like it should. What's wrong with totem?)

---

### Post by Bachstelze on 2005-11-30
Dunno... Totem works fine here. Try downloading the codecs with [Automatix](http://ubuntuforums.org/showthread.php?t=66563).

---

### Post by bored2k on 2005-11-30
By default, totem is based on gstreamer, which is hardly plays anything out there. If you want a functional totem, install totem-xine.

---

### Post by kamagurka on 2005-12-01
[QUOTE=bored2k]By default, totem is based on gstreamer, which is hardly plays anything out there. If you want a functional totem, install totem-xine.[/QUOTE]
And this doesn't strike you as needlessly complicated?
Nice FLCL reference, btw.

---

### Post by bored2k on 2005-12-01
[QUOTE=kamagurka]And this doesn't strike you as needlessly complicated?
Nice FLCL reference, btw.[/QUOTE]
I don't make the rules in Gnome..

---

