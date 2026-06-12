---
title: "Changing port that GPG uses to import keys?"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by GuinessDraft on 2009-02-25
Hi All!

I am trying to get KDE 4.2 installed on Intrepid using instructions located at:

[http://www.ubuntugeek.com/how-to-install-kde-42-stable-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-install-kde-42-stable-in-ubuntu-810-intrepid-ibex.html)

I have gotten to the step where I am supposed to import the keys from the keyserver, but the process times out.  After much experimentation, I believe I've found the culprit:  my company with its draconian IT department have closed the port that GPG is using.

Does anyone know a way I can make GPG work over port 80 or another accepted port?  Thanks for any ideas.

-Bill

---

### Post by GuinessDraft on 2009-02-26
I found an answer to my own question.

Instead of trying to import the keys, it's easier just to use this instead of apt-get:

```
aptitude update -o Acquire::http::No-Cache=True
```This will allow the use of third party repositories behind a locked-up firewall.

-Bill

---

