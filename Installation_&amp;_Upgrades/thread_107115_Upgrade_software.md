---
title: "Upgrade software"
date: 2005-12-22
forum: Installation &amp; Upgrades
---

### Post by nami on 2005-12-22
Is there any easy/standardised method of upgrading all the programs in your box?  For example, I currently have firefox 1.0.7 and some old version of OpenOffice.  Is there any way I can quickly and find any newer versions of all the software I have and then update/upgrade to the newer versions easily?

So in this case firefox 1.0.7 would become firefox 1.5 replacing the old version and same with OpenOffice and anything else installed.

Is this possible?

---

### Post by Lofticus on 2005-12-22
apt-get dselect-upgrade <package> should do the trick.

But, for firefox there is no ubuntu version atm. There is however an wikientry for firefox. (Be careful though to save your bookmarks and so on)

Lofticus

---

### Post by az on 2005-12-22
Wait until dapper comes out and uprade to dapper.

Wait until firefox 1.5 gets into the backports and use that.

But basically, use synaptic and add whatever ubuntu repositories you want.

---

### Post by aaronc222 on 2005-12-22
For Firefox I just downloaded it straight from Mozilla's site and overwrote the /usr/lib/mozilla-firefox directory with the new files and it worked like a charm.

As for regular upgrades:
```
sudo apt-get update
sudo apt-get upgrade
```

That's the way I keep myself 'up-to-date'. If I run something on a regular basis that isn't fully updated in the repositories I figure out where it stores it's main files and go from there.

---

### Post by nami on 2005-12-23
Thanks for the info!

So how would you upgrade breezy to the next version of ubuntu when it comes out?

nami

---

### Post by Lofticus on 2006-01-11
sudo apt-get dist upgrade if i remember correctly

---

### Post by Thirsteh on 2006-01-11
sudo apt-get dist-upgrade  -- missing the "-" ;)

---

