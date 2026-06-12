---
title: "Firefox works, but updates don't"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by hairyhippy on 2009-05-11
Hi, I'm new here and a beginner with Ubuntu so please be gentle. I'm setting up Ubuntu studio to run through my university network on an old ish pc. I have set the network proxy cofiguration for firefox and it works fine, but I can't get the update manager or the synaptic package manager to  work. Could anyone help me please? 

Pete

---

### Post by emacbri on 2009-05-11
I don't understand, are you talking about the Firefox update manager or Ubuntu's???

---

### Post by drs305 on 2009-05-11
If you are talking about update-manager, run this in a terminal (ALT-F2) and tell us what error messages you get:
```

sudo apt-get update && sudo apt-get upgrade

```

Of course, with Jaunty automatic updates aren't made on a daily basis except for security ones.

---

### Post by hairyhippy on 2009-05-11
Sorry, I wasn't clear. Firefox can connect to the internet (ie the internet connection is working) but Ubuntu's update manager (or synaptic package manger for that matter) will not connect to check for updates.

---

### Post by hairyhippy on 2009-05-11
> **drs305 said:**
> If you are talking about update-manager, run this in a terminal (ALT-F2) and tell us what error messages you get:
```

sudo apt-get update && sudo apt-get upgrade

```Of course, with Jaunty automatic updates aren't made on a daily basis except for security ones.

I get this lot.

---

### Post by drs305 on 2009-05-11
In either Software Sources or Synaptic: Settings, Preferences, Network tab. Is it set to connect directly to the internet?
Have you tried another repository (Settings, Repositories, Other)?
You are using Hardy, correct?

---

### Post by hairyhippy on 2009-05-11
> **drs305 said:**
> In either Software Sources or Synaptic: Settings, Preferences, Network tab. Is it set to connect directly to the internet?
Have you tried another repository (Settings, Repositories, Other)?
You are using Hardy, correct?

I have tried setting the synaptic package manager to connect directly to the internet and tried to manually configure the proxy with the proxy set the same as the setting I used for the proxy in firefox.

I'm using Ubuntu studio and I don't seem to have a Settings, repositories, other.

---

### Post by gjoellee on 2009-05-11
404 means that the "URL" (website address) does not exist. Try changing repositories. That can be done in "Software Sources" which you can find in the System menu.

---

### Post by emacbri on 2009-05-12
I don't know much about Ubuntu Studio but i'll take a whack at it any way. Try opening the "Software Sources" Control Panel (assuming that Ubuntu Studio uses Gnome). Under the Updates tag make sure that the at least "Important Security Updates" and "Reccomended Updates" are both checked. Oh, and try disableing the proxy, that may do the trick (Unless the proxy is required by your school). Good Luck!!!:)

---

### Post by lisati on 2009-05-12
> **emacbri said:**
> I don't know much about Ubuntu Studio but i'll take a whack at it any way. Try opening the "Software Sources" Control Panel (assuming that Ubuntu Studio uses Gnome). Under the Updates tag make sure that the at least "Important Security Updates" and "Reccomended Updates" are both checked. Oh, and try disableing the proxy, that may do the trick (Unless the proxy is required by your school). Good Luck!!!:)

I can confirm that on Ubuntu Studio the relevant option to select software sources is on the System->Administration->Software Sources menu item.

BTW I was getting error messages from Update Manager on U.S. 9.04 & "regular" ubuntu 64-bit earlier today, maybe there's a server or two down at the moment.

---

### Post by hairyhippy on 2009-05-12
-> **emacbri said:**
> I don't know much about Ubuntu Studio but i'll take a whack at it any way. Try opening the "Software Sources" Control Panel (assuming that Ubuntu Studio uses Gnome). Under the Updates tag make sure that the at least "Important Security Updates" and "Reccomended Updates" are both checked. Oh, and try disableing the proxy, that may do the trick (Unless the proxy is required by your school). Good Luck!!!:)

I've tried that with no joy :( Should the proxy in Settings / network proxy be set the same as the proxy is set in firefox?

---

### Post by emacbri on 2009-05-12
Yes, try that if you haven't allready. And thank you for putting up with me, I have a hard time following these threads

---

### Post by hairyhippy on 2009-05-12
:( I can't think what to try next.

---

