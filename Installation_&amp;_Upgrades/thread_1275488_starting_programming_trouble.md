---
title: "starting programming trouble"
date: 2009-09-25
forum: Installation &amp; Upgrades
---

### Post by hellert88 on 2009-09-25
I am new to ubuntu and very new to Perl.  I was just starting to code this:

[I]#!/usr/bin/perl
@lines = `perldoc -u -f atan2`;[/I]

I then tried running it and it said "You need to install the perl -doc package to use this program."
I tried searching the net for it and the only things that came up were modules.  Do I need to download one of those for this to work?? Also do I need to download anything else??  I tried simpler ones like just printing a line to the screen and that worked.

---

### Post by Partyboi2 on 2009-09-25
I don't know much about perl, but you can install the perl doc package by opening a terminal and installing with
```
sudo apt-get install perl-doc 
```

---

### Post by hellert88 on 2009-09-26
Hey you know enough to help me with that problem!! It worked, thanks a ton!

---

