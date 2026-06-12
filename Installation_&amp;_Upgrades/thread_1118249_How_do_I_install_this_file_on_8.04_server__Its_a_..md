---
title: "How do I install this file on 8.04 server?  Its a .franklin?"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by Linuxwho? on 2009-04-06
"root@ubuntu:/tmp# install zcs-5.0.6_GA_2314.UBUNTU8.FRANKLIN -t /tmp /etc
install: omitting directory `zcs-5.0.6_GA_2314.UBUNTU8.FRANKLIN'
install: omitting directory `/etc'
root@ubuntu:/tmp#"

[COLOR="DarkSlateBlue"]What does all that mean?[/COLOR]
---------
[COLOR="DarkSlateBlue"]The directions for my install say:[/COLOR]

" Download the appropriate package for your Ubuntu installation (32 or 64 bit Ubuntu 8.04 LTS), copy it into your choice directory (I prefer /temp because /tmp is volatile and clears out every reboot), change to that directory, and type

tar -xzf zc*

and it'll create a whole directory /temp/zcs with lots of files inside it. Then:

cd /temp/zcs
./install.sh"

[COLOR="DarkSlateBlue"]This is WRONG as far as I can tell.[/COLOR]

[COLOR="DarkSlateBlue"]#1 It does not create any such directory named "zcs."
#2 ./install.sh does nothing.

Any ideas? Thanks.[/COLOR]

---

### Post by Linuxwho? on 2009-04-06
Anyone?

---

### Post by linuxuser21 on 2009-04-06
Where did you get it from?

---

### Post by Linuxwho? on 2009-04-06
Thanks.  I got it from zimbra for email.  The instructions on their site are not clear so I fought with it for 4 hours.  Prolly cuz I am such a newb as well.  It created a directory with the same exact name of the tar file which threw me way off.

---

### Post by linuxuser21 on 2009-04-06
So, is the file the actual application?  Or is that an add-on or something like that?

---

### Post by Linuxwho? on 2009-04-07
> **linuxuser21 said:**
> So, is the file the actual application?  Or is that an add-on or something like that?

The file is the actual application and when you run that command it makes a directory with the same exact name as the file...it confused the $%^& out of me at first.

---

