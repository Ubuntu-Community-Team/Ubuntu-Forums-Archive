---
title: "How the heck do I install flash?"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by sambrucealmighty on 2009-06-30
I've tried just about every forum, every distro, every way... why can't flash install?

GRRRR!

Absolute newbie to ubuntu... it seems pretty cool but browsing nowadays is pretty useless without flash in firefox!!!

:-)

Someone help please! 

Thanks!

---

### Post by Revolutionary101 on 2009-06-30
Go to this website [http://get.adobe.com/flashplayer/?promoid=BUIGP](http://get.adobe.com/flashplayer/?promoid=BUIGP)

Then download it as a .deb file.

When it downloads all you have to do is double click the .deb file and it will install it for you.

---

### Post by coffeecat on 2009-06-30
Even better - go to System > Administration > Synaptic and install the package ubuntu-restricted-extras. This will do for you automatically what the previous poster suggests, and will also install a number of useful multimedia codecs, Java runtime, **and** the Microsoft core fonts for good measure.

---

### Post by lovinglinux on 2009-07-01
Even better :)

Run the following command in the terminal [see footnote] 

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree 
```

This will install flash and also remove the default plugin, which might conflict with the one from Adobe.

> [color=#CC0000]**How to run commands in a Terminal: **[/color]Open "Applications >> Accessories >> Terminal", then type or paste the code (CTRL+SHIFT+V) and hit *Enter*. You might be prompted to enter your password. You cannot see it while you type, but it is there. Then just hit *Enter* again to run the command. Please do not run commands without knowing what they do. If you do not understand what a command does, ask for explanations.

---

