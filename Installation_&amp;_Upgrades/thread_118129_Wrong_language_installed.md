---
title: "Wrong language installed"
date: 2006-01-16
forum: Installation &amp; Upgrades
---

### Post by Garyu on 2006-01-16
When I installed Breezy I tried to select swedish, but got an error message saying there was no kernel installed. Tried again with the same result. Checked the CD for errors but no errors was found. So I tried installing in english, and it worked great... only one problem now...

How do I switch default language for EVERYTHING to swedish???

The most annoying thing right now is that in GAIM everything I type is marked as "underline red"-spelling error... and I really can't find a setting for language in GAIM... I can live with english menus, but hey, I'm not that bad at spelling. :P

I have installed everything swedish from Synaptic. I tried changing to swedish in the System|Administration|Language selector, but that doesn't seem to change anything... Some tips, anyone?

---

### Post by kaamos on 2006-01-16
try
```
sudo dpkg-reconfigure locales
```
Choose a swedish setting, log out and back in.

---

