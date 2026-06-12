---
title: "Touchscreen in Ubuntu"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by RelativelyQuantum on 2007-06-06
Ok, I need some serious help.

I recently purchased a Planar PT1510MX touchscreen. After some correspondence with the company, I was told that drivers for it would be available for Linux. This is true; the drivers *are* for Linux - the only problem is that they're for Suse and Redhat. I hope that I'll be able to use the screen with Ubuntu, but have no idea how to go about doing so.

Any advice would be greatly appreciated.

---

### Post by RelativelyQuantum on 2007-06-06
Somebody? Anything would help...

---

### Post by ramjet_1953 on 2007-06-06
I had a quick look on the net and couldn't find a deb package.

However, if you install a package called [COLOR="Blue"]alien[/COLOR], it may do the conversion for you.

Copy and paste this into a terminal:

[COLOR="Red"]sudo apt-get install alien[/COLOR]

Make sure that you read up on its' use before diving in, by typing in a terminal [COLOR="Red"]man alien[/COLOR] .

Regards,
Roger :cool:

---

### Post by RelativelyQuantum on 2007-06-09
Thanks alot; this really helps! I'll install the package...

---

### Post by RelativelyQuantum on 2007-06-09
Two questions:

How do I use it? (The manual file was blank)

Does it require a system restart, or can I just plug my screen in and have a go?

---

### Post by lintoon on 2007-08-08
Man page:

[http://pwet.fr/man/linux/commandes/p/alien](http://pwet.fr/man/linux/commandes/p/alien)

[http://pwet.fr/man/linux/fonctions_bibliotheques/pm/alien_package](http://pwet.fr/man/linux/fonctions_bibliotheques/pm/alien_package)

---

