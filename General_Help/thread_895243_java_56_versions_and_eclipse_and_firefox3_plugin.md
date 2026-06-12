---
title: "java 5/6 versions and eclipse and firefox3 plugin"
date: 2008-08-20
forum: General Help
---

### Post by tbunix on 2008-08-20
Ubuntu 8.0.4.1
firefox 3.0.1

While trying to fix an eclipse problem - can't get the lisp plugin to work - I found this page
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

which explained why even though I had sun java 6 from the repositries installed $java -version still returned 1.5.0

so I followed the how-to with this result

:~$ sudo update-java-alternatives -s java-6-sun
No alternatives for firefox-3.0-javaplugin.so.
No alternatives for firefox-javaplugin.so.
No alternatives for iceape-javaplugin.so.
No alternatives for iceweasel-javaplugin.so.
No alternatives for midbrowser-javaplugin.so.
No alternatives for mozilla-javaplugin.so.
No alternatives for xulrunner-addons-javaplugin.so.
No alternatives for xulrunner-javaplugin.so.

plus a whole lot more showing where substitutions were found from java 1.5.0 to 1.6.0_06

question- did I just break firefox? in some way I've yet to discover?

no idea what iceape and iceweasel are/were

---

