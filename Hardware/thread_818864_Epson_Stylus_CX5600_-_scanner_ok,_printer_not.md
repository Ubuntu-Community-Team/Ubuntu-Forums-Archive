---
title: "Epson Stylus CX5600 - scanner ok, printer not"
date: 2008-06-04
forum: Hardware
---

### Post by owbizi on 2008-06-04
Hi all.

When Ubuntu Hardy was released, as soon as I got the notice I downloaded it and made a fresh install of it. And... yay! My printer is automatically detected and, alike Gutsy, it **works**!

After, installed the scanner following [this tutorial](http://ubuntuforums.org/showthread.php?t=627471), and... double yay! **Working too**!

By the way, after few days (hmm, it sounded good) Ubuntu went heavy - and I was looking for somewhat lightier to use. So... Ubuntu was good... triple yay! Let's *fresh reinstall* (new vocabulary?) it!

...and the printer decided not to work anymore. Negative yay...

When connected, Ubuntu identifies **and** installs it automatically, just like before, but, when I try to print something, a page, a photo, whatever, it's like the printer has just... gotten mad and started complaining about its life and if it has or hasn't to print this same something (in other words, it just stops)!

Right now, CX5600's scanner is working. Looking at it (not the scanner, the CX5600 itself), two lights are... lighting, constantly: the **green** one (because, ohh, it's turned on) and the waterdrop **red** one (now, more to a tear drop...).

Anybody got something similar or has any tip for solving it?

---

### Post by teaker1s on 2008-10-26
avasys epson 
[http://avasys.jp/hp/menu000000500/hpg000000442.htm]("http://avasys.jp/hp/menu000000500/hpg000000442.htm")


download alien
```
sudo apt-get install alien
```
download rpm file from avasys site
```
sudo alien di nameofpackage.rpm
```
converts and installs from rpm to deb

---

