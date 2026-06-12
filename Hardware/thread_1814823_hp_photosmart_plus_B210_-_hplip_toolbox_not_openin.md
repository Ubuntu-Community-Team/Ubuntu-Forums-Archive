---
title: "hp photosmart plus B210 - hplip toolbox not opening"
date: 2011-07-30
forum: Hardware
---

### Post by Tootler on 2011-07-30
I recently bought this printer as my old one had died on me.

As this is a relatively new model, I had to download and install an up to date version of hplip from the hplip opensource website which I did and the installation went successfully and the printer is working fine.

However, recently I have found that the toolbox no longer opens when you click on the gui, so I tried opening from the terminal and got the following error message:
```
error: Unable to load DBus libraries. Please check your installation and try again.
```

I have checked on synaptic and as far as I can tell the dbus libraries are installed. Obviously something has changed, but what?

TIA 

Geoff

---

### Post by steveMyatt on 2011-08-20
I made it work by installing python-qt4-dbus

---

