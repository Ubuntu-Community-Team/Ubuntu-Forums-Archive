---
title: "More problems with Wubi."
date: 2008-07-29
forum: General Help
---

### Post by Conger on 2008-07-29
Well, since my initial problem (ubuntu won't boot) doesn't seem to be of interest to anyone anymore, I've uninstalled Ubuntu.

Sadly, the option to boot into ubuntu is still there when I turn my computer on. I know it's a minor inconvenience, but it's an inconvenience nonetheless.

I've searched the forum, and have even tried a link to an uninstall.exe that Ago posted... no luck.

I deleted the folder, as well... that's probably a bad idea... but when I uninstalled, everything was still sitting there. 

Any ideas? anyone? 

Or, is there something in BIOS or somethin' that will let me change the duration of time that that screen is available, so it picks Vista quickly?

thanks for your time.

---

### Post by beerslayer on 2008-07-29
> **Conger said:**
> Or, is there something in BIOS or somethin' that will let me change the duration of time that that screen is available, so it picks Vista quickly?

Hopefully I'm not completely out in left field with this response...

Try this:
In Vista, hopefully you have Administrative Tools enabled in your Control Panel, because I don't remember off the top of my head how to enable them if you don't.  Assuming you do, select Administrative Tools --> System Configuration, then click the Boot tab.  You will probably have at least two entries there - one for Vista and one for Ubuntu.

You can probably remove the Ubuntu entry here, or, if you prefer, select the Vista entry, make sure it's the default, and set whatever timeout value you like in the box on the right labeled "Timeout:"  The box labeled "Make all boot settings permanent" is pretty self-explanatory.  I don't recommend you tinker with anything else here unless you know what you're doing.

---

### Post by ago on 2008-07-29
[https://wiki.ubuntu.com/WubiGuide#head-61fe7beb6f9507b384ce19642d3dcb697b19aeb1](https://wiki.ubuntu.com/WubiGuide#head-61fe7beb6f9507b384ce19642d3dcb697b19aeb1)

---

### Post by Conger on 2008-07-29
Well, there was only the vista option, but I set the timeout to the minimum, so I guess I can live with that. 

Ago, I've tried that with no luck. =-(

Thanks for your help!

---

### Post by ago on 2008-07-30
You can either edit boot.ini (XP) or use EasyBCD (Vista) and remove manually the boot option

---

### Post by Conger on 2008-07-30
Fantastic! Thanks, Ago.

---

