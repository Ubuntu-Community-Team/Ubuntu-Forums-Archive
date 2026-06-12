---
title: "Minefield 3.5 Web Browser?"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by TSWMIN85 on 2009-07-01
Running Juanty Jackalope.

I was looking for a .deb file for the Firefox 3.5 release.

I went to this site: [http://www.blogsdna.com/3824/how-to-download-install-firefox-35-on-ubuntu-904-linux.htm](http://www.blogsdna.com/3824/how-to-download-install-firefox-35-on-ubuntu-904-linux.htm)

I followed the instructions and it installed an unbranded Firefox 3.5 beta called MINEFIELD 3.5 WEB BROWSER. When I run this sketchy seeming program the window bar says SHIRETOKO.

My question is how do I uninstall MINEFIELD 3.5 WEB BROWSER and if recommended SHIRETOKO as well. I seen shiretoko in the ADD/REMOVE app when I was looking for MINEFIELD 3.5 WEB BROWSER which doesn't seem to appear under ADD/REMOVE or SYNAPTIC PACKAGE MANAGER.

Thanks in advance.

---

### Post by TSWMIN85 on 2009-07-01
I found the solution. I ran as root:

```
apt-get remove --purge firefox-3.5
```

---

### Post by jimv on 2009-07-01
EDIT

Nevermind

---

### Post by TSWMIN85 on 2009-07-01
If I wait will it come up in system update tool?

Also if I downloaded the file from mozilla.com for Firefox 3.5 how could I install it from that?

---

### Post by jimv on 2009-07-01
Yes, you can download it from the Mozilla site.

---

### Post by TSWMIN85 on 2009-07-01
How would I iinstall iit once downloaded from the Mozilla site?

---

### Post by vivatsemiramis on 2009-07-02
i also had the same issue then i found this one:

[http://gaarai.com/2009/07/01/upgrade-to-firefox-3-5-on-ubuntu-9-04-jaunty-jackalope/](http://gaarai.com/2009/07/01/upgrade-to-firefox-3-5-on-ubuntu-9-04-jaunty-jackalope/)

you may consider looking at his instructions, they worked perfectly for me. :)

hope that helps

---

### Post by TSWMIN85 on 2009-07-07
> **vivatsemiramis said:**
> i also had the same issue then i found this one:

[http://gaarai.com/2009/07/01/upgrade-to-firefox-3-5-on-ubuntu-9-04-jaunty-jackalope/](http://gaarai.com/2009/07/01/upgrade-to-firefox-3-5-on-ubuntu-9-04-jaunty-jackalope/)

you may consider looking at his instructions, they worked perfectly for me. :)

hope that helps

Perfect! Thank you!

---

