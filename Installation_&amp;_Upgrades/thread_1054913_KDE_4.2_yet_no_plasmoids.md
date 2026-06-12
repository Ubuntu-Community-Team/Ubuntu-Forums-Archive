---
title: "KDE 4.2 yet no plasmoids"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by Oceanic on 2009-01-30
I upgraded to KDE 4.2 on Intrepid 
(with instructions from kubuntu.org)

Yet I cannot use ANY plasmoid. When I pick one for the desktop or the panel, plasma hangs and then screen goes black (reboot necessary)

Install gave some errors and told me to apt-get -f install
Only issue with kdepimlibs5-dev...

For the rest KDE 4.2 looks very crisp and colourful and lighter than KDE 4.1 fortunately which was a bit too black.

Particular plasmoids that I tried in vain were Luna, Show desktop, Clock...


Where can I find what is wrong (logfiles?) 

Cheers !

---

### Post by abn91c on 2009-01-30
the website tells you to uninstall the plasmoids when upgrading. My self I just removed them from the desktop before upgrading and now the ones I use- LDC weather, clock and desktop folder view work.
try running the install again? may help

---

### Post by Oceanic on 2009-01-30
Yes, I uninstalled all plasmoid...:KS

---

### Post by Oceanic on 2009-01-30
In fact, I did the whole installation precedure three times...
No differences.
Looks great, however no plasmoids possible in the panel, and when I try to place a pasmoid on the desktop... black screen

Cheers!

---

### Post by MistralWind on 2009-02-02
> **Oceanic said:**
> In fact, I did the whole installation precedure three times...
No differences.
Looks great, however no plasmoids possible in the panel, and when I try to place a pasmoid on the desktop... black screen

Cheers!
I don't know if this will help you or not, but I had a problem with my screen freezing whenever I tried to add a plasmoid. I fixed it by going into: 

> home > [your directory] > .kde > share > config

and deleting **plasma-appletsrc**. It reset the configuration somehow so that I could add plasmoids again.

---

