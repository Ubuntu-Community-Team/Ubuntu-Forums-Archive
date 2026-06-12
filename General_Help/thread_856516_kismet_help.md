---
title: "kismet help"
date: 2008-07-11
forum: General Help
---

### Post by jkid on 2008-07-11
did something playing around and now kismet doesnt want to start this is what appearsfile:///home/jkid/Desktop/Screenshot.png

---

### Post by openflame06 on 2008-07-19
I think the error is because your kismet.conf file has no source listed.

Have a look at /etc/kismet.conf (if you installed via apt) or /usr/local/etc/kismet.conf if compiled from source.

There is a line that says:
source=addme

You need to change it to reflect your card.

---

