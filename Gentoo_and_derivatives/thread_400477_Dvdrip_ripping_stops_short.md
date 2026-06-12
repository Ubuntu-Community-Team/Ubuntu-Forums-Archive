---
title: "Dvd::rip ripping stops short"
date: 2007-04-03
forum: Gentoo and derivatives
---

### Post by Iarwain ben-adar on 2007-04-03
Hi there,

When i used Kubuntu, i used dvd::rip to rip my dvd's to ogm (with hardcoded sub's.
Trying to do the same on Sabayon, i always get an error..

[IMG]http://img477.imageshack.us/img477/2178/dvdripnu8.png[/IMG]

Can anyone tell me what could be wrong?


Iarwain

---

### Post by Iarwain ben-adar on 2007-04-06
Bumpie?


Iarwain

---

### Post by takakia on 2007-05-10
I am also having the same problem.  Couldn't rip a DVD :(

---

### Post by zaratustra on 2007-05-10
maybe you could try to rebuild transcode and libdvdread
you can do that like this```

emerge -av --oneshot transcode libdvdread

```

---

