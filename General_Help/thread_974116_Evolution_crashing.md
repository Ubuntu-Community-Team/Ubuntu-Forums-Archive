---
title: "Evolution crashing"
date: 2008-11-07
forum: General Help
---

### Post by rdn2fst on 2008-11-07
I recently reinstalled my Dell D630 with Ubuntu going from 8.04 to 8.10.  Sadly my Evolution client has been problematic.  Has anyone experienced the scenario of Evolution starting, updating folders/email from OWA then crashing and dissapear with no output to the window manager?

If I start Evolution from a terminal window i get the following:
```
ahachenberg@9KM6SD1:~$ evolution --disable-preview
  
** (evolution:27264): DEBUG: mailto URL command: evolution %s
** (evolution:27264): DEBUG: mailto URL program: evolution

(evolution:27264): camel-exchange-provider-WARNING **: Unable to load Exchage summary for folder personal: no such table: personal

(evolution:27264): camel-exchange-provider-WARNING **: Unable to load Exchage summary for folder personal/Deleted Items: no such table: personal/Deleted Items

(evolution:27264): GLib-CRITICAL **: g_base64_encode: assertion `len > 0' failed
Segmentation fault
ahachenberg@9KM6SD1:~$
```

The same thing happened right off the bat when I installed Ubuntu 8.10 and restored Evo from backup files.  I was able to get in by removing that restoration and starting from scratch.  This time i'm having no luck starting from scratch.  I've verified that I can successfully log into to OWA from firefox.:confused:

---

