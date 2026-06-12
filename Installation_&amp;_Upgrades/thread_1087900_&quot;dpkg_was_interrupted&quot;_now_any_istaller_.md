---
title: "&quot;dpkg was interrupted&quot; now any istaller won't open"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by I.know.nothing on 2009-03-05
I had a blackout in my area while I was using synaptic package manager to install vlc. I believe that at least the download had already finished when I lost power (during installation). When I turned on the computer (xubuntu desktop) I notice that vlc wasn't installed (because installation was interrupted) so I tried to open synaptic, an error appears.(and the other 'add/remove' package manager opened but when I click "apply", the same error appears)the error says the following:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried to run dpkg --configure -a But I have no idea what to do afterwars; please help.

---

### Post by howefield on 2009-03-05
Did you have to preface the command with sudo

```
sudo dpkg --configure -a
```

It will then ask for your password, type it in (you won't see it being typed)

---

