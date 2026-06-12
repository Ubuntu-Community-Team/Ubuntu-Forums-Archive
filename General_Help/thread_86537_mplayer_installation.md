---
title: "mplayer installation"
date: 2005-11-05
forum: General Help
---

### Post by nelak on 2005-11-05
hi,
i am new on ubuntu. i tried to install mplayer using synaptic pakage manager but the installed software wasnt working properly. There wasnt any sound, no fullscreen mode and other problems. Any ideas on how to get it right??
bye

---

### Post by syphix on 2005-11-05
I can't even FIND mplayer in Synaptic.  I've tried compiling it myself, but it doesn't like the gcc that came with Breezy...

---

### Post by kzutter on 2005-11-05
Are you on Breezy? - I tried mplayer on Hoary, but it was horribly broken - wouldn't even launch. So I removed it. Haven't tried it on Breezy...

-Ken

---

### Post by syphix on 2005-11-05
Well, I got mplayer working thanks to Automatix:
[http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix)

---

### Post by taurus on 2005-11-05
Well, add these lines to your /etc/apt/sources.list and install mplayer away...

deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy multiverse

---

### Post by mustang on 2005-11-05
[QUOTE=nelak]hi,
i am new on ubuntu. i tried to install mplayer using synaptic pakage manager but the installed software wasnt working properly. There wasnt any sound, no fullscreen mode and other problems. Any ideas on how to get it right??
bye[/QUOTE]

To (partially) answer the question of the original poster, try

```
gmplayer -zoom <videofile>
```

That will take care of the zoom issue. I'm not sure how to make that permanent though so that you don't have to always type that in. Perhaps someone else will chime in?

Regarding the sound problems---is it specific to mplayer or a universal problem? What kind of sound card do you have?

---

### Post by bejinxed on 2005-11-06
[QUOTE=taurus]Well, add these lines to your /etc/apt/sources.list and install mplayer away...

deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy multiverse[/QUOTE]

This worked great, thank you.

-bej

---

### Post by nelak on 2005-11-06
yes i am on breezy and the sound card is intel's.
-nel

---

