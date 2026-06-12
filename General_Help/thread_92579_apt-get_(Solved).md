---
title: "apt-get (Solved)"
date: 2005-11-19
forum: General Help
---

### Post by dev3n on 2005-11-19
Hello, I just tested Linux (Ubuntu) for the first time ever today, and it works pretty nice, except "apt-get" does not work properly, when I try for example apt-get install gftp i get this:

Läser paketlistor... Färdig 
Bygger beroendeträd... Färdig
E: Kunde inte hitta paketet gftp 

I know, its on swedish, but I'll translate the error message:
E: Could not find package gftp


I've tried apt-get update and it worked well, but i have no idea why it does not work..

Thanks, Christopher.

---

### Post by JimmyBEng on 2005-11-19
what your sources.list look like?

I believe gftp is in universe so do you have that enabled?

---

### Post by aysiu on 2005-11-19
Yes, [gFTP is in the Universe repositories](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=breezy&release=all&keywords=gftp&sourceid=mozilla-search).

If you want those repositories, see the first link in my sig.

---

### Post by dev3n on 2005-11-19
```
deb http://se.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://se.archive.ubuntu.com/ubuntu breezy main restricted

# deb http://se.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://se.archive.ubuntu.com/ubuntu breezy universe

```

i belive i should remove the # ?

---

### Post by aysiu on 2005-11-19
[QUOTE=dev3n]```
deb http://se.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://se.archive.ubuntu.com/ubuntu breezy main restricted

# deb http://se.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://se.archive.ubuntu.com/ubuntu breezy universe

```

i belive i should remove the # ?[/QUOTE] Yes, but I count vouch for the se.archive.ubuntu.com, as I've seen people with other country-specific sources have problems (us.archive.ubuntu.com, for example). If it doesn't work, check the first link in my sig.

---

### Post by adwait on 2005-11-19
Check the page in ayisus signature......cut paste that to your a new file. Back up the old /etc/apt/sources.list and replace it with this one.

---

### Post by dev3n on 2005-11-20
Thanks a ton guys, I don't know how to thank you :) Linux was easier then i first thought.

---

### Post by heimo on 2005-11-20
[quote=dev3n]```
deb http://se.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://se.archive.ubuntu.com/ubuntu breezy main restricted

# deb http://se.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://se.archive.ubuntu.com/ubuntu breezy universe

``` 
i belive i should remove the # ?[/quote] 
Det st&#228;mmer. ;) (Yes.)

EDIT: I'm late as usual. :) Hopefully you got it fixed. Debian package management rocks.

---

