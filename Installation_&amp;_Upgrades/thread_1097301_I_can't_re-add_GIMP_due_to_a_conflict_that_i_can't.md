---
title: "I can't re-add GIMP due to a conflict that i can't resolve :("
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by vaserlan on 2009-03-15
An error message stated that i need to go to the synaptic package manager to remove the conflicting software.

In synaptic, it stated

'Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies.
Make sure that all the required repositories are added and enabled in the preferences. 

gimp:
  Depends: libgimp2.0 (<=2.6.1-z) but 2.6.3-1ubuntu1~intrepid1 is to be installed
  Depends: gimp-data (<=2.6.1-z) but 2.6.3-1ubuntu1~intrepid1 is to be installed



[COLOR="RoyalBlue"]Please help. :)[/COLOR]

---

### Post by mc4man on 2009-03-15
Your libgimp2.0 and gimp-data are intrepid backports versions, but synaptic is showing only the intrepid version of gimp.

Two solutions

Open up System -> admin. -> software sources and enable the backports source under the 'updates' tab. Then click 'close' and 'reload'
Then go back into synaptic and search gimp and install (or use sudo apt-get install gimp in a terminal.

Or leave backports disabled and in synaptic remove libgimp2.0 and gimp-data, then when done install gimp.

The first way gives you the backports version, the 2nd way the intrepid version, your choice

---

### Post by vaserlan on 2009-03-15
Thanks. It worked. :)

I used the first option. :)

---

